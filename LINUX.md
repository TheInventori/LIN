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
* prikazom `man [nazov prikazu]` si vieme pozriet manualovu stranku prikazu
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
  * `rm -r*` vymaze uplne vsetko
  * `rm -r [cast nazvu]*` vymaze vsetko co sa zacina na text zadany pred hviezdickou
________________________________________________________________________________________
### FUN PRIKAZ => VLACIK V TERMINALE
* instaluje sa prikazom `sudo apt install sl`
* nasledovne sa spusti prikazom `sl` 
________________________________________________________________________________________

## Praca so subormi
* subor vieme vytvorit prikazom `touch`
* prikaz `cp` => vieme kopirovat aj premenovat subor
* `cp -i` => prepisanie suboru
<br>

* ak chceme kopirovat priecinok pouzivame `cp -r`
<br>

* prikazom `mv` => dokaze presuvat, taktiez vie premenovat subor ale len ak ho presuvame do rovnakeho priecinka kde uz je
<br>

* na upravu textovych suborov sluzi textovy editor **NANO** spusteny prikazom `nano [nazov suboru]`
<br>

**Prikazy na vypis suboru**
* prikaz `cat` sluzi na pracu s textovymi subormi
  * `cat [nazov]` => vypise obsah suboru
  * `cat > [nazov]` => dokaze vytvorit subor
  * `cat [nazov1] > [nazov2]` => prepise subor
  * `cat [nazov1] >> [nazov2]` => pripise obsah jedneho suboru do druheho
  * `cat [nazov1] [nazov2] > [nazov3]` => spoji subory do dalsieho, obsah povodnych sa ponechava
  * `cat [subor] > [subor]` => ak je pouzity rovnaky nazov suboru dvakrat, subor vymaze
 
* prikaz `wc` s pomocou prepincov vypise riadky, slova, bajty a nazov
* prikaz `split` rozdeli subor podla pouziteho prepinaca
* prikaz `head` vyber parametrov suboru z hora
* prikaz `tail` vyber parametrov suboru z dola
<br>

**PRE VIAC INFO NEZABUDAJTE NA PRIKAZ `man [nazov prikazu]`**
<br>

* symbol `|` (alebo pipe) presmeruje vystup prveho prikazu do druheho (pouzije vystup prveho prikazu ako vstup pre ten druhy)
  * napr. `cat [nazov] | tail -n [cislo]` z vypisu suboru [nazov] vypise tolko riadkov od spodu ake bolo zadane [cislo]
<br>

**Prikazy na upravu suboru**
* prikaz `tr` sluzi na zamenu nejakeho symbolu v textovom subore za iny
  * pre viac info pozri `man tr`
* prikaz `sort` uz z nazvu vyplyva ze sluzi na zoradenie parametrov v subore
  * zoradenie sa lisi podla pouziteho prepinaca, pozri `man sort`
* prikaz `cut` sluzi na vystrihnutie konkretnych dat v subore
  * ako `sort` tak aj `cut` sa lisi podla pouziteho prepinaca, pozri `man cut`
<br>

**Porovnavacie prikazy**
* prikaz `paste`
  * vypise za sebou vsetky zadane subory napr. `paste [nazov1] [nazov2] [nazov3]`
* prikaz `diff`
  * postupne po riadku porovna subory napr. `diff [nazov1] [nazov2]`
* prikaz `cmp`
  * porovna subory byte po byte, presne znaky ktore sa tam vyskytuju napr. `cmp [nazov1] [nazov2]`
<br>

* prikaz `grep`
  * vyhlada v subore cast textu, retazca
  * podla roznych prepinacov vieme zas a znova ovplyvnit spravanie prikazu
  * pozri `man grep`
<br>

**Vyhladavacie prikazy**
* `which` => vyhladava velmi rychlo, prehladava priecinok bin, hlada prikazy
* `whereis` => prehladava aj manualove stranky (teda `man`), existuje cesta, `echo &PATH`
* `find` => prehladava cely system, ak sa nema pravo sa dostat do nejakeho priecinku vypise ERROR
* `locate` => je vykonnejsi teda rychlejsi ako `find`, avsak nieje nainstalovany (treba doinstalovat `sudo apt install plocate` to "p" tam byt ma) 
  * pracuje s databazou, ak chceme spravne pouzivat tento prikaz treba ju aktualizovat `sudo updatedb`
<br>

**Linkovanie / linky**
* pozname dva zakladne plus jeden dalsi typ linku
  * *soft* link => uchovava cestu na subor alebo priecinok
  * *hard* link => uchovava a synchronizuje obsah suboru (len subor!!)
  * *dead link* mrtvy odkaz => je to druhe *soft* linku ktory vsak ukazuje na neexistujucu cestu (subor alebo pricinok uz neexistuje)
<br>

* `ln -s [stara_cesta] [nova_cesta]` vytvory *soft* link
* `ln [stara_cesta] [nova_cesta]` vytvory *hard* link (prikaz bez prepinaca)
  * i uzol ``inode`` (hard link) => oznacuje subory s rovnakym obsahom na dvoch rozdielnych miestach
  * `find -inum [inode_cislo]` => vypise subory ktore maju ``inode`` rovnaky ako bol zadany (rovnake subory)
  <br>

  * `ls -li` prepinac ku prikazu `ls` ktory vo vypise obsahu priecinku zobrazi aj ``inode`` cislo
<br>

**Komprimovanie a archivacia**
* `compress`
* `gzip`
* `bzip2`
<br>

* na pouzitie prikazu `compress` je potrebne prikaz nainstalovat `sudo apt install ncompress`
<br>

* tieto komprimacne prikazy neuchovavaju povodny subor preto ak chceme zachovat aj nekomprimovany subor mozeme vyuzit tuto metodu pomocou `|`
  * `cat [nazov] | compress > [nazov.z]` z vystupu prikazu cat, co je vypis suboru, spravy skomprimovany subor takze sa original nijako nezmeni
<br>

* pre viac info ako komprimovat a dekomprimovat pomocou tychto prikazov vyuzite `man [komprimovaci_prikaz]`
<br>

**Prava** 
* pozname tri zakladne prava `r`, `w`, `x`, alebo aj read, write, execute
* tieto prava vieme pridelit trom skupinam
  * `user`
  * `group`
  * `other`
* teda prava sa zobrazuju takto
  * xrwxrwxrw
  * kazde `xrw` je pre jednu skupinu teda `u` `g` a `o`
<br>

* tieto prava vieme pridavat, uberat alebo priamo nastavit pomocou `+` `-` `=`
  * napr. `o - r` (skupine `o` teda other pomocou operatora `-` minus, odoberieme pravo `r` teda read)
* nemiesto znakov `r`, `w`, `x`, vieme taktiez pouzit cislo od 0 po 7
<br>
| cislo | read | write | execute |
| ---| --- | --- | --- |
| 0 | / | / | / |
| 1 | / | / | x |
