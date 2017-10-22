Process Modeling Library
========================

Source [Blocks]
---------------
Generuje objekty, ktoré sú použité v systéme.
Ak je potrebné modelovať príchod pomocou exponenciálneho rozdelenia,
treba nastaviť **arrivals defined by** ako **interarrival time**, pričom hodnota korešpondujúceho políčka bude `exponential ((double) 1 / priemer);`.
V prípade potreby generovania príchodu viacerích ľudí naraz, je potrebné zaškrtnúť **Multiple agents per arrival** a do novozobrazeného políčka určiť zdroj
empirického rozdelenia pravdepodobnosti. **Custom Distribution** tu môže nájsť využitie.
V tomto prvku sa väčšinou nastavujú parametre agentov v ktorých potrebujeme uchovávať čas vstupu do systému, konkrétne v akcii **On Exit**.

Sink [Blocks]
-------------
Vyhadzuje objekty zo systému. Akcia **On enter** je dôležitá pre výpočet pobytu v systéme. Nezabudnúť zmeniť typ agenta ak je to nutné.

Queue [Blocks]
--------------
Pri použití frontu je potrebné dať si pozor na zaškrtnutie **maximum capacity** (vo väčine prípadov na cvičeniach neboli fronty s obmedzenou kapacitou).

Delay [Blocks]
---------------
Dosť často využívané na modelovanie obsluhy.

Resource Pool [Blocks]
----------------------
Predstavuje zdroj pre nejaké prvky, v prípade cvičenia sa jednalo o pokladníčky.
**Resource type** nastavený na **static** určuje nehybné prvky, čo pokladničky sú, a **Capacity** určuje ich maximálny počet.
Avšak typ **New resource unit** v tomto prípade nebude náš custom **Visitor** ale **Agent**, nakoľko sa jedná o odlišné entity.
Tento objekt vie poskytnúť informáciu o využítí pomocou metódu `object.utilization()`.

Service [Blocks]
----------------
Nahradzuje kombináciu objektov **Queue** a **Delay**. Pre špecifikovanie zdrojových objektov ktoré budú v úlohe obsluhujúcich
je nutné zvoliť voľbu **Units of the same pool** a následne zadať názov konkrétneho objektu **Resource Pool**.
Zaškrtnutie políčka **Maximum queue capacity** má rovnaký význam ako pri samotnom **Queue** ako aj zadanie intervalov pre
čakanie pomocou nejakého rozdelenia.
V sekcii **Priorities / preemption** je možné nastaviť uprednostňovanie nejakých agentov pred inými, príklad na cvičení
`agent.parDisability == true ? 1 : 0` prioritizoval postihnutých navštevníkov.

Select Output [Blocks]
----------------------
Rozhodovací blok. Políčko **Probability** určuje pravdepodobnosť s ktorou je daný objekt odklonený na trasu **True**,
pričom **Condition** vyhodnocuje podmienku s efektom totožným ako v predchádzajúcom prípade.

Batch [Blocks]
--------------
Zlúči objekty do jedného nového, iného typu.

Unbatch [Blocks]
----------------
Rozbalí zlúčené objekty nejakého typu a na výstup ich pošle v type, ktorý mali, keď boli zlúčené.

Schedule [Blocks]
-----------------
