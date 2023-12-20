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
