Agent
=====

Custom Distribution [Agent Components]
--------------------------------------
Slúži na definovanie empirického rozdelenia pravdepodobnosti.
Pri použití je potrebné zavolať metódu `getInt()` pre získanie nejakej hodnoty, napríklad v prvku **Source**.

Parameter [Agent Components]
----------------------------
Parametre môžu byť rôznych typov, príklad použitia typu **boolean** je z cvičenia, kedy 5% návštevníkov mali nejakú zdravotnú poruchu.  
Prípad použitia: `uniform() < 0.05 ? true : false`, čo značí, ak náhodné číslo vygenerované z rovnomerného rozdelenia je menšie ako
0.05, tak daný človek je postihnutý, teda **true**, v opačnom prípade **false**.

Variable [Agent Components]
---------------------------
Premenná, ktorá drží konkrétnu hodnotu špecifikovaného typu.