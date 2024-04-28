# LIN
Poznamky z linuxu

# Aktualizacia systemu

najprv si aktualizujeme repozitare: `sudo apt update`

potom si aktualizujeme system a aplikacie: `sudo apt upgrade`

ked si chceme nieco nainstalovat tak pouzijeme `sudo apt install nazov_balicka`

ked si chceme nieco odinstalovat tak pouzijeme `sudo apt remove nazov_balicka` alebo ked chceme aj kofiguracne subory tak `sudo apt purge nazov_balicka`

# Linux file hrierarchy system

absolutna cesta `/root/Downloads`

relativna cesta `./Downloads`

prikaz `pwd` nam vypise kde sa nachadzame

medzi pricinkami sa presuvame pomocou `cd`

presunutie o priecinot hore: `cd ..`

presun pomocou absolutnej cesty: `cd /root/Downloads`

presun pomocou relativnej cesty: `cd ./Downloads` alebo `cd Downloads`

`man prikaz` nam ukaze manualovu stranku pre dany prikaz

ak sa nachadzate v `/home/student/Downloads/` a chcete ist do `/root/`: `cd ../../../root`

## prikaz `ls`

`ls` nam vypise obsah priecinku

| prikaz | vysvetlenie |
| --- | --- |
| `ls` | vypise obsah priecinku |
| `ls -l` | vypise dlhy vypis obsahu priecinka |
| `ls -a` | vypise vsetky subory a priecinky |
| `ls -lh` | vypise dlhy vypis a prepocita velkost suboru do citatelnej formy (KiB, MiB, GiB, ...) |
| `ls -t` | zoradi obsah priecinka podla casu (je lepsie ked to pouzite s `-l` prepinacom) |
| `ls -S` | zoradi obsah priecinka podla velkosti (je lepsie ked to pouzite s `-l` prepinacom) |
| `ls -r` | vypise obsah suboru v opacnom poradi |
| `ls /root` | vypise obsah priecinka `root` z akejkolvek polohy |

## prikaz `tree`

nainstalujeme si to pomocou `sudo apt install tree`

| prikaz | vysvetlenie |
| --- | --- |
| `tree /` | vypise stromovu strukturu korenoveho adresara |
| `tree -L cislo` | vypíše iba určitý počet podpriečinkov (hlbka) |
| `tree -d` | vypise iba priecinky |

## vytvaranie priecinkov

| prikaz | vysvetlenie |
| --- | --- |
| `mkdir nazov` | vytvori priecinok |
| `mkdir -v nazov` | vypise ake priecinky sme vytvorili |
| `mkdir "super meno"` | tak mozete vytvorit priecinok s divnymi znakmi (medzera, @, #, !, ...) |
| `mkdir 'supre meno'` | mozete pouzit aj apostrofy |
| `mkdir predmety{1..20}` | vytvori predmey1, predmety2, predmety3, ... az predmety20 |
| `mkdir -pv europa/{EU/{pevnina/{euro/{svk,ger,fra},non-euro/{cze,pl,hu}},ostrov/irl},non-EU/{pevnina/sui,ostrov/obr/{en,no,wls,sco}}}` | 

## mazanie suborov a priecinkov

| prikaz | vysvetlenie |
| --- | --- |
| `rm nazov` | vymaze **subor** |
| `rmdir nazov` | vymaze **prazdny priecinok** (nepouziva sa) |
| `rm -r nazov` | vymaze priecinok a vsetko v nom |
| `rm -r *` | vymaze vsetko v priecinku, v ktorom sa nachadzame |
| `rm cast_nazvu*` | vymaze vsetky subory, ktore zacinaju na ten nazov |

## vytvaranie suborov

| prikaz | vysvetlenie |
| --- | --- |
| `touch` | funguje podobne ako mkdir ale vieme nim modifikovat datum vytvorenia, upravy, atd. |
| `touch nazov` | vytvori subor |

## kopirovanie suborov

| prikaz | vysvetlenie |
| --- | --- |
| `cp nazov nazov2` | skopiruje a moze aj premenovat subor |
| `cp -i nazov nazov2` | ak uz taky existuje tak ho prepise |
| `cp -r` | skopiruje priecinky |

## presuvanie suborov

| prikaz | vysvetlenie |
| --- | --- |
| `mv` | take iste ako cp |
| `mv nazov nazov2` | pouziva sa premenovanie suborov |

## textovy editor

| prikaz | vysvetlenie |
| --- | --- |
| `nano nazov` | user firendly editor |
| `vim nazov` | pokrocily editor |

# Skriptovanie - BASH

* interpretovany jazyk
* príkazový interpreter - sprostredkúva interakciu medzi používateľom a počítačom
* BASH - bourne again shell ("znovuzrodený shell")
* jazyk na skriptovanie
* najpoužívanejší skriptovací jazyk v Linux-e
* vsetky shelly najdeme v `/etc/shells` (`cat /etc/shells`)
* shell pouzivatelov najdeme v `/etc/passwd` (`cat /etc/passwd`)

## systemove premenne
* `printenv` - vypise vsetky systemove premenne
* `$SHELL` - aky shell pouzivame
* `$USER` - za akeho pouzivatela sme prihlaseny
* `$PWD` - kde sme
* ak chceme daco vypisat napr. shell: `echo $SHELL`
* vieme si vytvorit systemovu premennu (iba pre tento terminal, ked zatvorime a znova otvorime terminal uz tam nebude) pomocou `export HODINA=linux` a vypisat pomocou `echo $HODINA`
* systemovu premennu vymazeme pomocou `unset HODINA`

## meta znaky (?,*,[],/,~, >,>>,{}, |, 2>)

| znak | vysvetlenie | priklad | vysvetlenie |
| --- | --- | --- | --- |
| ? | nahradza 1 znak | `echo ????` | vypise vsetko co 4 znaky |
| * | nahradza nekonecno znakov | `echo *.txt` | vypise vsetko co sa konci na `.txt` |
| [] | mnozina znakov | `echo [DS]*` | vypise vsetko co sa zacina na D alebo S |
| / | root (kmenovy) adresar (priecinok) | `cd /` | presunieme sa do kmenoveho adresara |
| ~ | domovsky adresar (priecinok), to iste je aj `$HOME` a `/home/nazovPouzivatela/` | `cd ~` | presunieme sa do domovskeho priecinka |
| {} | rozsah | `echo {a..g}` alebo `touch file{1..5}` | vypise: `abcdefg` alebo vytvori: `file1`, `file2`, `file3`, `file4`, `file5` |
| > | prepise obsah suboru | `cat subor1.txt > subor2.txt` | prepise to co bolo v `subor1` do `subor2` |
| >> | dopise do suboru | `cat subor1.txt >> subor2.txt` | dopise to co bolo v `subor1` do `subor2` |
| \| | presmeruje vystup z jednoho pridazu do druheho | `ls \| grep subor` | zisti obsah priecinka a to presmeruje do prikazu grep, ktory nam najde vsetko co obsahuje `subor` |
| 2> | presmeruje vsetky errory |

## skriptovanie

* subor na skripty vzdy bude koncit na `.sh` (`superSkript.sh`)
* na zaciatku musi byt shebang (bash: `#!/bin/bash`, mozeme pouzit aj python: `#!/usr/bin/env python`)
* aby sme mohli sputit skrip musime mu dat `x` pravo (`chmod +x superSkript.sh`)
* skripty spustame `./superSkript.sh` alebo ked nam to nejde tak `bash ./superSkript.sh` ale NEODPORUCA SA TO
* prikaz `echo` ma prepinac `-e`, ktory nam bude vypisovat aj ecsapovane znaky opacnym lomkou (`echo "Dnes je super den\n"` vypise `Dnes je super den\n` ale `echo -e "Dnes je super den\n"` vypise `Dnes je super den`)

### uvodzovky `" "`, apostrof `' '`, opacny apostrof `` ` ` ``, opacna lomka `\`
* Úvodzovky `" "` a apostrofy `' '` odoberaju niektorym metaznakom ich specialny vyznam
* opačná lomka `\`robi to iste ale iba pre jeden znak
* opacny apostrof `` ` ` `` - vyraz medzi opacnymi apostrofami sa nahradi textovym vystupom prikazu

### komenty
* jednoriadkovy koment:
```Bash
# toto je koment
```

* viacriadkovy koment
```Bash
:'
musi
sa
zacinat
a
konit
apostrofom
'
```
alebo
```Bash
:<< superKoment
musi
sa
zacinat
a
koncit
rovnakym
slovom
superKoment
```

### vypis do terminalu `echo`
* príkaz `echo` sa používa na zobrazenie textu, správy, hodnoty premennej na obrazovke
* da sa pouzit aj `printf`, ktory ma rovnaku syntax ako v `C`
* prepínače:

| prepinac | vysvetlenie |
| --- | --- |
| `-e` | vypise aj opacne lomky |
| `-E` | nevypise opacne lomy (vychodzie nastavenie) |
| `-n` | nebude davat na koniec (neviditelny) znak noveho riadku |

### podmienky
* zacina sa `if`
* podmienka sa pise do hranatych zatvoriek `[ podminka ]`
* potom nasleduje `then`
* ked potrebujeme dame tam `else` alebo `elif [ podmineka ]` (pri `elif` potrebujeme taktiez `then` a `fi`)
* na uplnom konci podminky (alebo vnorenej podminky) je `fi`
* prepinace, ktore pozname su:

| prepinac | vysvetlenie |
| --- | --- |
| `-gt` | vecsie ako |
| `-eq` | rovne |
| `-lt` | mensie ako |
| `-ge` | vecsie alebo rovne |
| `-le` | mensie alebo rovne |
| `-d` | ak existuje taky priecinok (adresar) |
| `-f` | ak existuje taky subor |

```Bash
prveC = 10
druheC = 20

if [ $prveC -gt $druheC ]
then
  echo Podmienka plati
fi
```
```Bash
prveC = 10
druheC = 20

if [ $prveC -gt $druheC ]
then
  echo Podmienka plati
else
  echo Podmienka neplati
fi
```

### nacitavanie z konzoly
* prikaz `read`
* prepinace:

| prepinac | vysvetlenie |
| --- | --- |
| `-t` | nam obmedzi cas na napisanie |
| `-p` | mozeme mu tam daco napisat napr. `Zadaj cislo: ` |
| `-n` | obmedzi pocet znakov |
| `-s` | pouziva sa pri heslach (nevidis co pises) |
