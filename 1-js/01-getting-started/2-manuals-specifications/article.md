
# Priručnici i specifikacije

Ova knjiga je *tutorial*. Njezin cilj je pomoći ti postupno naučiti jezik, ali jednom kada svladaš osnove trebat ćeš druge izvore.

## Specifikacija

[ECMA-262 specifikacija](https://www.ecma-international.org/publications/standards/Ecma-262.htm) sadrži najdetaljnije, formalizirane informacije o JavaScriptu koje idu najviše u dubinu. Ona definira taj jezik.

Međutim, budući da je tako formalizirana, isprva je teška za shvatiti. No ako trebaš najpouzdaniji izvor informacija o detaljima jezika, ta specifikacija je pravi izbor, samo nije najprikladnija za svakodnevno korištenje. 

Nova verzija specifikacije izdaje se svake godine. Između tih izdanja, skica najnovije specifikacije nalazi se na <https://tc39.es/ecma262/>.

Ako želiš čitati o najnovijim značajkama "krvarećeg ruba" (eng. *bleeding edge*), uključujući onim koje su "skoro pa standard" (tzv. "stadij 3"), pogledaj prijedloge na <https://github.com/tc39/proposals>.

Također, ako razvijaš za web preglednik, postoje i druge specifikacije koje su pokrivene u [drugom dijelu](info:browser-environment) tutoriala.

## Priručnici

- **MDN (Mozilla) JavaScript Reference** je glavni priručnik s primjerima i drugim informacijama. Odličan je za pronaći detaljne informacije o pojedinim funkcijama, metodama, i sl. koje se nalaze u jeziku.

    Može se naći na <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference>.

Doduše, često je najbolje koristiti neku web tražilicu. Samo se u upitu iskoristi format "MDN [pojam]", npr. <https://google.com/search?q=MDN+parseInt> kako bi se potražila `parseInt` funkcija.

## Tablice usklađenosti

JavaScript je jezik u razvoju, dakle učestalo dobiva nove značajke.

Kako bi se vidjela podrška za njih kroz pokretače bilo u pregledniku ili van njega, postoje:

- <http://caniuse.com> - tablica podrške po svakoj značajki, npr. pregled podrške za moderne kriptografske funkcije: <http://caniuse.com/#feat=cryptography> i
- <https://kangax.github.io/compat-table> - tablica sa značajkama jezika i pokretačima koji ih ili podržavaju ili ne.

Svi su ovi izvori korisni u stvarnom razvoju aplikacija jer sadrže vrijedne informacije o detaljima jezika, podršci značajki, itd.

Bilo bi dobro zapamtiti ih (ili ovu stranicu) za slučajeve kada se javi potreba za detaljima o nekoj značajci.
