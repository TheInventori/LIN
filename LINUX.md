# LINUX
### Basic prikazy na aktualizaciu
* `sudo apt update`  => aktualizacia repozitaru
* `sudo apt upgrade` => aktualizacia software a kernel

## Zaklady suborovej hierarchie
* **absolutna cesta** => vzdy sa zacina v kmenovom adresari oznacenom znakom `/`
  * presna cesta od zaciatku az ku pozadovanemu suboru ci priecinku napr. `/home/student/`
* **realtivna cesta** => zacina sa oznacenim `.` alebo bez `/` na zaciatku
  * cesta relativna od toho kde sa prave nachadzate napr. `./Downloads`

### Prikazy na orientaciu v suborovom systeme linuxu
* `pwd` => zobrazi vasu momentalnu poziciu
* `cd` => sluzi na presun medzi priecinkami
  * `cd..` => presun o priecinok vyssie
  * `cd /home/student` => presun pomocou absolutnej cesty
  * `cd ./Downloads` alebo `cd Downloads` => presun pomocou relativnej cesty
* `ls` => prikaz na vypis obsahu priecinka

### Manualove stranky
* prikazom `man` a nazvom prikazu si vieme pozriet manualovu stranku prikazu
  *napr.  `man ls` zobrazi manualovu stranku pre prikaz `ls` (vypis obsahu priecinka)

* pomocou manualovych stranok si vieme pozriet ake mozne `prepinace` prikazy mozu mat
  * `prepinac` sluzi ako doplnenie prikazu ak chceme aby spravil nieco konkretne napr. `ls` s prepinacom `-l` = (`ls -l`), vypise dlhsi a podrobnejsi obsah priecinku
 
### Priecinky a prikaz `tree`
* prikaz tree sluzi podobne ako ls na vypis obsahu priecinku no zobrazy taktiez podpirecinky a ich podpriecinky ci subory v podobe stromu
  * instaluje sa pomocou prikazu `sudo apt install tree`
* pomocou prepinacov vieme vybrat co presne chceme zobrazit
  * `/` vypis celeho stromu adresara root
  * `-L` + cislo vypise strom len do hlbky danej cislom za prepinacom
  * `-d` vypise len priecinky
 <br>
 
* skrz linux terminal vieme priecinky vytvarat priecinky a to prikazom `mkdir`
  * napr. `mkdir priecinok` vytvory priecinok s nazvom priecinok
* ak chceme priecinok s viac-slovnym nazvom vyuzijeme
  * uvodzovky => `mkdir "priecinok jeden"`
  * apostrofy => `mkdir 'priecinok dva'`
  * specialny symbol => `mkdir priecinok\jeden-dva_tri`
 
* priencinky vieme taktiez mazat prikazom `rm` (tento prikaz vieme pouzit aj na mazanie suborov)
  * `rm -r` na uplne odstranenie celeho priecinku aj s jeho obsahom
 
### FUN INTERSECTION => VLACIK V TERMINALE
* instaluje sa prikazom `sudo apt install sl`
* nasledovne sa spusti prikazom `sl`

