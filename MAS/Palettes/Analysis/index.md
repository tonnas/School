Analysis
========

Statistics [Data]
-----------------
Vypočítanie a zobrazovanie charakteristík premennej (stredná hodnota, min, max, ...)  
Príklad: `statTimeInModel.add(time() - agent.parInputTime);`, čo predstavuje priemernú dobu zákazníka v systéme.

Histogram Data [Data]
---------------------
Vykonanie štandardnej štatistickej analýzy hodnôt premennej
(stredná hodnota, min, max, odchýlka, veriácia, interval spoľahlivosti strednej hodnoty);
zostavovanie distribučnej funkcie alebo funkcie hustoty.  
Príklad: `hdWaitingTime.add(time() - agent.parWaitingStartTime);`

Data Set [Data]
---------------
Pre zaznamenávanie vývoja premennej, uchováva stanovený počet historických hodnôt.  
Príklad: `dsAverageWaitingTime.add(hdWaitingTime.count(), hdWaitingTime.mean());`
Často je potrebné odškrtnúť **Use time as horizontal axis**, nakoľko ako aj v prípade vyššie,
[X,Y] dáta sú poskytnuté súbežne a nejedná sa o čas. Je veľmi dobrý pre ukážku ustáľovania nejakej hodnoty.
V prípade vyššie sa do **Data Setu** postupne pridáva počet nameranných hodnôt spoločne s ich priemerom, ktoré sa neskôr ustália.

Bar Chart [Charts]
------------------
Zobrazovanie aktuálnej hodnoty premennej.    
  
Príklad: Zobrazovanie priemernej dĺžky frontu `queue.statsSize.mean()`,
pričom tento zdrojový kód je pridaný do sekcie **Data** po tom, ako je vybraná možnosť **Do not update data automatically**.  
  
Príklad: Zobrazovanie priemerného vyťaženia pracovníčky pri pokladni `queue.statsUtilization.mean() * 100`, pričom hodnota
má byť nastavená na **Fixed** v rozsahu od **0** do **100**, pokiaľ sa jedná o takýto prípad výpočtu.

Plot [Charts]
-------------
Zobrazovanie vývoja premennej zapísaného pomocou objektu **Data Set**.

Histogram [Charts]
------------------
Zobrazuje štatistiky zozbierané pomocou objektu **Histogram Data**.