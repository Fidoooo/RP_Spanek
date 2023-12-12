# Ročníková práce

Naše ročníková práce se zaměřuje na sestavení a využití **zařízení monitorující spánek**. Toto zařízení bude fungovat na základě LED senzoru životních funkcí a teploměru s akcelerometrem přidávající další kontext k hlavním datům. Elektrotechnická část práce zahrnuje návrh a sestavení obvodů zajišťujících správnou funkci senzorů a následné vytvoření rozhraní pro jejich propojení a sběr dat. Cílem bude spolehlivé monitorovací zařízení schopné efektivního sběru dat o spánku, s možností jejich pozdějšího využití.


## Hardware
Naším cílem je, abychom zprovoznili všechny potřebné senzory (akcelerometr[^2], teploměr, fotosenzor) a diody[^1] (červená, zelená a infračervená) a až pak se budeme zabývat velikostí a designem, ale i tak se chceme inspirovat již existujícími zařízeními na monitorování spánku jako například WHOOP 4.0, Oura Ring a Garmin.

<a href="https://www.whoop.com/eu/en/"> 
<img src="https://images.ctfassets.net/rbzqg6pelgqa/C8vHNCpTJcNSQfta0vYlI/3e5cd32ce2242f64b797eaa165f29373/band-renders-sized-2.png?fm=webp&q=75&w=1920" alt="WHOOP 4.0" width="200" height="200">
</a>

## Software
Nejdříve bychom chtěli docílit přenosu dat ze zařízení na jednoduchou webovou stránku nebo aplikaci a až potom (pravděpodobně ve 4. ročníku) bychom řešili vzhled a zpracování získaných dat. Chceme se inspirovat už existujícími aplikacemi jako je například WHOOP, která zobrazuje data číselně i graficky a uživateli nabízí tipy, ale zároveň bychom chtěli zkusit vymyslet nové funkce nebo některé vylepšit.

<a href="https://www.whoop.com/eu/en/"> 
<img src="https://helios-i.mashable.com/imagery/articles/0195WOwkhwtJIlIxzbFi5b7/images-2.fill.size_363x750.v1611706688.png" width="150" height="auto">
</a>

## Součástky
Akcelerometr https://www.aliexpress.com/item/1005004937815379.html?spm=a2g0o.productlist.main.5.34c43733hY5hny&algo_pvid=090c440d-a9c7-4e93-8bfc-e4ada5a3f7ea&algo_exp_id=090c440d-a9c7-4e93-8bfc-e4ada5a3f7ea-2&pdp_npi=4%40dis%21CZK%21112.23%2178.52%21%21%214.86%21%21%40211b80d117018921205148974e82bc%2112000031083429736%21sea%21CZ%210%21AB&curPageLogUid=rjL012Rs8zeD#nav-specification

https://a.aliexpress.com/_mOfIqrm

baterie

port pro baterii https://www.aliexpress.com/item/1005005341202402.html?spm=a2g0o.productlist.main.17.562d64c0U75Vu2&algo_pvid=ad522ff2-121b-47ac-851c-8b327e2f9ad9&algo_exp_id=ad522ff2-121b-47ac-851c-8b327e2f9ad9-8&pdp_npi=4%40dis%21CZK%2142.26%2111.32%21%21%211.83%21%21%40210388c917018913897682310e681b%2112000032671731627%21sea%21CZ%210%21AB&curPageLogUid=z8p4kGSqHpTU

snímač tepu a okysličení https://www.aliexpress.com/item/1005004916269995.html?spm=a2g0o.productlist.main.17.6f1a5cf2hhtC7q&algo_pvid=4f4e1962-3a4f-4291-a474-15d68faea60f&algo_exp_id=4f4e1962-3a4f-4291-a474-15d68faea60f-8&pdp_npi=4%40dis%21CZK%2128.17%2128.17%21%21%211.22%21%21%40211b813b17018916192545075eb99c%2112000031007376104%21sea%21CZ%210%21AB&curPageLogUid=ZKvNZuZgWVL8

<p>https://www.hwkitchen.cz/max30102-snimac-pro-srdecni-tep-a-pulzni-oxymetr/</p>



[^1]: https://youtu.be/BFZxlauizx0?si=Zi1RsaSW9pjEn2BY
[^2]: https://youtu.be/fLlQ2w1gOEM?si=hkw2ZW8PtDQGrrTT
