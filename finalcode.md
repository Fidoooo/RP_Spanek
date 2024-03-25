# Finální verze kódu
V tomto kódu shromažďujeme data z MPU6050 a MAX30102 a následně je posíláme na webovou stránku, kde se ukazují každých 5 vteřin nová, aktuální, data.

## Kód
```
import time
import network
import socket
import MPU6050  # Import MPU6050 library
import machine
from machine import SoftI2C, Pin
from max30102 import MAX30102

# Set up the I2C interface
i2c = machine.I2C(0, sda=machine.Pin(20, Pin.OUT, Pin.PULL_UP), scl=machine.Pin(21, Pin.OUT, Pin.PULL_UP))

# Set up the MPU6050 instance
MPU6050 = MPU6050.MPU6050(i2c)

MPU6050.wake()

sensor = MAX30102(i2c=i2c)

# Setup with default values
sensor.setup_sensor()

# Define HTML template
html_template = """<!DOCTYPE html>
<html>
<head>
    <title>Pico W MPU6050 Data</title>
    <meta http-equiv="refresh" content="5">
</head>
<body>
    <h1>MPU6050 Data</h1>
    <p>%s</p>
</body>
</html>
"""

# Initialize network
ssid = 'Vodafone-DB08'  # Your WiFi SSID
password = 'dm2F42hutrRf7tza'  # Your WiFi password
wlan = network.WLAN(network.STA_IF)
wlan.active(True)
wlan.connect(ssid, password)

# Wait for connection
max_wait = 10
while max_wait > 0:
    if wlan.status() < 0 or wlan.status() >= 3:
        break
    max_wait -= 1
    print('Waiting for connection...')
    time.sleep(1)

# Check connection status
if wlan.status() != 3:
    raise RuntimeError('Network connection failed')
else:
    print('Connected')
    status = wlan.ifconfig()
    print('IP:', status[0])

# Set up socket server
addr = socket.getaddrinfo('0.0.0.0', 80)[0][-1]
s = socket.socket()
s.bind(addr)
s.listen(1)
print('Listening on', addr)

# Main server loop
while True:
    try:
        cl, addr = s.accept()
        client_ip = addr[0]
        print('Client connected from', client_ip)
        request = cl.recv(1024)
        
        sensor.check()
    
        red_sample = sensor.pop_red_from_storage()
        ir_sample = sensor.pop_ir_from_storage()
    
        # Read MPU6050 data
        gyro = MPU6050.read_gyro_data()
        accel = MPU6050.read_accel_data()
        mpu6050_data = "Gyro: " + str(gyro) + ", Accel: " + str(accel) + ", RED:" + str(red_sample) + "," + ", IR:" + str(ir_sample)


        # Construct response HTML
        response_html = html_template % (mpu6050_data)

        # Send HTTP response
        cl.send('HTTP/1.0 200 OK\r\nContent-type: text/html\r\n\r\n')
        cl.send(response_html)
        cl.close()

    except OSError as e:
        print('Connection error:', e)
        cl.close()


```
