**Slovenščina** · [English](cgt4tcs.md)

# Modul 1: Nekatere kombinatorične igre na particijah

**Teoretično računalništvo I**

**FAMNIT, Univerza na Primorskem**

**Jesen 2026**

**prof. Eric Gottlieb**[^1]

[^1]: Ti učni moduli so bili razviti s podporo Fulbrightove štipendije za ameriške znanstvenike. Avtor se zahvaljuje ameriškemu zunanjemu ministrstvu, ki sponzorira program Fulbright, gostiteljski ustanovi Univerzi na Primorskem in domači ustanovi Rhodes College.

V tem semestru bomo s teorijo kombinatoričnih iger ponazorili teme, ki jih bomo obravnavali pri predmetu. Namen je, da boste videli, kako matematiki v svojem raziskovalnem delu uporabljajo pojme, ki jih preučujemo. Začeli bomo z nekaj preprostimi kombinatoričnimi igrami. Cilj tega modula je, da se s kombinatoričnimi igrami seznanite na intuitiven način. Omenili bomo tudi nekaj strokovnih izrazov, ki bodo natančneje opredeljeni v poznejših modulih, kjer bomo raziskovali nekatere teoretične vidike kombinatoričnih iger. Začnimo!

---

## Odštevanje: »preprosta« kombinatorična igra

Predpostavimo, da imate kupček s 30 žetoni. Prijatelja Peter in Nina izmenično odstranjujeta 1, 2 ali 3 žetone s kupčka. Nina začne. Zmaga igralec, ki zadnji vzame žeton. Ali ima kateri od igralcev zmagovalno strategijo? Če jo ima, kateri in kako naj igra?

Pri toliko žetonih je težko videti, kaj se dogaja. Poglejmo, ali lahko ugotovimo, kaj se dogaja pri manjšem številu žetonov. Če je žeton en sam, Nina zmaga, če ga vzame. Pravzaprav *mora* zmagati, saj je to njena edina možna poteza. Če sta žetona dva, lahko Nina vzame enega ali oba. Če vzame le enega, potem Peter lahko (in mora) zmaga tako, da vzame zadnjega. Če pa vzame oba, zmaga Nina. Očitno naj Nina vzame oba žetona. Podobno naj pri treh žetonih Nina vzame vse tri, saj lahko Peter zmaga tako, da vzame preostale žetone, če Nina vzame enega ali dva.

To ponazarja pomembno razliko: ko rečemo, da ima Nina pri dveh žetonih na mizi zmagovalno strategijo, to ne pomeni, da zmaga ne glede na svoje poteze. Pomeni, da ima Nina pot do zmage ne glede na Peterjeve poteze. Zato bomo pri analizi vedno predpostavljali popolno (tj. brezhibno) igro obeh igralcev.

Poglejmo, kaj se zgodi pri štirih žetonih. Če Nina vzame enega, lahko Peter zmaga tako, da vzame tri. Če vzame dva, Peter zmaga tako, da vzame dva. Če vzame tri, Peter zmaga tako, da vzame enega. Z drugimi besedami: ne glede na Ninino potezo ima Peter zmagovalni odgovor. Peter ima torej pri štirih žetonih zmagovalno strategijo.

Dobro; naša analiza pokaže, da ima Nina zmagovalno strategijo pri enem, dveh ali treh žetonih, Peter pa lahko vsili zmago pri štirih žetonih.

| $n$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **zmagovalec** | N | N | N | P |  |  |  |  |  |  |  |  |  |

Pri petih žetonih postanejo stvari nekoliko zapletenejše. Jasno je, da Nina ne sme odstraniti treh žetonov, saj lahko Peter potem zmaga z odvzemom dveh. Prav tako ne sme vzeti dveh žetonov, saj lahko Peter potem zmaga z odvzemom treh. Kaj pa, če vzame en žeton? V tem primeru se Peter znajde v popolnoma enakem položaju kot Nina pri štirih žetonih — nima zmagovalne poteze. Z drugimi besedami: Nina je Petra pustila v izgubljenem položaju, zato ima zmagovalno strategijo!

Zdaj ste na vrsti vi.

**Vaja 1.** V skupini dopolnite spodnjo tabelo tako, da za dano število žetonov navedete igralca, ki ima zmagovalno strategijo.

| $n$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **zmagovalec** | N | N | N | P | N |  |  |  |  |  |  |  |  |

**Vaja 2.** Če niste naredili napake, bo za vaš odgovor pri Vaji 1 veljalo očitno pravilo. Ali se lahko domislite načina, kako dokazati, da pravilo velja za poljubno pozitivno število žetonov? Kaj vam pravilo pove o tem, kdo ima zmagovalno strategijo pri 30 žetonih?

Pri tej igri je vredno opaziti nekaj stvari:

1. Število 30 ni nič posebnega; lahko bi začeli s poljubnim naravnim številom žetonov.
2. Pravila bi lahko spremenili tako, da bi igralca smela odstraniti na primer 2 ali 5 žetonov. Lahko pa bi odstranjevala 1, 3, 4 ali 6 žetonov. Z drugimi besedami: števila 1, 2 in 3 niso nič posebnega; za dovoljene poteze bi lahko izbrali poljubno množico pozitivnih celih števil. Če želimo takšne igre zapisati jedrnato, lahko za tri omenjene igre uporabimo oznake $S_{\{1, 2, 3\}}$, $S_{\{2,5\}}$ in $S_{\{1, 3, 4, 6\}}$.
3. Predpostavili smo, da oba igralca smeta izvesti enake poteze. Takšne igre imenujemo *nepristranske*. Nasprotno pa igre, v katerih imata igralca na voljo različne poteze, imenujemo *partizanske*. Lahko bi na primer določili, da Peter lahko odstrani 1, 2 ali 3 žetone, Nina pa 2 ali 5 žetonov. Takšno igro bi lahko označili z $S_{\{2,5\}, \{1, 2, 3\}}$. Pri tem predmetu se bomo osredotočali predvsem na nepristranske igre, vendar bomo občasno obravnavali tudi partizanske.
4. Pravila bi lahko spremenili tudi tako, da bi zadnji igralec, ki vzame žeton, izgubil. Prvotni dogovor imenujemo *normalna igra*, drugega pa *igra misère*. Preučujemo oba dogovora, vendar ima normalna igra, kot bomo videli, lepše teoretične lastnosti. Pri predmetu se bomo osredotočali predvsem na normalno igro, vendar bomo občasno zašli tudi na področje igre misère.
5. Pri **Odštevanju** se igralca ne moreta izenačiti in igra ne more trajati v nedogled, kot bi se lahko, če bi smela poleg odstranjevanja žetone tudi dodajati na kupček. Igre, pri katerih je zagotovljeno, da se igra iz poljubnega položaja konča po končnem številu korakov, imenujemo *kratke*. Pri tem predmetu se bomo ukvarjali izključno s kratkimi igrami.
6. Pri **Odštevanju** smo videli, da ima vedno eden od igralcev zmagovalno strategijo. To bo veljalo za vse igre, ki jih bomo obravnavali pri tem predmetu.
7. Pri **Odštevanju** igra traja, dokler ne zmanjka žetonov. Položaj, iz katerega ni možna nobena poteza, imenujemo *končni položaj*. Pri normalni igri Peter samodejno zmaga v vsakem končnem položaju.

**Vaja 3.** Dopolnite spodnjo tabelo za $S_{\{2,5\}}$.

| $n$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **zmagovalec** |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

Kot smo videli, je lahko precej zapleteno slediti temu, kateri igralec ima zmagovalno strategijo. Razlog je, da Nina začne kot naslednja igralka, po njeni potezi pa Peter postane naslednji igralec in Nina prejšnja igralka. Analiza je preprostejša, če o položaju govorimo kot o položaju, ki ga lahko dobi *naslednji* ali *prejšnji* igralec, namesto da ga pripisujemo določeni osebi. Položaj, ki ga lahko dobi naslednji (oziroma prejšnji) igralec, imenujemo $\mathcal{N}$- (oziroma $\mathcal{P}$-) položaj.

Ta razdelek zaključimo s pomembnim opažanjem, ki je uporabno pri analizi **Odštevanja** ali katerekoli druge kratke nepristranske kombinatorične igre.

> **Opažanje 1.** $\mathcal{N}$-položaji so natanko tisti, iz katerih obstaja poteza v $\mathcal{P}$-položaj. $\mathcal{P}$-položaji pa so natanko tisti, iz katerih ne obstaja poteza v $\mathcal{P}$-položaj.

---

## Nim

V igri **Nim** začnemo z več kupčki žetonov. Igralca izmenično izbereta enega od kupčkov in z njega odstranita poljubno pozitivno število žetonov. Položaj s $k$ kupčki, pri katerem $j$-ti kupček vsebuje $n_j$ žetonov, označimo z $n_1/\ldots/n_k$.

**Nim** ima ključno vlogo pri analizi kratkih nepristranskih iger. O tej pomembni igri bomo povedali več pozneje; za zdaj jo bomo uporabili za vajo naših na novo pridobljenih veščin iz teorije kombinatoričnih iger.

**Vaja 4.** Kateri igralec ima zmagovalno strategijo v igri **Nim** v naslednjih položajih?

1. Noben kupček, noben žeton
2. En kupček z $n$ žetoni, kjer je $n$ pozitivno celo število.
3. $1/2$
4. $1/2/3$
5. $n/n$, kjer je $n$ pozitivno celo število.
6. $m/n$, kjer sta $m$ in $n$ različni pozitivni celi števili.
7. $1/3/5/7$ je klasični začetni položaj. Če ne poznate strategije igre **Nim**, je težko vedeti, ali gre za $\mathcal{P}$- ali $\mathcal{N}$-položaj, vendar je dobro, da o njem razmislite, da boste dobili občutek, kako zahtevno je to vprašanje.

---

## Particije in Youngovi diagrami

V zadnjih letih smo[^2] preučevali različne kombinatorične igre na particijah celih števil. Pri tem predmetu boste spoznali nekatere od teh iger in načine, kako se pri njihovem preučevanju uporabljajo nekatere teme tega predmeta. Preden lahko igre opišemo, se moramo pogovoriti o particijah in Youngovih diagramih.

[^2]: »Mi« se tu nanaša na prof. Erica Gottlieba, Matjaža Krnca in Petra Muršiča ter na več študentskih sodelavcev z Univerze na Primorskem in Rhodes Collegea.

*Particija celega števila* (ali preprosto *particija*) nenegativnega celega števila $n$ je zapis števila $n$ kot vsote pozitivnih celih števil, pri čemer vrstni red sumandov ni pomemben. Sumande imenujemo *deli* particije. Tu so vse particije prvih šestih nenegativnih celih števil:

| 0 | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- |
|  | 1 | 2<br>

<br>1+1 | 3<br>

<br>2+1<br>

<br>1+1+1 | 4<br>

<br>3+1<br>

<br>2+2<br>

<br>2+1+1<br>

<br>1+1+1+1 | 5<br>

<br>4+1<br>

<br>3+2<br>

<br>3+1+1<br>

<br>2+2+1<br>

<br>2+1+1+1<br>

<br>1+1+1+1+1 |

Ker particij ne razlikujemo glede na vrstni red delov, jih lahko uredimo, kakor želimo. Uporabili bomo kanonično obliko, v kateri so deli zapisani v nenaraščajočem vrstnem redu, kot je prikazano zgoraj. Z $p(n)$ označimo število particij pozitivnega celega števila $n$. Torej


$$p(1) = 1 \quad p(2) = 2 \quad p(3) = 3 \quad p(4) = 5 \quad p(5) = 7$$


Particija števila 0 je ena sama, namreč prazna vsota, zato je $p(0) = 1$.

**Vaja 5.** Izračunajte $p(6)$, $p(7)$ in $p(8)$.

Zgornji zapis je nekoliko neroden. Da bi bil jedrnatejši, bomo vsak znak $+$ v particiji zamenjali z vejico in rezultat zapisali v oglatih oklepajih. Če je torej $n = \lambda_1 + \cdots + \lambda_r$ particija, bomo zapisali $\lambda = [\lambda_1, \ldots, \lambda_r]$. Število $n$ imenujemo *velikost* particije $\lambda$ in pišemo $\lambda \vdash n$. Particijo $5 + 4 + 4 + 1 + 1 + 1$ velikosti 16 bi na primer zapisali kot $[5,4,4,1,1,1]$. Če želimo biti še jedrnatejši, lahko isto particijo z eksponentnim zapisom zapišemo kot $[5,4^2,1^3]$. Edino particijo števila nič označimo z $[\ ]$.

Tudi s poenostavljenim zapisom si je particije težko predstavljati. Zato uvedemo *Youngove diagrame*: to so levo poravnane razporeditve kvadratkov, pri katerih je število kvadratkov v $j$-ti vrstici od zgoraj enako $j$-temu delu particije. Youngov diagram zgoraj omenjene particije je na primer prikazan na Sliki 1. Izraza »particija« in »Youngov diagram« bomo uporabljali izmenično, množico vseh particij pa bomo označili z $\mathbb{Y}$.

*Slika 1: Youngova diagrama particije $[5,4^2,1^3]$ in njej konjugirane particije $[6,3^3,1]$.*

Iz Youngovega diagrama $\lambda$ s $k$ vrsticami lahko sestavimo nov Youngov diagram $\lambda'$ s $k$ stolpci, pri katerem je število kvadratkov v $j$-tem stolpcu diagrama $\lambda'$ enako številu kvadratkov v $j$-ti vrstici diagrama $\lambda$ za vsak $j \in \{1, 2, \ldots, k\}$. Za $\lambda'$ pravimo, da je *konjugirana* particija $\lambda$. Particija je *samokonjugirana*, če velja $\lambda' = \lambda$. Bralec lahko preveri, da je $(\lambda')' = \lambda$. Slika 1 prikazuje konjugirano particijo $[5,4^2,1^3]$.

Čeprav veliko kombinatoričnih objektov štejemo z ličnimi formulami, to ne velja za particije. Obstajajo pa zelo lepe povezave med različnimi razredi particij. Število particij števila $n$ na lihe dele je na primer enako številu particij števila $n$ na različne dele. Lastnosti množice particij so preučevali številni znameniti matematiki, med njimi Hardy in Ramanujan, Euler, Rademacher, Sylvester, MacMahon, Dyson in Ono.

---

## LCTR

Oglejmo si kombinatorično igro **LCTR** na $\mathbb{Y}$, v kateri igralca izmenično odstranjujeta bodisi skrajno levi stolpec bodisi zgornjo vrstico dane particije $\lambda$, dokler ne dosežeta prazne particije (ki je končni položaj). Študentka Univerze na Primorskem Jelena Ilić je igro **LCTR** preučevala v okviru svojega diplomskega projekta.

**Vaja 6.** Kateri igralec ima v **LCTR** zmagovalno strategijo pri naslednjih particijah?

1. $[\ ]$
2. $[1]$
3. $[c]$, kjer je $c$ pozitivno celo število. Particijo te oblike imenujemo *vrstica*.
4. $[1^r]$, kjer je $r$ pozitivno celo število. Particijo te oblike imenujemo *stolpec*.
5. $[c, 1^{r-1}]$, kjer sta $c$ in $r$ pozitivni celi števili. Particijo te oblike imenujemo *kavelj*.
6. $[c^r]$, kjer sta $c$ in $r$ pozitivni celi števili. Particijo te oblike imenujemo *pravokotnik*.
7. $[k, k-1, \ldots, 2, 1]$, kjer je $k$ pozitivno celo število. Particijo te oblike imenujemo *stopnišče*.
8. $[5,4^2,1^3]$

**Vaja 7.** Pokažite, da je v **LCTR** particija $\lambda$ v $\mathcal{P}$ natanko tedaj, ko je v $\mathcal{P}$ tudi $\lambda'$.

Za igro z lastnostjo, omenjeno v Vaji 7, pravimo, da je *konjugatno invariantna*.

---

## CRIM

V igri **LCTR** smemo odstraniti le skrajno levi stolpec ali zgornjo vrstico Youngovega diagrama. Kaj pa, če lahko igralca odstranita poljubno vrstico ali stolpec, pri čemer velja, da se preostali deli Youngovega diagrama združijo, če odstranjena vrstica ali stolpec ni niti prvi niti zadnji? To igro imenujemo **CRIM** oziroma *column-row impartial merge*; glejte Sliko 2.

*Slika 2: Dovoljene poteze v igri CRIM iz $[5,4^2,1^3]$.*

**Vaja 8.** Kateri igralec ima v **CRIM** zmagovalno strategijo pri naslednjih particijah?

1. $[\ ]$
2. $[1]$
3. $[c]$
4. $[1^r]$
5. $[c, 1^{r-1}]$
6. $[c^r]$
7. $[k, k-1, \ldots, 2, 1]$
8. $[5,4^2,1^3]$

**Vaja 9.** Ali je **CRIM** konjugatno invariantna? Zakaj oziroma zakaj ne?

---

## Vogali

Kvadratek Youngovega diagrama imenujemo *vogal*, če pod njim ali desno od njega ni nobenega kvadratka. V igri **Vogali** igralca izmenično odstranjujeta neprazno podmnožico vogalov particije; glejte Sliko 3.

*Slika 3: Vogali particije $[5,4^2,1^3]$ so osenčeni. Poteze ustrezajo odstranitvi neprazne podmnožice vogalov.*

**Vaja 10.** Kateri igralec ima v **Vogalih** zmagovalno strategijo pri naslednjih particijah?

1. $[\ ]$
2. $[1]$
3. $[c]$
4. $[1^r]$
5. $[c, 1^{r-1}]$
6. $[c^r]$
7. $[k, k-1, \ldots, 2, 1]$
8. $[5,4^2,1^3]$

**Vaja 11.** Ali je igra **Vogali** konjugatno invariantna? Zakaj oziroma zakaj ne?
