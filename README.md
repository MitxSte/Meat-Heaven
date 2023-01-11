# Meat Heaven

63210312 Mitjan Stepančič

63190277 David Šeruga

## Uvod

### Ideja
V današnjih časih je postalo zelo pupolarno, da ljudje kupujejo čim več lokalno pridelane hrane. Prav tako ljudje kupujejo Slovensko rejeno meso. Nekaj take ponudbe že ima Maxi market v Ljubljani.

Midva pa bi rada trg pripeljala lokalnim kmetom. Da bodo lahko oni direkno naprej prodajali svoje meso in se tako na nek način znebili posrednikov.

Tukaj v pomoč pride informacijski sistem Meat Heaven, ki omogoča prav to. Povezuje lokalne živinorejce s kupci. Kmetje bodo lahko svoje meso objavil na spletno trgovino, stranke pa bodo med različno ponudbo mesa prosto brskale. 
Prav tako bodo lahko stranke poslale povpraševanje po specifičnih kosih mesa, kot tudi shranile izdelke, s katerimi so po nakupu zadovoljne, za ponoven nakup.

### Funkcionalnosti
Kmetje se lahko prijavo in objavijo svojo ponudbo. Za to ponudbo bi bilo priporočljivo, če jo klasificirajo, da jo lahko ljudje, ki iščejo kaj specifičnega, lažje najdejo

Klasificirali bi lahko svoje meso po:
- vrsti mesa (perutnina, svinina, govedina, ...)
- tipu mesa (pečenka, kos mesa, mleto meso, mesni izdelek, ...)
- kosu mesa (bedro, prsa, svinjski kare, rib-eye, ...)
- hranjenje mesa (sveže, zamrznjeno)

Uporabniki pa bi lahko iskali svoje meso po:
- vrsti, tipu, kosu mesa
- kmetiji
- hranjenju
- ceni

To uporabnikom omogoča dobr pregled nad ponudbo in lažje iskanje specifičnega artikla. Živinorejcem pa omogoča, da imajo lepo urejene svoje izdelke in vse pod kontrolo.

### Primeri trenutnih podobnih praks

Slovenski primeri:
- Zagriz (zagriz.si)
- CoolHouse (coolhouse.si/spletna_trgovina/meso/)
- Poljanska tržnica (poljanska-trznica.si/domace-mesarstvo/sveze-meso/)
- ...

Tuji primeri:
- Good Ranchers (goodranchers.com)
- Crowd Cow (crowdcow.com)
- Grand Western Steaks (grandwesternsteaks.com)
- ...

## Sistem

### Spletna aplikacija



### Podatkovna baza



### Spletna storitev

##### API

Najino spletno aplikacijo smo že pod oddelkom **Spletna aplikacija** objavila v oblak *Microsoft Azure*. 

Center tega pod področa je bil API, ki smo ga izdelala. Za to, da sva tega razvila je bilo potrebno pripraviti okolje. Na githubu sva ustvarila nov problem (*Issue*), kjer sva predlagala ustvarjanje API-ja. Ustvarila sva tudi nov branch *api*, ki je bil uporabljen za razvoj. Ta branch je bil nekaj časa tudi uporabljen kot production, zaradi testiranja določenih stvari.

Da sva ustvarila API sva zgenerirala 2 `Controller`ja tipa `API` za entiteti `Izdelki` in `Kmetije`. 
V teh kontrolerjih sva tudi popravila njihov `route`, ki smo ga nastavila na `api/v1/[controller]`
Dodala sva tudi dokumentacijo za najin Web API. To sva ustvarila, tako da sva dodala nov paket `Swashbuckle.AspNetCore`. In nato dodala storitev `Swashbuckle` v najin `Program.cs`. Po tem je bila najina dokumentacija API-ja dostopna na najinem naslovu z dodanim `/swagger`.


### Odjemalec Android

##### Android GET

Android aplikacijo smo izdelali v okolju *Android Studio*, ki stoji na platformi *IntelliJ IDEA*. Android aplikacijo pa sva razvijala v programskem jeziku *Java*.

Aplikaciji smo prvo omogočili dostop do interneta, tako da smo ji dodali `android.permission.INTERNET`.
Uvozili smo tudi knjižnico *volley*

V tej točki smo na ekran začeli dodajati elemente. Dodala sva dva elementa. En gumb in eno tekstovno polje. Ta elementa smo pravilno poravnali in sedaj sledi programiranje njihovih funkcionalnosti. Te bomo dodali v datoteki `MainActivity.java`.

Prvo uvozimo veliko različnih stvari, nato pa ustvarimo nekaj globalni spremenljivk, ki se nanašajo na elemente, povezave in na poizvedbe.

Ustvarimo funkcijo `prikaziIzdelke()`, ki poskrbi, da ob kliku na naš gumb pridobimo podatke iz našega API-ja, ter te podatke prikažemo. Zato, da to naredimo moramo tudi popraviti funkcijo `onResponse()`, ki se nahaja v razredu `Response.Listener`, ki pa ga potrebujemo, da lahko ustvarimo objekt `jsonArrayListner`, ki ga potrebuje razred `JsonArrayRequest`, da lahko naredi poizvedbo.

Po vsem tem, nam aplikacija prikazuje izelke, ki jih pridobi preko API-ja, ki smo ga naredili.
