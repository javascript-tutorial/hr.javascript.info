# Uvod u JavaScript

Idemo vidjeti što je tako posebno oko JavaScripta, što njime možemo postići i koje druge tehnologije dobro rade s njim.

## Što je JavaScript?

*JavaScript* je isprva napravljen kako bi "napravio web-stranice živima".

Programi u ovom jeziku nazivaju se *skriptama*. One mogu biti napisane izravno u HTML-u web-stranice i pokrenute automatski pri učitavanju stranice.

Skripte su pružene i izvršene kao običan tekst. Ne trebaju posebnu pripremu niti kompilaciju da bi se pokrenule.

U tom pogledu, JavaScript je vrlo različit od jednog drugog jezika zvanog [Java](https://hr.wikipedia.org/wiki/Java_(programski_jezik))).

```smart header="Zašto se zove <u>Java</u>Script?"
Kada je JavaScript tek stvoren imao je drugo ime: "LiveScript". Međutim, u to je vrijeme Java bila vrlo popularna pa je odlučeno da bi bilo od pomoći postaviti taj novi jezik kao "mlađeg brata" Jave.

No, kako je evoluirao, JavaScript je postao sasvim neovisan jezik vlastite specifikacije zvane [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript) pa sad više nema nikakvog odnosa s Javom.
```

Danas, JavaScript nema mogućnost izvođenja samo u web pregledniku (eng. *browser*), već i na poslužitelju (eng. *server*), odnosno na bilokojem uređaju koji ima poseban program imena [JavaScript pokretač](https://en.wikipedia.org/wiki/JavaScript_engine) (eng. *JavaScript engine*).

Web preglednik ima ugrađeni pokretač koji se ponekad naziva "JavaScript virtualnim strojem" (eng. *JavaScript virtual machine*).

Različiti pokretači imaju različita "kodna imena". Na primjer:

- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- Chrome i Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- Firefox.
- ...Postoje i druga kodna imena poput "Chakra" za IE, "JavaScriptCore", "Nitro" i "SquirrelFish" za Safari, itd.

Gornji pojmovi dobri su za zapamtiti jer se koriste u developerskim člancima na internetu, a korisit će se i ovdje. Na primjer, ako "V8 podržava značajku X", onda najvjerojatnije radi u Chromeu i Operi.

```smart header="Kako rade pokretači?"
Pokretači su komplicirani, ali osnove su jednostavne.

1. Pokretač (ugrađen ako je web preglednik) čita ("parsira") skriptu.
2. Zatim pretvara ("kompajlira") skriptu u strojni jezik.
3. Onda se strojni kod izvršava, i to prilično brzo.

Pokretač primjenjuje optimizacije u svakom koraku procesa. On čak i gleda kompajliranu skriptu dok se izvršava, analizira podatke koji kroz nju prolaze pa još više optimizira strojni kod na temelju toga.
```

## Što sve može JavaScript u web pregledniku?

Moderni JavaScript je "siguran" programski jezik. Ne pruža pristup memoriji ili CPU jer je originalno napravljen za preglednike kojima to nije bilo potrebno.

JavaScriptove mogućnosti uvelike ovise o okolini u kojoj se izvršava. Na primjer, [Node.js](https://wikipedia.org/wiki/Node.js) podržava funkcije koje dopuštaju JavaScriptu da čita/piše proizvoljne datoteke, izvršava mrežne zahtjeve, itd.

JavaScript u web pregledniku može raditi sve vezano uz manipulaciju web stranicama, interakciju s korisnikom, i web poslužitelja.

Na primjer, JavaScript u web pregledniku može:

- Dodati novi HTML na stranicu, mijenjati postojeći sadržaj, mijenjati stilove,
- Reagirati na korisnikove akcije, pokretati se na pritisak miša, micanje pokazivača i pritisak znakova tipkovnice,
- Slati zahtjeve preko mreže na udaljene (eng. *remote*) poslužitelje, preuzimati i učitavati datoteke (takozvane [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) i [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) tehnologije),
- Dohvaćati i postavljati kolačiće, postavljati pitanja posjetitelju, prikazivati poruke, te
- Pamtiti podatke na klijentskoj strani ("local storage").

## Što JavaScript u web pregledniku NE može?

JavaScriptove sposobnosti u web pregledniku ograničene su za sigurnost korisnika. Cilj je zloj stranici spriječiti pristup privatnim podacima ili mogućnost oštećivanja korisnikovih podataka.

Primjeri takvih ograničenja uključuju:

- JavaScript na web-stranici ne smije čitati/pisati proizvoljne datoteke na tvrdi disk, kopirati ih ili izvoditi programe. Nema izravan pristup funkcijama operacijskog sustava.

    Moderni preglednici dopuštaju mu rad s datotekama, ali pristup je ograničen i dopušten samo ako korisnik, na primjer, "ubaci" datoteku u prozor preglednika ili ju označi kroz `<input>` oznaku.

    Postoje načini za interakciju s kamerom/mikrofonom i drugim uređajima, ali oni zahtijevaju korisnikovo eksplicitno dopuštenje. Dakle, stranica s omogućenim JavaScriptom ne smije i ne može potajice uključiti web kameru, proučavati okolinu i slati informacije [SOA-i](https://hr.wikipedia.org/wiki/Sigurnosno-obavje%C5%A1tajna_agencija).

- Različiti tabovi/prozori uglavnom ne znaju jedan za drugog. Ponekad znaju, npr. kada jedan prozor koristi JavaScript kako bi otvorio drugi. Međutim, čak i tada, JavaScript jedne stranice ne smije pristupiti drugoj ako dolaze s drugačijih mjesta (eng. *site*) (druga domena, protokol, port).

    Ovo se zove "Same Origin Policy" (politika istog izvora). Kako bi se to zaobišlo, *obje stranice* moraju pristati na razmjenu podataka i sadržavati poseban JavaScript kod koji time rukuje (eng. *handle*). Pokrit ćemo to u ovom tutorialu.

    Ovo ograničenje je, opet, za sigurnost korisnika. Stranica s `https://bilosto.hr` koju je korisnik otvorio ne smije moći pristupiti drugom tabu preglednika URL-a `https://mail.google.com` i krasti informacije odandje.
- JavaScript može jednostavno komunicirati preko mreže s poslužiteljem s kojeg je trenutna stranica došla, ali mu je sposobnost primanja podataka od drugih stranica/domena osakaćena. Iako je moguće, zahtijeva eksplicitni pristanak (izražen preko HTTP zaglavlja (eng. *headers*)) udaljene strane komunikacije. I opet, to je sigurnosno ograničenje.

![](limitations.svg)

Takva ograničenja ne postoje kada se JavaScript koristi izvan preglednika, na primjer na poslužitelju. Moderni preglednici također dopuštaju pluginove/ekstenzije koje mogu tražiti proširena dopuštenja.

## Što JavaScript čini jedinstvenim?

Postoje barem *tri* odlične stvari oko JavaScripta:

```compare
+ Potpuna integracija s HTML-om i CSS-om.
+ Jednostavne stvari rade se jednostavno.
+ Svi veliki preglednici podržavaju ga pod zadano.
```
JavaScript je jedina tehnologija web preglednika koja kombinira ove tri stvari.

I to čini JavaScript jedinstvenim; zbog toga je najrašireniji alat za stvaranje web sučelja.

Međutim, JavaScript također podržava stvaranje poslužitelja, mobilnih aplikacija, itd.

## Jezici "preko" JavaScripta

Sintaksa JavaScripta ne pristaje svačijim potrebama. Različiti ljudi žele različite značajke.

To je i očekivano jer su projekti i zahtjevi različiti za svakoga.

Tako se nedavno pojavilo obilje novih jezika koji se *transpajliraju* (eng. *transpile*) (pretvaraju) u JavaScript prije nego se pokrenu u pregledniku.

Moderni alati čine transpilaciju vrlo brzom i transparentnom pa tako čak i dopuštaju developerima kodiranje u drugom jeziku, koji automatski "ispod haube" pretvaraju u JavaScript.

Primjeri takvih jezika:

- [CoffeeScript](http://coffeescript.org/) je "sintaktički šećer" za JavaScript, a uvodi kraću sintaksu kojom omogućava pisanje čišćeg i preciznijeg koda. Obično ga vole developeri Rubyja.
- [TypeScript](http://www.typescriptlang.org/) se koncentrira na dodavanje "strogog tipiziranja podatka" za pojednostavljenje razvoja i podršku kompleksnih sustava. Razvija ga Microsoft.
- [Flow](http://flow.org/) također dodaje tipiziranje podataka, ali na drugačiji način. Razvija ga Facebook.
- [Dart](https://www.dartlang.org/) je samostalan jezik koji ima vlastiti pokretač koji se vrti u okolinama van preglednika (poput mobilnih aplikacija), ali također može biti transpajliran u JavaScript.
- [Brython](https://brython.info/) je Python-u-JavaScript transpajler koji omogućuje pisanje aplikacija u čistom Pythonu.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) je moderan, koncizan i siguran programski jezik koji može ciljati preglednik ili Node.

Postoji ih još. Naravno, čak i ako koristimo jedan od transpajlanih jezika trebamo znati JavaScript kako bismo zaista shvaćali što radimo.

## Sažetak

- JavaScript originalno stvoren kao jezik samo za web preglednike, ali sada se također koristi u raznim drugim okolinama.
- JavaScript danas ima posebnu poziciju kao najraširenije usvojen jezik web preglednika s potpunom integracijom s HTML-om i CSS-om.
- Postoje mnogi jezici koji se mogu transpajlirati u JavaScript i pružaju određene značajke. Preporučljivo je barem ih malo pogledati nakon svladavanja JavaScripta.
