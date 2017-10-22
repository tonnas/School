Model
======


Cas od 4:00 do 23:00
---------------------
V pripade prveho testu, kde riesime replikacie, sa tento cas nastavuje priamo v `replications`, nie v nstaveniach `main`


Môžeme modelovať pomocou exponenciálneho rozdelenia pravdepodobnosti so strednou dobou 1,2 minúty
--------------------------------------------------------------------------------------------------
Tieto nastavenia prisluchaju objektu source. Nastavime `Interarrival time`, kedze budu agenti prichadzat v casovych intervaloch

Interarrival time nastavime na `exponential(1/1.2) minutes`. V tomto pripade nie je nutne nastavit pretypovanie na `(double)`, pretoze cislo 1.2 uz je typu double ktory potrebujeme


Dobu potrebnú na zakúpenie cestovného lístka môžeme modelovať pomocou exponenciálneho rozdelenia pravdepodobnosti so strednou dobou obsluhy 75 sekúnd
-----------------------------------------------------------------------------------------------------------------------------------------------------
V tomto pripade mame dve moznosti.. pouzit objekt `delay` alebo `service`. Service je pohodlnejsie a prisposobivejsie. 
Ak nie je uvedene inak, nastavime `Maximum queue capacity` pre neobmedzeny pocet agentov cakajucich v rade.
`Delay time` v tomto pripade nastavime na `exponential((double)1/75) seconds`. 

Obsluha pre delay
------------------
Pouzijeme objekt `Resource Pool` v ktorom kapacitu nastavime na `2`. Podla zadania potrebujeme dve pracovnicky/priehradky.
V uz pridanom objekte `service` pomocou `+` pri `Resource sets (alternatives)` pridame nas vytvoreny `resourcePool`, ktory bude v moznostiach

Statistika
===========

Ako dlho (v minutach) bude cestujuci cakat na zaciatok obsluhy.
----------------------------------------------------------------------------------------
Ako prve potrebujeme o cestujucom vediet kedy zacal cakat. Pre nas najlepsie je vytvorit parameter `parStartWaiting` v nasom agentovi. Agenta je potrebne vytvorit, ak este nie je vytvoreny.
`parStartWaiting` nastavime na `double` a default value na `0`. Agenta mame pre statisticu vytvoreneho.

Potrebujeme vytvorit statisticu. Mozeme ju nazvat `statWaitingTime` a nastavime na `Discrete` (malo by byt nastavene defaultne).
V objekte `service` v casti `Action` -> `On enter` pridame java kod. Najskor naplnime `agent.parStartWaiting = time();`. Teda agent prave zacal cakat.
Nasledne v objekte `service` v casti `Action` -> `On enter delay` pridame potrebne data do statistiky.. `statWaitingTime.add(time() - agent.parStartOfWaiting);` aktualny cas - zaciatok cakania nam da dlzku cakania v rade. 
V statistike dlzky cakania mame vsetko co treba 


Aký bude priemerný počet čakajúcich cestujúcich v rade
------------------------------------------------------


Replikacie
==========

