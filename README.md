# A Clojure stílus útmutató

## Tartalomjegyzék

  * Bevezetés 
    * Irányadó elvek
    * Megjegyzés a következetességről
    * Fordítások
  * Forráskód elrendezése és szervezése 
    * Maximális sorhossz 
    * Tabok vs szóközök
    * Törzs behúzása
    * Függvényargumentumok igazítása
    * Függvényargumentumok behúzása
    * Kötések igazítása
    * Map kulcsok igazítása
    * Sorvégek
    * Fájlok lezárása újsorral
    * Zárójelek körüli szóközök
    * Vesszők mellőzése a sorozatgyűjtemény-literálokban
    * Vesszők használata map literálokban (opcionális)
    * Záró zárójelek egy sorba gyűjtése
    * Üres sorok a legfelső szintű formák között
    * Nincs üres sor a definíciókon belül
    * Nincs záró szóköz
    * Névtérenként egy fájl
  * Névtér deklaráció 
    * Ne használjunk egyszegmenses névtereket
    * Névtérszegmensek maximális száma
    * Átfogó ns forma
    * Sortörések az ns-ben
    * A :require előnyben a :use-szal szemben
    * Az :require és :import sorok rendezése
    * Használjunk idiomatikus névtér-aliasokat
    * Recept a jó névtér-aliasokhoz
    * Következetes névtér-aliasok használata
  * Elnevezés 
    * Névtér elnevezési sémák
    * Összetett szavú névtérszegmensek
    * Függvények és változók
    * Protokollok, rekordok, structok és típusok
    * Predikátum függvények
    * Nem biztonságos függvények
    * Konverziós függvények
    * Dinamikus változók
    * Konstansok
    * Nem használt azonosítók
    * Idiomatikus nevek
  * Függvények 
    * Újsor a függvénynév után (opcionális)
    * A multimethod dispatch értékének elhelyezése
    * Egysoros függvények
    * Több aritású függvények behúzása
    * A több aritású verziók sorrendje
    * Függvény hossza
    * A függvény paraméterek számának korlátja
    * Pre- és postfeltételek
  * Idiomák 
    * Névtér dinamikus módosítása
    * Előrehivatkozások
    * declare
    * Magasabb rendű függvények
    * Változók függvényen belül
    * A clojure.core nevek árnyékolása
    * Var kötés módosítása
    * Nil punning
    * Szekvenciák vektorrá alakítása
    * Logikai értékké alakítás
    * when vs if
    * if-let
    * when-let
    * if-not
    * when-not
    * when-not vs if-not
    * not=
    * printf
    * Rugalmas összehasonlító függvények
    * Egy paraméteres függvényliterálok
    * Többparaméteres függvényliterálok
    * Ne használjunk felesleges névtelen függvényeket
    * Ne használjunk több kifejezést függvényliterálokban
    * Névtelen függvények vs complement, comp és partial
    * Threading makrók
    * Threading makrók és opcionális zárójelek
    * Threading makrók igazítása
    * A cond alapértelmezett ága
    * condp vs cond
    * case vs cond/condp
    * Rövid formák a cond-ban
    * Halmaz használata predikátumként
    * inc és dec
    * pos? és neg?
    * list* vs cons
    * Cukrozott Java-interop
    * Tömör metaadat-notáció az igaz értékű jelzőknek
    * Privát
    * Privát változó elérése
    * Metaadat körültekintő hozzárendelése
  * Adatszerkezetek 
    * Listák kerülése
    * Kulcsszavak használata hash kulcsként
    * Literál gyűjtemény szintaxis használata
    * Index alapú gyűjteményelérés kerülése
    * Kulcsszavak használata függvényként map értékek lekéréséhez
    * Gyűjtemények használata függvényként
    * Kulcsszavak használata függvényként
    * Átmeneti gyűjtemények kerülése
    * Java gyűjtemények kerülése
    * Java tömbök kerülése
  * Típusok és rekordok 
    * Rekord konstruktorok
    * Egyedi rekord konstruktorok
    * Egyedi rekord konstruktorok elnevezése
  * Mutáció 
    * Refek
    * Agentek
    * Atomok
  * Math 
    * A clojure.math függvények preferálása az interoppal szemben
  * Szövegek 
    * A clojure.string függvények preferálása interop helyett
  * Kivételek 
    * Létező kivételtípusok újrahasználata
    * A with-open preferálása a finally-vel szemben
  * Makrók 
    * Ne írjunk makrót, ha függvény is megteszi
    * Először a makró használatát írjuk meg, utána magát a makrót
    * Bontsuk szét a bonyolult makrókat
    * Makrók mint szintaktikus cukor
    * Szintaktikusan idézett formák
  * Gyakori metaadatok 
    * :added
    * :changed
    * :deprecated
    * :superseded-by
    * :see-also
    * :no-doc
    * Behúzási metaadat
  * Megjegyzések 
    * Magától értetődő kód
    * Fejléc kommentek
    * Felső szintű kommentek
    * Kódrészlet (sor) kommentek
    * Margó (sorvégi) kommentek
    * Pontosvessző utáni szóköz
    * Angol szintaxis
    * Kerüljük a fölösleges kommenteket
    * Kommentek karbantartása
    * #_ olvasómakró
    * Refaktorálj, ne kommentelj
    * Komment jelölések
      * Jelölés felül
      * Jelölő kulcsszavak
      * Jelölések behúzása
      * Jelölések aláírása és keltezése
      * Ritka margó (sorvégi) jelölések
      * TODO
      * FIXME
      * OPTIMIZE
      * HACK
      * REVIEW
      * Egyedi jelölések dokumentálása
  * Dokumentáció 
    * Dokumentációs stringek preferálása
    * Dokumentációs string összefoglaló
    * Markdown használata a dokumentációs stringekben
    * Pozícionális argumentumok dokumentálása
    * Hivatkozások dokumentálása
    * Dokumentációs stringek nyelvtana
    * Dokumentációs stringek behúzása
    * Dokumentációs string eleji/végi szóközök
    * Dokumentációs string elhelyezése a függvénynév után
  * Tesztelés 
    * Tesztkönyvtár struktúra
    * Teszt névtér elnevezése
    * Tesztek elnevezése
  * Könyvtár felépítése 
    * Könyvtár koordináták
    * Függőségek minimalizálása
    * Eszköz-függetlenség
  * Létezés 
    * Legyél funkcionális
    * Légy következetes
    * Józan ész
  * Eszközök 
    * Lint eszközök
    * Kódformázók
  * Történet
  * Inspiráció forrásai
  * Szerkesztőcsapat
  * Hozzájárulás 
    * Hogyan lehet hozzájárulni?
  * Kolofon
  * Licenc
  * Terjeszd a hírt

## Bevezetés

> A példaképek fontosak.

— Alex J. Murphy rendőrtiszt / RoboCop 

Ez a Clojure stílus útmutató bevált módszereket ajánl, hogy a valódi környezetben dolgozó Clojure programozók olyan kódot írjanak, amit más, szintén valódi környezetben dolgozó Clojure programozók karban tudnak tartani. Egy stílus útmutató akkor hasznos, ha a valós használatot tükrözi – különben hiába kiváló, ha az általa segíteni kívánt emberek már elutasították az abban foglalt elveket, nem fogják használni.

Az útmutató több, témakörök szerint rokon szabályokat tartalmazó szekcióra van bontva. Igyekeztünk feltüntetni a szabályok mögötti indoklást is (ha ez hiányzik, azt feltételeztük, hogy magától értetődő).

Nem a semmiből találtuk ki ezeket a szabályokat; nagyrészt a szerkesztők tapasztalatain, a Clojure közösség számos tagjának visszajelzésein és javaslatain, valamint több nagy tekintélyű Clojure-forrásanyagon alapulnak – például a 【0†"Clojure Programming"†www.clojurebook.com】 és a 【1†"The Joy of Clojure"†www.manning.com】 könyveken.

Semmi sincs kőbe vésve ebből. Ez az útmutató idővel változik, ahogy újabb konvenciók merülnek fel, és régiek válnak elavulttá magának a Clojure nyelvnek a változásai miatt.

**Megjegyzés**

A Clojure fejlesztői fenntartanak egy listát a 【2†könyvtárakra vonatkozó kódolási irányelvekről†clojure.org】【3†1】 is. Ezek egyike volt az ihletforrásoknak annak a dokumentumnak, amit épp olvasol.   

### Irányadó elvek

> A programokat az embereknek olvashatóra kell írni, és csak mellékesen a gépeknek futtatásra.

— Harold Abelson  
_Structure and Interpretation of Computer Programs_

Közismert, hogy a kódot sokkal gyakrabban olvassák, mint írják. Az itt megfogalmazott irányelvek célja a kód olvashatóságának javítása és az, hogy egységessé tegye a Clojure-kódok széles skáláját. Emellett az is cél, hogy a Clojure valós használatát tükrözzék, ne valamilyen önkényes ideált. Amikor választanunk kellett egy nagyon elterjedt gyakorlat és egy szubjektíve jobb alternatíva között, az elterjedt gyakorlat ajánlása mellett döntöttünk【4†2】.

Van néhány terület, ahol a Clojure közösségben nincs egyértelmű konszenzus egy adott stílust illetően (például a szemantikus behúzás vs fix behúzás, szemantikus kommentek vs egységes kommentformátum stb.). Ilyen esetekben minden népszerű stílust elismerünk, és rajtad múlik, melyiket választod és alkalmazod következetesen.

Szerencsére a Clojure Lisp, és a Lispek alapvetően egyszerűek. Bár ez az útmutató pár évvel a Clojure megjelenése után készült (az első verzió 2013 elején jelent meg), látható volt, hogy a legtöbb „vadonban” található Clojure-kód meglehetősen egységes. Ezt részben az általunk már említett egyszerűségnek tulajdonítjuk, részben pedig annak, hogy a Clojuristák már a kezdetektől fogva átvették számos bevett Lisp dialektus (pl. Common Lisp és Scheme) stílusbeli konvencióit. Ez nagymértékben megkönnyítette az útmutató elkészítését – különösen a Ruby stíluskalauz közösségi létrehozásához képest, ami igazi frusztráló kínszenvedés volt【5†Community Ruby Style Guide†rubystyle.guide】【6†3】.

A Clojure híresen az egyszerűségre és érthetőségre van optimalizálva. Szeretnénk hinni, hogy ez az útmutató segít majd neked is a lehető legegyszerűbb és legtisztább kódot írni.

### Megjegyzés a következetességről

> Az ostoba következetesség a kis elmék manója, melyet a kicsinyes államférfiak, filozófusok és papok imádnak.

— Ralph Waldo Emerson 

Egy stílus útmutató lényege a következetesség【7†4】. Fontos, hogy következetes legyél ehhez az útmutatóhoz. Még ennél is fontosabb a projekteden belüli következetesség. A legfontosabb pedig az, hogy egy adott fájlon vagy függvényen belül legyél következetes.

Ugyanakkor tudd, mikor **ne** legyél következetes — néha az útmutató ajánlásai egyszerűen nem alkalmazhatók. Ha bizonytalan vagy, használd a legjobb ítélőképességedet. Nézz meg más példákat, és döntsd el, mi néz ki a legjobban. És ne habozz kérdezni!

Különösen: ne törj visszafelé kompatibilitást csak azért, hogy megfelelj ennek az útmutatónak!

Néhány jó ok, amiért figyelmen kívül hagyhatsz egy-egy irányelvet:

  * Ha az irányelv alkalmazása még az azt megszokott olvasók számára is rontaná a kód olvashatóságát.

  * Ha azért térsz el az irányelvtől, hogy a környező kóddal konzisztens maradj (esetleg történelmi okokból) — bár ez egyúttal alkalmat adhat arra, hogy XP-stílusban rendbe tedd más rendetlenségét.

  * Ha a szóban forgó kód megelőzi az irányelv bevezetését, és egyébként nem indokolt módosítani azt.

  * Ha a kódnak korábbi Clojure verziókkal is kompatibilisnek kell maradnia, amelyek nem támogatják az útmutató által javasolt funkcionalitást.

### Fordítások

Az útmutató elérhető az alábbi nyelveken is:

  * 【8†Kínai†github.com】

  * 【9†Olasz†github.com】 (Folyamatban)

  * 【10†Japán†github.com】

  * 【11†Koreai†github.com】

  * 【12†Portugál†github.com】 (Folyamatban)

  * 【13†Orosz†github.com】

  * 【14†Spanyol†github.com】

  * 【15†Török†github.com】

**Megjegyzés**

Ezeket a fordításokat nem a hivatalos szerkesztőcsapat gondozza, így minőségük és teljességük változó lehet. A fordított verziók gyakran le vannak maradva az eredeti angol verzióhoz képest.   

## Forráskód elrendezése és szervezése

> Majdnem mindenki meg van győződve arról, hogy minden stílus csúnya és olvashatatlan, kivéve a sajátját. Ha elhagyjuk a „kivéve a sajátját” részt, valószínűleg igazuk van…​

— Jerry Coffin (a behúzásról) 

### Maximális sorhossz 

Lehetőleg kerüljük, hogy a sorok hossza meghaladja a 80 karaktert.

**Miért ragaszkodjunk a 80 karakteres sorhosszhoz a modern széles képernyős kijelzők korában?**

Manapság sokan úgy érzik, hogy a 80 karakteres sorhossz korlátja csak a múlt maradványa, és ma már nincs sok értelme. Elvégre a modern kijelzők könnyedén meg tudnak jeleníteni 200+ karaktert egy sorban. Mégis, van néhány fontos előnye annak, ha ragaszkodunk a rövidebb kódsorokhoz.

Először is – számos tanulmány kimutatta, hogy az emberek sokkal gyorsabban olvasnak függőlegesen, és a túl hosszú szövegsorok akadályozzák az olvasást. Ahogy korábban említettük, ennek az útmutatónak az egyik vezérelve, hogy a kódot emberi fogyasztásra optimalizáljuk.

Továbbá, ha korlátozzuk a szükséges szerkesztőablak szélességet, lehetővé válik, hogy több fájlt nyissunk meg egymás mellett, és jól működik az olyan kódellenőrző eszközökkel is, amelyek két verziót egymás melletti oszlopokban mutatnak.

A legtöbb eszköz alapértelmezett sortörése megtöri a kód vizuális struktúráját, és nehezebben érthetővé teszi azt. A korlátot úgy érdemes megválasztani, hogy 80 karakteres ablakméretnél ne legyen szükség sortörésre, még akkor sem, ha az eszköz a legutolsó oszlopba valamilyen jelölést tesz töréskor. Néhány webes eszköz egyáltalán nem kínál dinamikus sortörést.

Néhány csapat határozottan előnyben részesíti a hosszabb sorokat. Ha egy kódot kizárólag vagy elsősorban egy olyan csapat tart karban, amely meg tud egyezni ebben a kérdésben, megengedhető a sorhossz-limit növelése akár 100 karakterre, vagy legfeljebb 120 karakterig. Kérjük, próbálj meg ellenállni a kísértésnek, hogy 120 karakternél is tovább menj.

### Tabok vs szóközök

Behúzáshoz szóközöket használjunk. Ne használjunk tabulátor karaktereket.

### Törzs behúzása

Használjunk 2 szóközt a törzsblokkok behúzására azoknál a formáknál, amelyek törzset tartalmaznak. Ide tartozik minden `def` forma, minden speciális forma és makró, ami lokális kötéseket vezet be (pl. `loop`, `let`, `when-let`), valamint sok más makró, mint a `when`, `cond`, `as->`, `cond->`, `case`, `with-*` stb.

```clojure
;; jó
(when something
  (something-else))

(with-out-str
  (println "Hello, ")
  (println "world!"))

;; rossz – négy szóköz
(when something
    (something-else))

;; rossz – egy szóköz
(with-out-str
 (println "Hello, ")
 (println "world!"))
```

### Függvényargumentumok igazítása

Igazítsuk függőlegesen a több sorba törő függvény- (vagy makró-) hívások argumentumait.

```clojure
;; jó
(filter even?
        (range 1 10))

;; rossz – az argumentum a függvénynév alá van igazítva (egy szóköz behúzás)
(filter even?
 (range 1 10))

;; rossz – két szóköz behúzás
(filter even?
  (range 1 10))
```

Az irányelv mögötti ok egyszerű – az argumentumokat könnyebb feldolgozni az emberi agynak, ha kiugranak és együtt vannak rendezve.

### Függvényargumentumok behúzása

**Megjegyzés**

Általában tartsuk magunkat a fenti formázási szabályhoz, hacsak a rendelkezésre álló vízszintes hely korlátja ezt felül nem írja.   

Használjunk egyetlen szóköznyi behúzást a függvény- (vagy makró-) hívások argumentumainak, ha egy sorban sincs argumentum a függvénynév mellett.

```clojure
;; jó
(filter
 even?
 (range 1 10))

(or
 ala
 bala
 portokala)

;; rossz – két szóköz behúzás
(filter
  even?
  (range 1 10))

(or
  ala
  bala
  portokala)
```

Lehet, hogy furcsa különszabálynak tűnik ez azoknak, akik nem ismerik a Lisp hátteret, de a mögöttes logika egyszerű. A függvényhívások valójában listaliterek, és amikor több sorra tagolódnak, általában ugyanúgy vannak igazítva, mint bármely más gyűjteménytípus literáljai:

```clojure
;; lista literál
(1
 2
 3)

;; vektor literál
[1
 2
 3]

;; halmaz literál
#{1
  2
  3}
```

Elismerjük, hogy a listaliterek nem túl gyakoriak Clojure-ben, ezért érthető, hogy sokak számára a lista csupán a hívás szintaxisát jelenti.

Mellékes haszonként a fenti behúzásnál az argumentumok is igazítva maradnak – történetesen egybeesnek a függvénynévvel is.

**Szemantikus behúzás vs fix behúzás**

Az az irányelv, hogy a törzzsel rendelkező makrók behúzása eltérjen minden más makró és függvény behúzásától, összefoglaló nevén „szemantikus behúzás”. Egyszerűen fogalmazva ez azt jelenti, hogy a kódot eltérően húzzuk be aszerint, hogy a behúzás utaljon a kód jelentésére.

Ennek a megközelítésnek az a hátránya, hogy okosabb formázó eszközöket kíván. Vagy fel kell dolgozniuk a `macro` arglistáit és feltételezni, hogy az emberek konzisztensen nevezték el a paramétereiket, vagy pedig használniuk kell extra behúzási metaadatot.

A Clojure közösségben néhányan vitatják, hogy megéri-e ez, és inkább azt javasolják, hogy mindent egyszerűen ugyanúgy húzzunk be. Íme néhány példa:

```clojure
;;; Fix behúzás
;;
;; makrók
(when something
  (something-else))

(with-out-str
  (println "Hello, ")
  (println "world!"))

;; két soros függvényhívás
(filter even?
  (range 1 10))

;; három soros függvényhívás
(filter
  even?
  (range 1 10))
```

Ez a javaslat kétségkívül teret nyert a közösségben, de szembemegy a Lisp hagyományok jelentős részével, és ellentmond az útmutató egyik fő céljának is – nevezetesen annak, hogy a kódot emberi fogyasztásra optimalizáljuk.

Van egy kivétel a fix behúzás szabály alól – az adatlisták (amelyek nem függvényhívások):

```clojure
;;; Fix behúzás
;;
;; list literálok
;; még mindig így csináljuk
(1
 2
 3
 4
 5
 6)

;; és így
(1 2 3
 4 5 6)

;; ahelyett, hogy
(1 2 3
   4 5 6)

;; vagy
(1
   2
   3
   4
   5
   6)
```

Ez biztosítja, hogy a listák formázása konzisztens maradjon a többi gyűjteménytípus megszokott behúzásával.

### Kötések igazítása

Igazítsuk függőlegesen a `let` (és `let`-szerű) kötéseket.

```clojure
;; jó
(let [thing1 "some stuff"
      thing2 "other stuff"]
  (foo thing1 thing2))

;; rossz
(let [thing1 "some stuff"
  thing2 "other stuff"]
  (foo thing1 thing2))
```

### Map kulcsok igazítása

Igazítsuk függőlegesen a map kulcsait.

```clojure
;; jó
{:thing1 thing1
 :thing2 thing2}

;; rossz
{:thing1 thing1
:thing2 thing2}

;; rossz
{:thing1 thing1
      :thing2 thing2}
```

### Sorvégek

Unix-stílusú sorvégjeleket használjunk.【16†5】

**Tipp**

Ha Gitet használsz, érdemes beállítani a következő konfigurációt, hogy megvédd a projektedet attól, hogy Windows sorvégék szivárogjanak bele:

```bash
$ git config --global core.autocrlf true
```

### Fájlok lezárása újsorral

Minden fájl végét zárjuk egy újsor karakterrel.

**Tipp**

Ezt érdemes szerkesztőbeállítással automatikusan megoldani, nem manuálisan.   

### Zárójelek körüli szóközök

Ha egy nyitó zárójel (`(`, `{` vagy `[`) előtt szöveg áll, vagy egy záró zárójel (`)`, `}` vagy `]`) után szöveg következik, szóközzel válasszuk el a szöveget a zárójeltől. Ugyanakkor ne hagyjunk szóközt egy nyitó zárójel után, ha utána szöveg jön, és ne tegyünk szóközt egy szöveg után közvetlenül egy záró zárójel elé.

```clojure
;; jó
(foo (bar baz) quux)

;; rossz
(foo(bar baz)quux)
(foo ( bar baz ) quux)
```

### Vesszők mellőzése a sorozatgyűjtemény-literálokban

> A szintaktikus cukor pontosvesszőrákot okoz.

— Alan Perlis 

Ne használjunk vesszőt a sorozatszerű gyűjtemény-literálok elemei között.

```clojure
;; jó
[1 2 3]
(1 2 3)

;; rossz
[1, 2, 3]
(1, 2, 3)
```

### Vesszők használata map literálokban (opcionális)

Fontoljuk meg a vesszők és sortörések megfontolt használatát a map literálok olvashatóságának javítása érdekében.

```clojure
;; jó
{:name "Bruce Wayne" :alter-ego "Batman"}

;; jó, és talán kissé olvashatóbb
{:name "Bruce Wayne"
 :alter-ego "Batman"}

;; jó, és talán tömörebb
{:name "Bruce Wayne", :alter-ego "Batman"}
```

### Záró zárójelek egy sorba gyűjtése

Az összes záró zárójelet egyetlen sorba tegyük, ahelyett, hogy külön sorokba kerülnének.

```clojure
;; jó – egy sorban
(when something
  (something-else))

;; rossz – külön sorokban
(when something
  (something-else)
)
```

### Üres sorok a legfelső szintű formák között

Egy üres sort hagyjunk a top-level formák között.

```clojure
;; jó
(def x ...)

(defn foo ...)

;; rossz
(def x ...)
(defn foo ...)
```

```clojure
;; rossz
(def x ...)

(defn foo ...)
```

Kivételt képez az az eset, amikor egymáshoz tartozó `def` formákat csoportosítunk.

```clojure
;; jó
(def min-rows 10)
(def max-rows 20)
(def min-cols 15)
(def max-cols 30)
```

### Nincs üres sor a definíciókon belül

Ne hagyjunk üres sorokat egy függvény vagy makró definíciójának közepén. Kivételt tehetünk páronkénti konstrukciók (mint a `let` és `cond`) csoportosítására, ha azok nem férnek ki egy sorba.

```clojure
;; jó
(defn fibo-iter
  ([n] (fibo-iter 0 1 n))
  ([curr nxt n]
   (cond
     (zero? n) curr
     :else (recur nxt (+' curr nxt) (dec n)))))
```

```clojure
;; megengedhető – a sortörés a cond ágak csoportját jelzi
(defn fibo-iter
  ([n] (fibo-iter 0 1 n))
  ([curr nxt n]
   (cond
     (zero? n)
     curr

     :else
     (recur nxt (+' curr nxt) (dec n)))))
```

```clojure
;; rossz
(defn fibo-iter
  ([n] (fibo-iter 0 1 n))

  ([curr nxt n]
   (cond
     (zero? n) curr

     :else (recur nxt (+' curr nxt) (dec n)))))
```

Időnként jó ötletnek tűnhet egy-egy üres sort beszúrni itt-ott egy hosszabb függvény definícióba, de ha idáig jutottál, érdemes elgondolkodni, hogy nem végez-e túl sok feladatot az a hosszú függvény, és nem lehetne-e részekre bontani.

### Nincs záró szóköz

Kerüljük a sorvégi (felesleges) whitespace-t.

### Névtérenként egy fájl

Egy névtérhez egy fájlt és egy fájlhoz egy névteret használjunk.

```clojure
;; jó
(ns foo.bar)
```

```clojure
;; rossz
(ns foo.bar)
(ns baz.qux)
```

```clojure
;; rossz
(in-ns quux.quuz)
(in-ns quuz.corge)
```

```clojure
;; rossz
(ns foo.bar) vagy (in-ns foo.bar) több fájlban
```

## Névtér deklaráció

### Ne használjunk egyszegmenses névtereket

Kerüljük az egyszavas (egyszegmenses) névterek használatát.

```clojure
;; jó
(ns example.ns)

;; rossz
(ns example)
```

A névterek arra szolgálnak, hogy azonosítókat különítsenek el egymástól. Ha egyszegmenses névteret használsz, közvetlen konfliktusba kerülsz mindenki mással, aki szintén egyszegmenses névteret használ, így nagyobb eséllyel ütközöl más kódbázisokkal.

Gyakorlatilag ez azt jelenti, hogy könyvtárak soha ne használjanak egyszegmenses névteret, hogy elkerüljék a névütközéseket más könyvtárakkal. Persze a saját, privát alkalmazásodon belül azt csinálsz, amit akarsz.

**Tipp**

Általános gyakorlat az `domain.library-name` vagy `library-name.core` konvenció használata olyan könyvtáraknál, amelyeknek csak egy névterük van. A névterek elnevezéséről bővebben később lesz szó.   

Más【17†egyéb okok†github.com】 is vannak, amiért érdemes elkerülni az egyszegmenses névtereket, ezért alaposan gondold át, mielőtt ilyet használsz.

### Névtérszegmensek maximális száma

Kerüljük a túl hosszú névtereket (azaz a 5-nél több szegmensből álló neveket).

### Átfogó ns forma

Minden névteret egy átfogó `ns` formával kezdjünk, ami `refer`, `require` és `import` formákat tartalmaz – konvencionálisan ebben a sorrendben.

```clojure
(ns examples.ns
  (:refer-clojure :exclude [next replace remove])
  (:require [clojure.string :as s :refer [blank?]])
  (:import java.util.Date))
```

### Sortörések az ns-ben

Ha több függőség van, célszerű mindegyiket külön sorba tenni. Ez megkönnyíti a rendezést, az olvasást, és tisztább diffeket eredményez a függőségek változásainál.

```clojure
;; jobb
(ns examples.ns
  (:require
   [clojure.string :as s :refer [blank?]]
   [clojure.set :as set]
   [clojure.java.shell :as sh])
  (:import
   java.util.Date
   java.text.SimpleDateFormat
   [java.util.concurrent Executors
                         LinkedBlockingQueue]))
```

```clojure
;; jó
(ns examples.ns
  (:require [clojure.string :as s :refer [blank?]]
            [clojure.set :as set]
            [clojure.java.shell :as sh])
  (:import java.util.Date
           java.text.SimpleDateFormat
           [java.util.concurrent Executors
                                 LinkedBlockingQueue]))
```

```clojure
;; rossz
(ns examples.ns
  (:require [clojure.string :as s :refer [blank?]] [clojure.set :as set] 
            [clojure.java.shell :as sh])
  (:import java.util.Date java.text.SimpleDateFormat [java.util.concurrent 
                                                     Executors LinkedBlockingQueue]))
```

### A :require előnyben a :use-szal szemben

Az `ns` formában részesítsük előnyben a `:require :as` használatát a `:require :refer`-rel szemben, és azt a `:require :refer :all`-lal szemben. Előnyben részesítjük a `:require` használatát a `:use`-szal szemben; utóbbi formát tekintsük elavultnak új kódban.

```clojure
;; jó
(ns examples.ns
  (:require [clojure.zip :as zip]))
```

```clojure
;; jó
(ns examples.ns
  (:require [clojure.zip :refer [lefts rights]]))
```

```clojure
;; megengedhető, ha indokolt
(ns examples.ns
  (:require [clojure.zip :refer :all]))
```

```clojure
;; rossz
(ns examples.ns
  (:use clojure.zip))
```

### Az :require és :import sorok rendezése

Az `ns` formában rendezzük alfabetikusan a require-öket és importokat. Ez javítja az olvashatóságot és elkerüli a duplikációt, különösen ha nagyon hosszú a require/import lista.

```clojure
;; jó
(ns examples.ns
  (:require
   [baz.core :as baz]
   [clojure.java.shell :as sh]
   [clojure.set :as set]
   [clojure.string :as s :refer [blank?]]
   [foo.bar :as foo]))
```

```clojure
;; rossz
(ns examples.ns
  (:require
   [clojure.string :as s :refer [blank?]]
   [clojure.set :as set]
   [baz.core :as baz]
   [foo.bar :as foo]
   [clojure.java.shell :as sh]))
```

### Használjunk idiomatikus névtér-aliasokat

Számos alap Clojure névtérnek vannak bevett aliasai, amelyeket érdemes használni a projektjeidben – pl. a `clojure.string` névteret legtöbbször így importálják: `[clojure.string :as str]`.

**Megjegyzés**

Elsőre úgy tűnhet, ez elfedi a `clojure.core/str` függvényt, de valójában nem. Elfogadott, hogy a `clojure.core/str` és a `clojure.string/*` ugyanabban a névtérben `str` és `str/akármi` néven használható konfliktus nélkül.   

```clojure
;; jó
(ns ... (:require [clojure.string :as str] ...))

(str/join ...)
```

```clojure
;; kevésbé jó – legyünk idiomatikusak és használjuk `str/` alias-t
(ns ... (:require [clojure.string :as string] ...))

(string/join ...)
```

Ahogy a következő részben megjegyezzük, általában bevett szokás az aliasnak a névter utolsó szegmensét használni, ha az egyedi, különben az utolsó két szegmenst, jellemzően elhagyva a fölösleges részeket, mint a `clj` vagy `core`.

A Clojure alap és Contrib névterek közül az alábbiak rendelkeznek ilyen mintát követő idiomatikus aliasokkal:

Név tér | Idiomatikus alias  
---|---  
clojure.datafy | datafy  
clojure.edn | edn  
clojure.java.io | io  
clojure.math | math  
clojure.set | set  
clojure.walk | walk  
clojure.zip | zip  
clojure.core.async | async  
clojure.data.csv | csv  
clojure.data.xml | xml  
clojure.tools.cli | cli  

Vannak továbbá alap és Contrib névterek, amelyeknek rövidebb idiomatikus aliasaik vannak:

Névtér | Idiomatikus alias  
---|---  
clojure.java.shell | sh  
clojure.pprint | pp  
clojure.spec.alpha | s  
clojure.string | str  
clojure.core.matrix | mat  
clojure.tools.logging | log  
clojure.core.protocols | p  
clojure.core.reducers | r  

Gyakran használt közösségi könyvtárak között is soknak vannak széles körben elfogadott aliasai:

Névtér | Idiomatikus alias  
---|---  
cheshire.core | json  
clj-yaml.core | yaml  
clj-http.client | http  
hugsql.core | sql  
java-time | time  
next.jdbc | jdbc  

### Recept a jó névtér-aliasokhoz

Fentebb áttekintettünk néhány népszerű névteret és azok idiomatikus aliasait. Észrevehetted, hogy nem teljesen egységesek:

  * `clojure.string` aliasa `str`

  * `clojure.pprint` aliasa `pp`

  * `clojure.walk` aliasa `walk`

  * `clojure.spec.alpha` aliasa `s`

Nyilvánvaló, hogy ami közös bennük, az az, hogy tömörek, de még hordoznak némi jelentést (a `clojure.walk` `w` aliasa ugyan tömör lenne, de nem túl beszédes).

De mi legyen az összes többi névtérrel, aminek nincs bevett aliasa? Nos, légy következetes az aliasok képzésében, különben a közös Clojure kódbázison dolgozók könnyen össze fognak zavarodni. Íme néhány szabály, amit kövess【18†6】:

1. Az alias legyen ugyanaz, mint a névtér neve, a kiinduló részek levágásával.

    ```clojure
    (ns com.example.application
      (:require
       [clojure.java.io :as io]
       [clojure.reflect :as reflect]))
    ```

2. Hagyd meg a végéből annyit, hogy mindegyik alias egyedi legyen.

    ```clojure
    [clojure.data.xml :as data.xml]
    [clojure.xml :as xml]
    ```

**Tipp**

Igen, az aliasokban lehet pont. Éljünk ezzel, ha szükséges.   

3. Távolítsd el az aliasokból a fölösleges szavakat, mint „core” és „clj”.

    ```clojure
    [clj-time.core :as time]
    [clj-time.format :as time.format]
    ```

### Következetes névtér-aliasok használata

Egy projekten belül jó, ha következetesek a névtér-aliasok; pl. ne következetlenül használd ugyanarra a névtérre hol `str`, hol `string` aliasokat. Ha követed az előző két irányelvet, akkor ez magától teljesül, de ha saját egyedi aliasolási sémát alkalmazol, akkor is fontos, hogy a projekteden belül konzisztensen tedd.

## Elnevezés

> A programozásban az egyetlen valódi nehézség a gyorsítótárak érvénytelenítése és a dolgok elnevezése.

— Phil Karlton 

### Névtér elnevezési sémák

Névtér elnevezésekor részesítsük előnyben az alábbi két sémát:

  * `projekt.modul`

  * `szervezet.projekt.modul`

Ha a `projekt.modul` sémát követjük és a projektünknek csak egyetlen (implementációs) névtere van, akkor azt általában `projekt.core`-nak nevezzük. Kerüljük a `projekt.core` nevet minden más esetben, mivel az informatívabb nevek mindig jobb választások.

### Összetett szavú névtérszegmensek

Használjunk „lisp-case” írásmódot az összetett szavakból álló névtér-szegmensekhez (pl. `bruce.project-euler`).

**Megjegyzés**

Sok nem-Lisp programozó közösség a `lisp-case`-t `kebab-case`-nek nevezi, de mindannyian tudjuk, hogy a Lisp sokkal előbb létezett, mint a kebab.   

### Függvények és változók

Használjunk `lisp-case` írásmódot a függvény- és változóneveknél.

```clojure
;; jó
(def some-var ...)
(defn some-fun ...)

;; rossz
(def someVar ...)
(defn somefun ...)
(def some_fun ...)
```

### Protokollok, rekordok, structok és típusok

Használjunk `CapitalCase` írásmódot a protokollok, rekordok, structok és típusok neveiben. (Az olyan mozaikszavakat, mint HTTP, RFC, XML hagyjuk nagybetűvel.)

**Megjegyzés**

A `CapitalCase` ismert `UpperCamelCase`, `CapitalWords` vagy `PascalCase` néven is.    

### Predikátum függvények

A predikátum függvények (booleant visszaadó függvények) neve kérdőjellel végződjön (pl. `even?`).

```clojure
;; jó
(defn palindrome? ...)

;; rossz
(defn palindrome-p ...) ; Common Lisp stílus
(defn is-palindrome ...) ; Java stílus
```

### Nem biztonságos függvények

Azoknak a függvényeknek/makróknak a nevét, amelyek STM tranzakciókban nem biztonságosan használhatók, felkiáltójellel zárjuk (pl. `reset!`).

### Konverziós függvények

Használjunk `->`-t a `to` helyett a konverziós függvények nevében.

```clojure
;; jó
(defn f->c ...)

;; nem annyira jó
(defn f-to-c ...)
```

### Dinamikus változók

„Fülcskékkel” jelöljük azokat a változókat, amelyeket át akarunk kötni (dinamikusak).

```clojure
;; jó
(def ^:dynamic *a* 10)

;; rossz
(def ^:dynamic a 10)
```

### Konstansok

Ne használjunk speciális jelölést a konstansokhoz; mindent konstansnak tekintünk, hacsak nincs kifejezetten másképp jelezve.

```clojure
;; jó
(def max-size 10)

;; rossz
(def MAX-SIZE 10) ; Java stílus
(def +max-size+ 10) ; Common Lisp stílus, globális konstans
(def *max-size* 10) ; Common Lisp stílus, globális változó
```

**Megjegyzés**

Híres ellenpélda a `*clojure-version*`, ami szembemegy ezzel a konvencióval – ezt tekintsük történelmi furcsaságnak, és ne kövessük a példáját.   

### Nem használt azonosítók

Használjunk `_` karaktert azon destrukturálási célnevek és formális paraméternevek helyén, amelyek értékét a kód figyelmen kívül hagyja.

```clojure
;; jó
(let [[a b _ c] [1 2 3 4]]
  (println a b c))

(dotimes [_ 3]
  (println "Hello!"))
```

```clojure
;; rossz
(let [[a b c d] [1 2 3 4]]
  (println a b d))

(dotimes [i 3]
  (println "Hello!"))
```

Ugyanakkor, ha a kód megértését segíti, néha hasznos lehet kifejezetten elnevezni a nem használt paramétereket vagy a destrukturált mapeket. Ilyenkor tegyünk aláhúzást a név elé, jelezve, hogy a változó értéke nem lesz felhasználva.

```clojure
;; jó
(defn myfun1 [context _]
  (assoc context :foo "bar"))

(defn myfun2 [context {:keys [id]}]
  (assoc context :user-id id))

;; még jobb
(defn myfun1 [context _user]
  (assoc context :foo "bar"))

(defn myfun2 [context {:keys [id] :as _user}]
  (assoc context :user-id id))
```

### Idiomatikus nevek

Kövessük a `clojure.core` példáját az olyan idiomatikus nevek használatában, mint `pred` és `coll`.

  * függvényekben:

    * `f`, `g`, `h` – függvény bemenő értéke

    * `n` – egész szám (gyakran méret)

    * `index`, `i` – egész index

    * `x`, `y` – számok

    * `xs` – szekvencia

    * `m` – map (asszociatív tömb)

    * `k`, `ks` – kulcs, kulcsok

    * `v`, `vs` – érték, értékek (kulcs/érték párokban)

    * `s` – string bemenet

    * `re` – reguláris kifejezés

    * `sym` – szimbólum

    * `coll` – kollekció

    * `pred` – predikátum függvény

    * `& more` – variádikus bemenet

    * `xf` – transzducer (`xform`)

    * `ns` – namespace【19†7】

  * makrókban:

    * `expr` – kifejezés

    * `body` – makró törzse

    * `binding` – makró binding vektor

  * metódusokban (ha `defprotocol`, `deftype`, `defrecord`, `reify` stb. határozza meg őket):

    * `this` – az első paraméter neve, ami az objektumra utal – vagy alternatívaként valami, ami az objektumot jellemzi, de legyen konzisztens.

## Függvények

### Újsor a függvénynév után (opcionális)

Ha nincs docstring, elhagyhatjuk az új sort a függvénynév és az argumentumvektor között a `defn` esetén.

```clojure
;; jó
(defn foo
  [x]
  (bar x))

;; jó
(defn foo [x]
  (bar x))

;; rossz
(defn foo
  [x] (bar x))
```

### A multimethod dispatch értékének elhelyezése

A multimethod `dispatch-val` értékét tegyük ugyanarra a sorra, mint a függvény nevét.

```clojure
;; jó
(defmethod foo :bar [x] (baz x))

(defmethod foo :bar
  [x]
  (baz x))

;; rossz
(defmethod foo
  :bar
  [x]
  (baz x))

(defmethod foo
  :bar [x]
  (baz x))
```

### Egysoros függvények

Lehetőség szerint hagyjuk el az új sort az argumentumvektor és egy rövid függvény törzse között.

```clojure
;; jó
(defn foo [x]
  (bar x))

;; jó kis törzsű függvénynél
(defn foo [x] (bar x))

;; jó több aritású függvényeknél
(defn foo
  "Két aritásom van."
  ([x] (foo x 1))
  ([x y]
   (if (predicate? x)
     (bar x)
     (baz x))))

;; rossz
(defn foo
  [x] (if (predicate? x)
        (bar x)
        (baz x)))
```

### Több aritású függvények behúzása

Egy függvény több aritású definíciójában minden aritást függőlegesen, a paramétereivel egy vonalba indentáljunk.

```clojure
;; jó
(defn foo
  "Két aritásom van."
  ([x]
   (foo x 1))
  ([x y]
   (+ x y)))
```

```clojure
;; rossz – extra behúzás
(defn foo
  "Két aritásom van."
  ([x]
    (foo x 1))
  ([x y]
    (+ x y)))
```

### A több aritású verziók sorrendje

A függvény aritásait rendezd a legkevesebb paraméterestől a legtöbb felé. Gyakori esetben egy K paraméteres aritás teljesen meghatározza a függvény működését, az N < K paraméteres aritások részben alkalmazzák a K paraméteres verziót, az N > K paraméteres aritások pedig a K paraméteres verziót hívják meg többször (pl. fold-olva).

```clojure
;; jó – könnyű átlátni az n-edik aritást
(defn foo
  "Két aritásom van."
  ([x]
   (foo x 1))
  ([x y]
   (+ x y)))
```

```clojure
;; elfogadható – a további aritások a két paraméteres aritást használják
(defn foo
  "Két aritásom van."
  ([x y]
   (+ x y))
  ([x]
   (foo x 1))
  ([x y z & more]
   (reduce foo (foo x (foo y z)) more)))
```

```clojure
;; rossz – látszólag ok nélkül összekevert sorrend
(defn foo
  ([x] 1)
  ([x y z] (foo x (foo y z)))
  ([x y] (+ x y))
  ([w x y z & more] (reduce foo (foo w (foo x (foo y z))) more)))
```

### Függvény hossza

Kerüljük a 10 sornál hosszabb függvényeket. Ideális esetben a legtöbb függvény rövidebb, mint 5 sor.

### A függvény paraméterek számának korlátja

Kerüljük azokat a függvényeket, amelyeknek három-négy darabnál több pozíciós paramétere van.

### Pre- és postfeltételek

Részesítsük előnyben a függvény pre- és postfeltételeit a függvénytörzsön belüli ellenőrzésekkel szemben.

```clojure
;; jó
(defn foo [x]
  {:pre [(pos? x)]}
  (bar x))

;; rossz
(defn foo [x]
  (if (pos? x)
    (bar x)
    (throw (IllegalArgumentException. "x must be a positive number!")))
```

## Idiomák

### Névtér dinamikus módosítása

Kerüljük a névtér-manipuláló függvények (például `require` és `refer`) használatát. REPL környezeten kívül ezek teljesen szükségtelenek.

### Előrehivatkozások

Kerüljük az előre deklarált hivatkozásokat. Néha szükség van rájuk, de a gyakorlatban ritkán fordul elő.

### `declare`

Használjunk `declare`-t, ha elengedhetetlen az előrehivatkozás.

### Magasabb rendű függvények

Részesítsük előnyben a magasabb rendű függvényeket (pl. `map`) a `loop/recur` helyett.

### Változók függvényen belül

Ne definiáljunk függvényen belül globális változókat.

```clojure
;; nagyon rossz
(defn foo []
  (def x 5)
  ...)
```

### A clojure.core nevek árnyékolása

Ne árnyékoljunk `clojure.core` neveket lokális kötésekkel.

```clojure
;; rossz – a clojure.core/map teljes nevével kell hivatkozni a függvényen belül
(defn foo [map]
  ...)
```

### Var kötés módosítása

Használjunk `alter-var-root`-ot `def` helyett egy var értékének megváltoztatására.

```clojure
;; jó
(def thing 1) ; thing értéke most 1
; csinálunk valamit thing-gel
(alter-var-root #'thing (constantly nil)) ; thing értéke most nil

;; rossz
(def thing 1)
; csinálunk valamit thing-gel
(def thing nil)
; thing értéke most nil
```

### Nil punning

Használjuk a `seq`-et mint terminálási feltételt annak tesztelésére, hogy egy szekvencia üres-e (ezt a technikát néha nil punningnak hívják).

```clojure
;; jó
(defn print-seq [s]
  (when (seq s)
    (prn (first s))
    (recur (rest s))))

;; rossz
(defn print-seq [s]
  (when-not (empty? s)
    (prn (first s))
    (recur (rest s))))
```

### Szekvenciák vektorrá alakítása

Ha egy szekvenciát vektorrá kell alakítani, inkább `vec`-et használjunk `into` helyett.

```clojure
;; jó
(vec some-seq)

;; rossz
(into [] some-seq)
```

### Logikai értékké alakítás

Ha valamit valódi boolean értékké (`true` vagy `false`) kell konvertálni, használjuk a `boolean` függvényt.

```clojure
;; jó
(boolean (foo bar))

;; rossz
(if (foo bar) true false)
```

**Megjegyzés**

Ne feledd, hogy Clojure-ban csak a `false` és a `nil` „hamisak”. Minden más értéke `true` lesz, amikor a `boolean` függvénynek adod.   

Ritkán van szükség tényleges boolean értékre Clojure-ban, de hasznos tudni, hogyan érhetjük el, ha mégis kell.

### `when` vs `if`

Használjunk `when`-t az `if` helyett, ha csak a feltétel igaz ágát kezeljük, például `(if feltétel (valami…​))` vagy `(if …​ (do …​))` esetén.

```clojure
;; jó
(when pred
  (foo)
  (bar))

;; rossz
(if pred
  (do
    (foo)
    (bar)))
```

### `if-let`

Használjunk `if-let`-et `let` + `if` helyett.

```clojure
;; jó
(if-let [result (foo x)]
  (something-with result)
  (something-else))

;; rossz
(let [result (foo x)]
  (if result
    (something-with result)
    (something-else)))
```

### `when-let`

Használjunk `when-let`-et `let` + `when` helyett.

```clojure
;; jó
(when-let [result (foo x)]
  (do-something-with result)
  (do-something-more-with result))

;; rossz
(let [result (foo x)]
  (when result
    (do-something-with result)
    (do-something-more-with result)))
```

### `if-not`

Használjunk `if-not`-ot `(if (not …​) …​)` helyett.

```clojure
;; jó
(if-not pred
  (foo))

;; rossz
(if (not pred)
  (foo))
```

### `when-not`

Használjunk `when-not`-ot `(when (not …​) …​)` helyett.

```clojure
;; jó
(when-not pred
  (foo)
  (bar))

;; rossz
(when (not pred)
  (foo)
  (bar))
```

### `when-not` vs `if-not`

Használjunk `when-not`-ot `(if-not …​ (do …​))` helyett.

```clojure
;; jó
(when-not pred
  (foo)
  (bar))

;; rossz
(if-not pred
  (do
    (foo)
    (bar)))
```

### `not=`

Használjunk `not=`-et `(not (= …​))` helyett.

```clojure
;; jó
(not= foo bar)

;; rossz
(not (= foo bar))
```

### `printf`

Részesítsük előnyben a `printf` használatát a `(print (format …​))` helyett.

```clojure
;; jó
(printf "Hello, %s!\n" name)

;; oké
(println (format "Hello, %s!" name))
```

### Rugalmas összehasonlító függvények

Összehasonlításoknál használjuk ki, hogy a Clojure `<`, `>` stb. függvényei tetszőleges számú argumentumot elfogadnak.

```clojure
;; jó
(< 5 x 10)

;; rossz
(and (> x 5) (< x 10))
```

### Egy paraméteres függvényliterálok

Egyparaméteres függvényliterálokban a `%` használata ajánlott a `%1` helyett.

```clojure
;; jó
#(Math/round %)

;; rossz
#(Math/round %1)
```

### Többparaméteres függvényliterálok

Többparaméteres függvényliterálokban a `%` helyett a `%1` használata ajánlott.

```clojure
;; jó
#(Math/pow %1 %2)

;; rossz
#(Math/pow % %2)
```

### Ne használjunk felesleges névtelen függvényeket

Ne burkoljunk függvényeket névtelen függvényekbe, ha nincs rá szükség.

```clojure
;; jó
(filter even? (range 1 10))

;; rossz
(filter #(even? %) (range 1 10))
```

### Ne használjunk több kifejezést függvényliterálokban

Ne használjunk függvényliterálokat, ha a függvény törzse egynél több formából áll.

```clojure
;; jó
(fn [x]
  (println x)
  (* x 2))

;; rossz (ilyenkor explicit do formára lenne szükség)
#(do (println %)
     (* % 2))
```

### Névtelen függvények vs `complement`, `comp` és `partial`

Részesítsük előnyben a névtelen függvényeket a `complement`, `comp` és `partial` helyett, mivel ez a legtöbbször egyszerűbb kódhoz vezet【20†8】.

#### `complement`

```clojure
;; jó
(filter #(not (some-pred? %)) coll)

;; elmegy
(filter (complement some-pred?) coll)
```

#### `comp`

*Tegyük fel, hogy `(:require [clojure.string :as str])`...*

```clojure
;; jó
(map #(str/capitalize (str/trim %)) ["top " " test "])

;; elmegy
(map (comp str/capitalize str/trim) ["top " " test "])
```

A `comp` nagyon hasznos transzducer láncok összefűzésére.

```clojure
;; jó
(def xf
  (comp
    (filter odd?)
    (map inc)
    (take 5)))
```

#### `partial`

```clojure
;; jó
(map #(+ 5 %) (range 1 10))

;; elmegy
(map (partial + 5) (range 1 10))
```

### Threading makrók

Részesítsük előnyben a `->` (thread-first) és `->>` (thread-last) makrók használatát a mélyen egymásba ágyazott kifejezésekkel szemben.

```clojure
;; jó
(-> [1 2 3]
    reverse
    (conj 4)
    prn)

;; kevésbé jó
(prn (conj (reverse [1 2 3])
           4))
```

```clojure
;; jó
(->> (range 1 10)
     (filter even?)
     (map (partial * 2)))

;; kevésbé jó
(map (partial * 2)
     (filter even? (range 1 10)))
```

### Threading makrók és opcionális zárójelek

Nem kötelező zárójeleket tenni a threading makrókban olyan függvények köré, amelyeknek nincs argumentuma, ezért csak akkor tegyük ki őket, ha szükséges.

```clojure
;; jó
(-> x fizz :foo first frob)

;; rossz – a zárójelek feleslegesek, csak bezavarják a képet
(-> x (fizz) (:foo) (first) (frob))

;; jó – ha van argumentum, szükséges a zárójel
(-> x
    (fizz a b)
    :foo
    first
    (frob x y))
```

### Threading makrók igazítása

A threading makrók `->` (thread-first) és `->>` (thread-last) argumentumait igazítsuk egymás alá.

```clojure
;; jó
(->> (range)
     (filter even?)
     (take 5))

;; rossz
(->> (range)
  (filter even?)
  (take 5))
```

### A cond alapértelmezett ága

Használjunk `:else` kulcsszót a `cond` catch-all (minden más eset) feltételeként.

```clojure
;; jó
(cond
  (neg? n) "negatív"
  (pos? n) "pozitív"
  :else "zero")

;; rossz
(cond
  (neg? n) "negatív"
  (pos? n) "pozitív"
  true "zero")
```

### `condp` vs `cond`

Részesítsük előnyben a `condp` használatát a `cond` helyett, ha az összehasonlító predikátum és kifejezés nem változik.

```clojure
;; jó
(cond
  (= x 10) :ten
  (= x 20) :twenty
  (= x 30) :thirty
  :else :dunno)

;; sokkal jobb
(condp = x
  10 :ten
  20 :twenty
  30 :thirty
  :dunno)
```

### `case` vs `cond`/`condp`

Ha a vizsgált kifejezések fordítási időben konstansok, részesítsük előnyben a `case` használatát a `cond` vagy `condp` helyett.

```clojure
;; jó
(cond
  (= x 10) :ten
  (= x 20) :twenty
  (= x 30) :forty
  :else :dunno)

;; jobb
(condp = x
  10 :ten
  20 :twenty
  30 :forty
  :dunno)

;; legjobb
(case x
  10 :ten
  20 :twenty
  30 :forty
  :dunno)
```

### Rövid formák a cond-ban

Használjunk rövid formát a `cond` (és hasonló) kifejezésekben. Ha ez nem lehetséges, adjunk vizuális segítséget a páronkénti csoportosításhoz kommentekkel vagy üres sorokkal.

```clojure
;; jó
(cond
  (test1) (action1)
  (test2) (action2)
  :else   (default-action))
```

```clojure
;; elmegy
(cond
  ;; 1. teszteset
  (test1)
  (long-function-name-which-requires-a-new-line
    (complicated-sub-form
      (-> 'which-spans multiple-lines)))

  ;; 2. teszteset
  (test2)
  (another-very-long-function-name
    (yet-another-sub-form
      (-> 'which-spans multiple-lines)))

  :else
  (the-fall-through-default-case
    (which-also-spans 'multiple
                      'lines)))
```

### Halmaz használata predikátumként

Használjunk halmazt predikátumként, amikor megfelelő.

```clojure
;; jó
(remove #{1} [0 1 2 3 4 5])

;; rossz
(remove #(= % 1) [0 1 2 3 4 5])

;; jó
(count (filter #{\a \e \i \o \u} "mary had a little lamb"))

;; rossz
(count (filter #(or (= % \a)
                    (= % \e)
                    (= % \i)
                    (= % \o)
                    (= % \u))
               "mary had a little lamb"))
```

### `inc` és `dec`

Használjunk `(inc x)` és `(dec x)` formát a `(+ x 1)` és `(- x 1)` helyett.

### `pos?` és `neg?`

Használjuk a `(pos? x)`, `(neg? x)` és `(zero? x)` formákat a `(> x 0)`, `(< x 0)` és `(= x 0)` helyett.

### `list*` vs `cons`

Használjunk `list*`-t több egymásba ágyazott `cons` helyett.

```clojure
;; jó
(list* 1 2 3 [4 5])

;; rossz
(cons 1 (cons 2 (cons 3 [4 5])))
```

### Cukrozott Java-interop

Használjuk a cukrozott Java interop formákat.

```clojure
;;; objektum létrehozás
;; jó
(java.util.ArrayList. 100)

;; rossz
(new java.util.ArrayList 100)

;;; statikus metódus hívás
;; jó
(Math/pow 2 10)

;; rossz
(. Math pow 2 10)

;;; példány metódus hívás
;; jó
(.substring "hello" 1 3)

;; rossz
(. "hello" substring 1 3)

;;; statikus mező elérés
;; jó
Integer/MAX_VALUE

;; rossz
(. Integer MAX_VALUE)

;;; példány mező elérés
;; jó
(.someField some-object)

;; rossz
(. some-object someField)
```

### Tömör metaadat-notáció az igaz értékű jelzőknek

Használjuk a tömör metaadat jelölést olyan metaadathoz, amely csak kulcsszó kulcsú és `true` értékű mezőket tartalmaz.

```clojure
;; jó
(def ^:private a 5)

;; rossz
(def ^{:private true} a 5)
```

### Privát

Jelöljük a kód privát részeit.

```clojure
;; jó
(defn- private-fun [] ...)

(def ^:private private-var ...)

;; rossz
(defn private-fun [] ...) ; egyáltalán nem privát

(defn ^:private private-fun [] ...) ; túl bőbeszédű

(def private-var ...) ; egyáltalán nem privát
```

### Privát változó elérése

Egy privát var eléréséhez (pl. teszteléskor) használjuk a `@#'some.ns/var` formát.

### Metaadat körültekintő hozzárendelése

Figyeljünk oda, hogy pontosan mihez rendelünk hozzá metaadatot.

```clojure
;; a metaadatot az `a` varhoz rendeljük hozzá
(def ^:private a {})
(meta a) ;=> nil
(meta #'a) ;=> {:private true}

;; a metaadatot az üres hash-map értékhez rendeljük hozzá
(def a ^:private {})
(meta a) ;=> {:private true}
(meta #'a) ;=> nil
```

## Adatszerkezetek

> Jobb, ha 100 függvény működik egy adatszerkezeten, mint ha 10 függvény működik 10 különböző adatszerkezeten.

— Alan J. Perlis 

### Listák kerülése

Kerüljük listák használatát általános adatok tárolására (hacsak éppen listára van szükségünk).

### Kulcsszavak használata hash kulcsként

Részesítsük előnyben a kulcsszavak használatát a hash map kulcsaiként.

```clojure
;; jó
{:name "Bruce" :age 30}

;; rossz
{"name" "Bruce" "age" 30}
```

### Literál gyűjtemény szintaxis használata

Amennyiben lehet, használjunk literál szintaxist a gyűjtemények létrehozásához. Azonban halmazok definiálásakor csak akkor használjunk literál szintaxist, ha az értékek fordítási időben konstansok.

```clojure
;; jó
[1 2 3]
#{1 2 3}
(hash-set (func1) (func2)) ; értékek futásidőben meghatározva

;; rossz
(vector 1 2 3)
(hash-set 1 2 3)
#{(func1) (func2)} ; runtime exception, ha (func1) = (func2)
```

### Index alapú gyűjteményelérés kerülése

Kerüljük a gyűjtemények index alapján történő elérését, amikor csak lehet.

### Kulcsszavak használata függvényként map értékek lekéréséhez

Ha lehetséges, használjunk kulcsszó-függvényeket a mapek értékeinek lekérdezésére.

```clojure
(def m {:name "Bruce" :age 30})

;; jó
(:name m)

;; bővebb a kelleténél
(get m :name)

;; rossz – NullPointerException lehetőség
(m :name)
```

### Gyűjtemények használata függvényként

Éljünk azzal, hogy a legtöbb gyűjtemény használható függvényként az elemeire.

```clojure
;; jó
(filter #{\a \e \o \i \u} "this is a test")

;; rossz – túl csúnya, hogy leírjuk
```

### Kulcsszavak használata függvényként

Éljünk azzal, hogy a kulcsszavak függvényként használhatók egy gyűjteményen.

```clojure
((juxt :a :b) {:a "ala" :b "bala"})
```

### Átmeneti gyűjtemények kerülése

Kerüljük az átmeneti (`transient`) gyűjtemények használatát, kivéve teljesítménykritikus kódrészekben.

### Java gyűjtemények kerülése

Kerüljük a Java gyűjtemények használatát.

### Java tömbök kerülése

Kerüljük a Java tömbök használatát, kivéve interop esetén és olyan teljesítménykritikus kódban, ahol sok primitív típussal dolgozunk.

## Típusok és rekordok

### Rekord konstruktorok

Ne használjuk az interop szintaxist típus- és rekordpéldányok létrehozására. A `deftype` és `defrecord` automatikusan létrehozza a konstruktor függvényeket. Ezeket használjuk az interop szintaxis helyett, mert így egyértelmű, hogy `deftype`-ról vagy `defrecord`-ról van szó. Részletekért lásd 【21†ezt a cikket†stuartsierra.com】.

```clojure
(defrecord Foo [a b])
(deftype Bar [a b])

;; jó
(->Foo 1 2)
(map->Foo {:b 4 :a 3})
(->Bar 1 2)

;; rossz
(Foo. 1 2)
(Bar. 1 2)
```

Megjegyzés: a `deftype` nem hoz létre `map->Type` konstruktort. Ilyen csak a rekordokhoz jár.

### Egyedi rekord konstruktorok

Adjunk hozzá egyedi típus-/rekord-konstruktorokat, ha szükséges (pl. hogy ellenőrizzük az értékeket rekord létrehozáskor). Részletekért lásd 【21†ezt a cikket†stuartsierra.com】.

```clojure
(defrecord Customer [id name phone email])

(defn make-customer
  "Creates a new customer record."
  [{:keys [name phone email]}]
  {:pre [(string? name)
         (valid-phone? phone)
         (valid-email? email)]}
  (->Customer (next-id) name phone email))
```

Nyugodtan alkalmazzunk tetszőleges elnevezési konvenciót vagy struktúrát az ilyen egyedi konstruktorokra.

### Egyedi rekord konstruktorok elnevezése

Ne definiáljuk felül az automatikusan generált típus-/rekord-konstruktor függvényeket. Az emberek elvárják, hogy ezek bizonyos módon működjenek, és ennek megváltoztatása sérti a legkisebb meglepetés elvét. Részletekért lásd 【21†ezt a cikket†stuartsierra.com】.

```clojure
(defrecord Foo [num])

;; jó
(defn make-foo
  [num]
  {:pre [(pos? num)]}
  (->Foo num))

;; rossz
(defn ->Foo
  [num]
  {:pre [(pos? num)]}
  (Foo. num))
```

## Mutáció

### Refek

#### `io!` makró

Fontoljuk meg, hogy minden I/O műveletet az `io!` makróba csomagoljunk, hogy elkerüljük a kellemetlen meglepetéseket, ha véletlenül tranzakcióban hívnánk ilyen kódot.

#### Kerüljük a `ref-set`-et

Kerüljük a `ref-set` használatát, amikor csak lehet.

```clojure
(def r (ref 0))

;; jó
(dosync (alter r + 5))

;; rossz
(dosync (ref-set r 5))
```

#### Kis tranzakciók

Próbáljuk a tranzakciók méretét (a bennük végzett munka mennyiségét) minél kisebben tartani.

#### Kerüljük a rövid és hosszú tranzakciók keverését ugyanazon Ref-fel

Kerüljük, hogy ugyanazon Ref-fel egyszerre rövid és hosszú tranzakciók is interakcióba lépjenek.

### Agentek

#### `send` használata agenteknél

A `send`-et csak CPU-igényes, I/O-t nem végző vagy más szálakon nem blokkoló műveletekhez használjuk.

#### `send-off` használata agenteknél

A `send-off`-ot olyan műveletekhez használjuk, amelyek blokkolhatnak, aludhatnak vagy egyéb módon lefoglalhatják a szálat.

### Atomok

#### Ne frissítsünk atomot tranzakción belül

Kerüljük atomok módosítását STM tranzakciókon belül.

#### Előnyben a `swap!` a `reset!`-tel szemben

Lehetőleg használjunk `swap!`-ot a `reset!` helyett.

```clojure
(def a (atom 0))

;; jó
(swap! a + 5)

;; kevésbé jó
(reset! a 5)
```

## Math

### A clojure.math függvények preferálása az interoppal szemben

Részesítsük előnyben a `clojure.math` névtér függvényeit a (Java) interop vagy saját megoldások helyett.

```clojure
;; jó
(clojure.math/pow 2 5)

;; elmegy
(Math/pow 2 5)
```

A JDK `java.lang.Math` csomagja számos hasznos matematikai függvényhez biztosít hozzáférést. Az 1.11 előtti Clojure verziók ezekhez interop útján fértek hozzá, de ennek voltak korlátai felfedezhetőség, primitívek teljesítménye, magasabb rendű alkalmazás és hordozhatóság terén. Az új `clojure.math` névtér wrapper függvényeket nyújt a `java.lang.Math` metódusaihoz `long` és `double` változatokkal, gyors primitív meghívással.

## Szövegek

### A clojure.string függvények preferálása interop helyett

Részesítsük előnyben a `clojure.string` névtér szövegmanipulációs függvényeit a közvetlen Java interop vagy saját megoldások helyett.

```clojure
;; jó
(clojure.string/upper-case "bruce")

;; rossz
(.toUpperCase "bruce")
```

**Megjegyzés**

Számos új függvény került a `clojure.string` névtérbe a Clojure 1.8-ban (`index-of`, `last-index-of`, `starts-with?`, `ends-with?` és `includes?`). Kerüld ezek használatát, ha régebbi Clojure-verziókat is támogatnod kell.

## Kivételek

### Létező kivételtípusok újrahasználata

Használjunk meglévő kivételtípusokat. Az idiomatikus Clojure kód – amikor kivételt dob – a szabványos kivételtípusok egyikét dobja (pl. `java.lang.IllegalArgumentException`, `java.lang.UnsupportedOperationException`, `java.lang.IllegalStateException`, `java.io.IOException`).

### A with-open preferálása a finally-vel szemben

Részesítsük előnyben a `with-open` használatát a `finally` helyett.

## Makrók

### Ne írjunk makrót, ha függvény is megteszi

Ne írjunk makrót, ha egy függvény is megfelelő lenne.

### Először a makró használatát írjuk meg, utána magát a makrót

Először készítsünk egy példát arra, hogyan szeretnénk használni a makrót, és csak utána írjuk meg magát a makrót.

### Bontsuk szét a bonyolult makrókat

A bonyolult makrókat lehetőség szerint bontsuk kisebb függvényekre.

### Makrók mint szintaktikus cukor

Egy makró általában csak szintaktikus cukrot biztosítson, a lényegi munka pedig egy hétköznapi függvényben történjen. Ezzel javítjuk a kompozíthatóságot.

### Szintaktikusan idézett formák

Részesítsük előnyben a szintaxis szerint idézett formákat a listák kézi összefűzése helyett.

## Gyakori metaadatok

Ebben a szakaszban áttekintjük a névterekhez és változókhoz kapcsolódó gyakori metaadatokat, amelyeket a Clojure fejlesztőeszközök ki tudnak használni.

### :added

A nyilvános API egy elemének bevezetési verzióját leggyakrabban az `:added` metaadattal dokumentáljuk.

```clojure
(def ^{:added "0.5"} foo
  42)

(ns foo.bar
  "Egy nagyon hasznos névtér."
  {:added "0.8"})
```

```clojure
(defn ^{:added "0.5"} foo
  (bar))
```

**Tipp**

Ha SemVer-t követsz, érdemes elhagyni a patch verziót. Ez azt jelenti, hogy pl. `0.5`-öt használj `0.5.0` helyett. Ez minden verzióhoz kötődő metaadatra vonatkozik.   

### :changed

A nyilvános API egy elemének megváltoztatását leggyakrabban `:changed` metaadattal dokumentáljuk. Ez a metaadat csak varokra értelmes, és ritkán kellene használni, hiszen a publikus API viselkedésének megváltoztatása általában rossz ötlet.

Ha mégis megteszed, a legjobb egyértelművé tenni a felhasználók számára.

```clojure
;; verzióval jelölve
(def ^{:added "0.5"
       :changed "0.6"} foo
  43)
```

### :deprecated

A publikus API-k elavulttá nyilvánításának leggyakoribb módja a `:deprecated` metaadat használata. Általában értékként annak a verziónak a számát adjuk meg, amelyben az elem elavulttá vált verziózott szoftverek (pl. könyvtárak) esetén, vagy egyszerűen `true` értéket verziót nem követő szoftvereknél (pl. egy webalkalmazás).

```clojure
;;; jó
;;
;; verzióval jelölve
(def ^{:deprecated "0.5"} foo
  "Használd helyette a `bar` függvényt."
  42)

(ns foo.bar
  "Elavult névtér."
  {:deprecated "0.8"})

(defn ^{:deprecated "0.5"} foo
  (bar))

;; verzió nélkül
(defn ^:deprecated foo
  (bar))
```

```clojure
;;; rossz
;;
;; a docstring használata az elavultság jelzésére
(def foo
  "ELAVULT: Használd helyette a `bar`-t."
  42)

(ns foo.bar
  "ELAVULT: Egy elavult névtér.")
```

### :superseded-by

Gyakran a `:deprecated`-ot kombináljuk a `:superseded-by` metaadattal, hiszen általában van egy újabb API, ami felváltja a régit.

Általában varok esetében nem teljesen minősített nevet használunk, ha a kiváltó új elem ugyanabban a névtérben van, egyébként teljesen minősített nevet.

```clojure
;; verzióval jelölve
(def ^{:deprecated "0.5"
       :superseded-by "bar"} foo
  "Használd helyette a `bar` függvényt."
  42)
```

```clojure
(ns foo.bar
  "Elavult névtér."
  {:deprecated "0.8"
   :superseded-by "foo.baz"})
```

```clojure
(defn ^{:deprecated "0.5"
        :superseded-by "bar"} foo
  (bar))

;; verzió nélkül
(defn ^{:deprecated true
        :superseded-by "bar"} foo
  (bar))
```

**Tipp**

Érdemes megfontolni a `:supersedes` metaadat hozzáadását az újabb API-khoz – ez lényegében a `:superseded-by` inverze.   

### :see-also

Időnként érdemes rámutatni kapcsolódó varokra/névterekre, amelyek a könyvtárad felhasználói számára érdekesek lehetnek. Ennek leggyakoribb módja a `:see-also` metaadat, amely egy vektorban sorolja fel a kapcsolódó elemeket. Ha varokról van szó – azonos névtéren belüli elemeknél nem szükséges a teljes név.

```clojure
;; ugyanazon névtérbeli varokra hivatkozik
(def ^{:see-also ["bar" "baz"]} foo
  "Egy nagyon hasznos var."
  42)

;; más névtérbeli varokra hivatkozik
(defn ^{:see-also ["top.bar" "top.baz"]} foo
  (bar))
```

**Megjegyzés**

Számos Clojure eszköz a docstringből is megpróbál kinyerni hivatkozásokat más varokra, de sokkal egyszerűbb és egyértelműbb a `:see-also` metaadat használata erre a célra.   

### :no-doc

Az olyan dokumentációs eszközök, mint 【22†Codox†github.com】 vagy 【23†cljdoc†github.com】 felismerik a `:no-doc` metaadatot. Ha egy var vagy névtér `:no-doc` metaadatot kap, az jelzi ezeknek az eszközöknek, hogy hagyják ki az API dokumentációból.

Egy teljes névtér kihagyása az API dokumentációból:

```clojure
(ns ^:no-doc my-library.impl
  "Belső megvalósítási részletek")

...
```

Egy dokumentált névtéren belüli varok kihagyása:

```clojure
(ns my-library.api)

;; a privát függvények nincsenek dokumentálva
(defn- clearly-private []
  ...)

;; ahogy azok a publikus függvények sem, amelyek :no-doc metaadatot kapnak
(defn ^:no-doc shared-helper []
  ...)

;; ez a függvény dokumentálva lesz
```

Ez utóbbi komment utolsó sora valószínűleg a dokumentált függvény illusztrációja, de most nincs tartalom utána, mert csak egy példát mutatott.

**Megjegyzés**: Az útmutató aszerint hagyja abba itt a kódblokkot és magyarázatot, a dokumentált függvény példáját valószínűleg a `shared-helper` utáni sor kommentje jelzi, hogy "ez a függvény dokumentálva lesz". Ez a magyarázat véget ért a példával.

## Megjegyzések

> A jó kód a saját legjobb dokumentációja. Mielőtt kommentet írsz, kérdezd meg magadtól: "Hogyan javíthatnám a kódot, hogy erre a kommentre ne is legyen szükség?" Javítsd a kódot, majd dokumentáld, hogy még egyértelműbb legyen.

— Steve McConnell 

### Magától értetődő kód

Törekedj arra, hogy a kódod minél inkább magától értetődő legyen. Ha ez nem sikerül, kövesd e szekció többi irányelvét.

### Fejléc kommentek

Írjunk szakaszoló fejléckommenteket legalább négy pontosvesszővel. Ezek jellemzően kódrészletek főbb szekcióit választják el vagy fontos gondolatokat írnak le. Gyakran egy szakaszkommentet több felső szintű komment követ.

```clojure
;;;; Szekció komment/Fejléc

;;; Foo...
;;; Bar...
;;; Baz...
```

### Felső szintű kommentek

Három pontosvesszővel írjunk top-level (mindentől független) kommenteket.

```clojure
;;; Én egy felső szintű komment vagyok.
;;; Egy definíción kívül helyezkedem el.

(defn foo [])
```

**Megjegyzés**

Bár a klasszikus Lisp hagyomány `;;;`-t használ a felső szintű kommentekhez, sok „vadonbeli” Clojure kódban `;;`-t vagy akár csak `;`-t láthatsz ugyanerre a célra.   

### Kódrészlet (sor) kommentek

Egy adott kódrészlethez tartozó kommentet az adott kód elé és azzal egy vonalba igazítva írjunk, két pontosvesszővel.

```clojure
(defn foo [x]
  ;; Én egy sor/kódrészlet komment vagyok.
  x)
```

**Megjegyzés**

Bár a klasszikus Lisp hagyomány `;;`-t diktál a sor-kommentekhez, sok „vadonbeli” Clojure kódban csak `;`-t használnak.   

### Margó (sorvégi) kommentek

A sorvégi kommenteket egy pontosvesszővel írjuk.

```clojure
(defn foo [x]
  x ; Én egy sor/kódrészlet komment vagyok.
  )
```

Kerüljük az ilyen kommenteket, ha lógó záró zárójel(ek) alakulnának ki miattuk.

### Pontosvessző utáni szóköz

Mindig tegyünk legalább egy szóközt a pontosvessző (komment) karakter után, mielőtt a szöveg következik.

```clojure
;;;; Frob Grovel

;;; Ebben a kódrészben fontos mondanivalók vannak:
;;;   1. Foo.
;;;   2. Bar.
;;;   3. Baz.

(defn fnord [zarquon]
  ;; Ha zob, akkor veeblefitz.
  (quux zot
        mumble             ; Zibblefrotz.
        frotz))
```

### Angol szintaxis

Ha egy komment egynél több szóból áll, nagybetűvel kezdődjön és használjon írásjeleket. A mondatokat egy 【27†egy szóköz†en.wikipedia.org】 válassza el egymástól.

```clojure
;; This is a good comment.

;; this is a bad comment
```

Nyilvánvalóan a helyesírás nem a kommentek legfontosabb aspektusa, de egy kis plusz erőfeszítés jobb élményt nyújt a kommentek olvasóinak.

### Kerüljük a fölösleges kommenteket

Kerüljük a fölösleges kommenteket.

```clojure
;; rossz
(inc counter) ; növeli a counter változót egyel
```

### Kommentek karbantartása

Tartsuk karban a kommenteket. Egy elavult komment rosszabb, mint ha nem is lenne komment.

### `#_` olvasómakró

Ha egy adott formát ki kell kommentezni, inkább a `#_` olvasómakrót használjuk egy sima komment helyett.

```clojure
;; jó
(+ foo #_(bar x) delta)

;; rossz
(+ foo
   ;; (bar x)
   delta)
```

### Refaktorálj, ne kommentelj

> A jó kód olyan, mint egy jó vicc – nincs szüksége magyarázatra.

— Russ Olsen 

Kerüld, hogy rossz kódot kommenttel magyarázz. Inkább refaktoráld a kódot, hogy önmagáért beszéljen. („Tedd, vagy ne tedd. De ne próbáld.” – Yoda)

### Komment jelölések

#### Jelölés felül

A jelöléseket általában közvetlenül az érintett kódelem fölé írjuk.

```clojure
;; jó
(defn some-fun
  []
  ;; FIXME: Replace baz with the newer bar.
  (baz))

;; rossz
;; FIXME: Replace baz with the newer bar.
(defn some-fun
  []
  (baz))
```

#### Jelölő kulcsszavak

A jelölő kulcsszót kettőspont és szóköz követi, majd a problémát leíró megjegyzés.

```clojure
;; jó
(defn some-fun
  []
  ;; FIXME: Replace baz with the newer bar.
  (baz))

;; rossz – nincs kettőspont a jelölés után
(defn some-fun
  []
  ;; FIXME Replace baz with the newer bar.
  (baz))

;; rossz – nincs szóköz a kettőspont után
(defn some-fun
  []
  ;; FIXME:Replace baz with the newer bar.
  (baz))
```

#### Jelölések behúzása

Ha több sor kell a probléma leírásához, a következő sorokat annyival indokoljuk beljebb, amennyit az első sor is be volt húzva.

```clojure
;; jó
(defn some-fun
  []
  ;; FIXME: This has crashed occasionally since v1.2.3. It may
  ;;        be related to the BarBazUtil upgrade. (xz 13-1-31)
  (baz))

;; rossz
(defn some-fun
  []
  ;; FIXME: This has crashed occasionally since v1.2.3. It may
  ;; be related to the BarBazUtil upgrade. (xz 13-1-31)
  (baz))
```

#### Jelölések aláírása és keltezése

Lásd el a jelölést a monogramoddal és dátummal, hogy könnyen ellenőrizhető legyen, mennyire aktuális.

```clojure
(defn some-fun
  []
  ;; FIXME: This has crashed occasionally since v1.2.3. It may
  ;;        be related to the BarBazUtil upgrade. (xz 13-1-31)
  (baz))
```

#### Ritka margó (sorvégi) jelölések

Ha a probléma annyira nyilvánvaló, hogy bármi egyéb magyarázat redundáns lenne, a jelölést kivételesen a sor végén, külön magyarázat nélkül is hagyhatjuk. Ezt a használatot tekintsük kivételesnek, ne normának.

```clojure
(defn bar
  []
  (sleep 100)) ; OPTIMIZE
```

#### TODO

Használd a `TODO`-t olyan hiányzó funkció vagy szolgáltatás megjelölésére, amit később pótolni kell.

#### FIXME

Használd a `FIXME`-t hibás kód megjelölésére, amit ki kell javítani.

#### OPTIMIZE

Használd az `OPTIMIZE`-t lassú vagy nem hatékony kód megjelölésére, amely teljesítményproblémát okozhat.

#### HACK

Használd a `HACK`-et a "code smell" (gyanús kód) megjelölésére, ahol kérdéses megoldásokat alkalmaztunk, és később tisztábbra kell refaktorálni.

#### REVIEW

Használd a `REVIEW`-t bármi olyan megjelölésére, amit át kell nézni, hogy biztosan a kívánt módon működik-e. Például: `REVIEW: Biztos, hogy az ügyfél jelenleg így csinálja X-et?`

#### Egyedi jelölések dokumentálása

Használhatsz más egyedi kommentjelölő kulcsszavakat is, ha szükségesnek érzed, de mindenképp dokumentáld őket a projekted `README`-jében vagy hasonló helyen.

## Dokumentáció

A docstringek az elsődleges eszközei a Clojure kód dokumentálásának. Sok definíciós forma (pl. `def`, `defn`, `defmacro`, `ns`) támogatja a docstringet, és általában jó ötlet is élni velük, függetlenül attól, hogy az adott var publikus vagy privát.

Ha egy definíciós forma nem támogatja közvetlenül a docstringet, metaadatként még mindig elláthatod `:doc` kulccsal.

Ez a szekció áttekinti a Clojure kód dokumentálásának néhány gyakori konvencióját és bevált gyakorlatát.

### Dokumentációs stringek preferálása

Ha egy forma közvetlenül támogat docstringet, azt részesítsd előnyben a `:doc` metaadattal szemben:

```clojure
;; jó
(defn foo
  "Ez a függvény nem csinál sokat."
  []
  ...)

(ns foo.bar.core
  "Ez egy nagyszerű könyvtár.")

;; rossz
(defn foo
  ^{:doc "Ez a függvény nem csinál sokat."}
  []
  ...)

(ns ^{:doc "Ez egy nagyszerű könyvtár."}
  foo.bar.core)
```

### Dokumentációs string összefoglaló

Legyen a docstring első sora egy teljes, nagybetűvel kezdődő mondat, amely tömören leírja a szóban forgó var funkcióját. Így az eszközök (Clojure szerkesztők, IDE-k) könnyen meg tudják jeleníteni a docstring rövid összefoglalóját különböző helyeken.

```clojure
;; jó
(defn frobnitz
  "Ez a függvény frobnitzet hajt végre.
  Gnorwatzot fog csinálni ennek érdekében, de csak bizonyos
  körülmények között."
  []
  ...)

;; rossz
(defn frobnitz
  "Ez a függvény frobnitzet hajt végre. Gnorwatzot fog csinálni 
  ennek érdekében, de csak bizonyos körülmények között."
  []
  ...)
```

### Markdown használata a dokumentációs stringekben

Az olyan fontos eszközök, mint 【28†cljdoc†github.com】 támogatják a Markdown szintaxist a docstringekben, ezért használjuk ki ezt a lehetőséget a szépen formázott dokumentáció érdekében.

```clojure
;; jó
(defn qzuf-number
  "Kiszámítja a [Qzuf számot](https://wikipedia.org/qzuf) a `coll` számára.
  Az `opts` lehetséges kulcsai:

  | kulcs           | leírás |
  | --------------- | ------ |
  | `:finite-uni?`  | Véges univerzumot feltételez; alapértelmezés: `false` |
  | `:complex?`     | Megengedjük komplex [szám](https://hu.wikipedia.org/wiki/Komplex_szám) visszatérését; alapértelmezés: `false` |
  | `:timeout`      | Kivételt dob, ha a számítás nem fejeződik be `:timeout` milliszekundum alatt; alapértelmezés: `nil` |

  Példa:
  ```clojure
  (when (neg? (qzuf-number [1 2 3] {:finite-uni? true}))
    (throw (RuntimeException. \"Error in the Universe!\")))
  ```"
  [coll opts]
  ...)
```

### Pozícionális argumentumok dokumentálása

Dokumentáljunk minden pozícionális argumentumot, és tegyük őket backtick (`) közé, hogy a szerkesztők és IDE-k azonosítani tudják őket, és esetleg extra funkcionalitást kínálhassanak rájuk.

```clojure
;; jó
(defn watsitz
  "A Watsitz egy `frob`-ot znoottá alakít.
  Ha a `frob` negatív, a znoot dühös lesz."
  [frob]
  ...)

;; rossz
(defn watsitz
  "A Watsitz egy frobot znoottá alakít.
  Ha a frob negatív, a znoot dühös lesz."
  [frob]
  ...)
```

### Hivatkozások dokumentálása

Tegyük a docstringben előforduló var hivatkozásokat backtick közé, hogy az eszközök fel tudják ismerni őket. Ha linkelni is szeretnénk rájuk, tegyük dupla kapcsos zárójel közé `[[..]]`.

```clojure
;; jó
(defn wombat
  "Úgy viselkedik, mint a `clojure.core/identity`, kivéve amikor nem.
  Bemenetként `x` értéket vesz, és visszaadja azt. Ha kedve tartja.
  Lásd még [[kangaroo]]."
  [x]
  ...)

;; rossz
(defn wombat
  "Úgy viselkedik, mint a clojure.core/identity, kivéve amikor nem.
  Bemenetként x értéket vesz, és visszaadja azt. Ha kedve tartja.
  Lásd még kangaroo."
  [x]
  ...)
```

### Dokumentációs string nyelvtana

A docstringek jól formált magyar mondatokból álljanak. Minden mondat nagybetűvel kezdődjön, nyelvtanilag helyes legyen, és megfelelő írásjellel végződjön. A mondatokat egy szóköz válassza el.

```clojure
;; jó
(def foo
  "Minden mondatnak ponttal (vagy esetleg felkiáltójellel) kell végződnie.
  A mondat után szóköz következzen, hacsak nem a docstring végét jelenti.")

;; rossz
(def foo
  "minden mondatnak ponttal (vagy esetleg felkiáltójellel) kell végződnie.
  A mondat után szóköz következzen, hacsak nem a docstring végét jelenti.")
```

### Dokumentációs string behúzása

A több soros docstringeket két szóközzel indentáljuk.

```clojure
;; jó
(ns my.ns
  "Valójában egy névteret is lehet dokumentálni.
  Ez egy jó hely a névtér céljának és talán az általános konvencióknak a leírására. Figyeld meg, hogy a docstring behúzásának *elmulasztása* megkönnyíti az eszközöknek a helyes megjelenítést.")

;; rossz
(ns my.ns
  "Valójában egy névteret is lehet dokumentálni.
    Ez egy jó hely a névtér céljának és talán az általános konvencióknak a leírására. Figyeld meg, hogy a docstring behúzásának elmulasztása megkönnyíti az eszközöknek a helyes megjelenítést.")
```

### Dokumentációs string eleji/végi szóközök

Ne kezdjünk vagy zárjunk docstringet whitespace karakterrel.

```clojure
;; jó
(def foo
  "Nagyon király vagyok."
  42)

;; rossz
(def silly
  "    Ostobaság szóközökkel kezdeni egy docstringet.
  Ugyanolyan ostoba, mint szóközökkel befejezni.      "
  42)
```

### Dokumentációs string elhelyezése a függvénynév után

Amikor docstringet adunk – különösen egy függvényhez a fenti formában – ügyeljünk, hogy a docstring a függvénynév után kerüljön, ne az argumentumvektor után. Az utóbbi nem szintaktikailag érvénytelen, nem okoz hibát, de a string így a függvény törzsének részeként kerül értelmezésre, ahelyett, hogy a var dokumentációja lenne.

```clojure
;; jó
(defn foo
  "docstring"
  [x]
  (bar x))

;; rossz
(defn foo [x]
  "docstring"
  (bar x))
```

**Megjegyzés**

A `defprotocol` metódusainál a docstringet az argumentumvektor után helyezzük el:

```clojure
(defprotocol MyProtocol
  "MyProtocol docstring"
  (foo [this x y z]
    "foo docstring")
  (bar [this]
    "bar docstring"))
```  

## Tesztelés

### Tesztkönyvtár struktúra

Tartsuk a teszteket külön könyvtárban, tipikusan `test/yourproject/` alatt (szemben a `src/yourproject/` könyvtárral). A build eszköz feladata, hogy szükség esetén ezeket elérhetővé tegye; a legtöbb projekt sablon ezt automatikusan beállítja.

### Teszt névtér elnevezése

Nevezd el a teszt névteret `yourproject.something-test` formára; ez a fájl jellemzően a `test/yourproject/something_test.clj` (vagy `.cljc`, `.cljs`) alatt található.

### Tesztek elnevezése

Ha a `clojure.test`-et használod, a teszteket `deftest`-tel definiáld, és nevezd el őket `valami-test` alakra.

```clojure
;; jó
(deftest something-test ...)

;; rossz
(deftest something-tests ...)
(deftest test-something ...)
(deftest something ...)
```

## Könyvtár felépítése

### Könyvtár koordináták

Ha mások által is használható könyvtárakat publikálsz, kövesd a 【29†Central Repository útmutatót†central.sonatype.org】 a `groupId` és `artifactId` megválasztásához. Ez segít elkerülni a névütközéseket és elősegíti a minél szélesebb körű felhasználhatóságot. Jó példa erre a 【30†Component†github.com】 – a koordinátája `com.stuartsierra/component`.

Egy másik elterjedt megközelítés az, ha projekt- (vagy szervezet-) nevet használsz `groupId`-ként a domain helyett. Ilyen példák:

  * `cider/cider-nrepl`

  * `nrepl/nrepl`

  * `nrepl/drawbridge`

  * `clj-commons/fs`

### Függőségek minimalizálása

Kerüld a szükségtelen függőségeket. Például, ha egy háromsoros kis segédfüggvényt bemásolhatsz a projektedbe, az általában jobb, mint egy függőség bevonása, ami százával hoz be olyan varokat, amiket nem is használsz.

### Eszköz-függetlenség

A fő funkcionalitást és az integrációs pontokat külön artefaktumokba szállítsd. Így a felhasználók eszközfüggetlenül is használhatják a könyvtáradat, anélkül hogy a te kiegészítő eszközválasztásaidhoz lennének kötve. Például a 【30†Component†github.com】 a fő funkcionalitást biztosítja, míg a 【31†reloaded†github.com】 a Leiningen integrációt.

## Létezés

### Legyél funkcionális

Funkcionális stílusban programozz, a mutációt csak akkor használd, ha van értelme.

### Légy következetes

Légy következetes. Ideális esetben légy következetes ezekhez az irányelvekhez is.

### Józan ész

Használd a józan eszed.

## Eszközök

Egy stílus útmutatóval az a probléma, hogy gyakran nehéz minden irányelvre emlékezni és azokat következetesen alkalmazni. Végül is csak emberek vagyunk. Szerencsére van egy csomó eszköz, ami elvégzi helyettünk a munka nagy részét.

**Tipp**

Érdemes ezeket az eszközöket a folyamatos integráció (CI) részeként futtatni. Így biztosíthatod, hogy egy projekt összes kódja következetes legyen az általad kitűzött stílussal.   

### Lint eszközök

A Clojure közösség készített néhány lint eszközt, amelyek segíthetnek idiomatikus Clojure kódot írni:

  * 【32†kibit†github.com】 – egy statikus kódelemző Clojure-hoz, ami a 【33†core.logic†github.com】 segítségével olyan kódrészeket keres, ahol létezhet idiomatikusabb függvény vagy makró az adott minta helyett.

  * 【34†clj-kondo†github.com】 – egy linter, ami számos nem ajánlott mintát felismer és javításokat javasol rájuk, ezen stílus útmutató alapján.

### Kódformázók

Bár a legtöbb Clojure szerkesztő és IDE tudja formázni a kódot az itt leírt layout szabályok szerint, hasznosak lehetnek a parancssori kódformázó eszközök is. Clojure-hoz több ilyen is elérhető, amelyek kiválóan formázzák a kódot az útmutató javaslatai szerint:

  * 【35†cljfmt†github.com】

  * 【36†cljstyle†github.com】

  * 【37†zprint†github.com】 (ennek konfigurálását a közösségi formázási szabályokhoz 【38†itt†github.com】 ismertetik)

**Megjegyzés**

Szerkesztők terén – Emacs `clojure-mode` módja alapból pontosan az útmutatóban leírtak szerint formázza a kódot. Más szerkesztők esetleg igényelnek némi konfigurálást a hasonló eredményhez.   

## Történet

Ezt az útmutatót 2013-ban indította 【39†Bozhidar Batsov†github.com】, a 【40†hasonló projekt†rubystyle.guide】 sikerén felbuzdulva, amit a Ruby közösség számára hozott létre.

Bozhidar szenvedélyesen szerette a Clojure-t és a jó programozási stílust, és át akarta hidalni azt a rést, ami a 【2†Clojure könyvtárak kódolási irányelvei†clojure.org】 és aközött állt fenn, amit más nyelvek (pl. Java, Python, Ruby) stíluskalauzai tipikusan lefedtek. Bozhidar ma is az útmutató elsődleges szerkesztője, de egy egész szerkesztőcsapat támogatja a projektet.

Az útmutató indulása óta rengeteg visszajelzést kaptunk a kiváló nemzetközi Clojure közösség tagjaitól. Köszönjük az összes javaslatot és támogatást! Együtt egy minden Clojure fejlesztő számára hasznos forrást hozhatunk létre.

## Inspiráció forrásai

Számos ember, könyv, előadás, cikk és más stíluskalauz hatott a közösségi Clojure stílus útmutatóra. Íme néhány közülük:

  * 【41†"The Elements of Style"†en.wikipedia.org】

  * 【42†"The Elements of Programming Style"†en.wikipedia.org】

  * 【43†Python Style Guide (PEP-8)†www.python.org】

  * 【40†Community Ruby Style Guide†rubystyle.guide】

  * 【44†Google Common Lisp Style Guide†google.github.io】

  * 【45†scheme-style†community.schemewiki.org】

  * 【2†Clojure könyvtár kódolási irányelvek†clojure.org】

  * 【0†"Clojure Programming"†www.clojurebook.com】

  * 【1†"The Joy of Clojure"†www.manning.com】

  * 【46†"Elements of Clojure"†elementsofclojure.com】

  * 【47†"Clojure Applied"†pragprog.com】

  * 【48†Stuart Sierra: "Clojure Do's and Don'ts" blog sorozata†stuartsierra.com】

## Szerkesztőcsapat

A Clojure stílus útmutatót egy tapasztalt Clojure-szerkesztőkből álló csapat gondozza, amelynek célja, hogy az összes beérkező inputot (pl. visszajelzések, javaslatok) egy jobb referenciává gyúrja mindenki számára.

  * 【49†Bozhidar Batsov†metaredux.com】

  * 【50†Alex Miller†insideclojure.org】

  * 【51†Daniel Compton†danielcompton.net】

  * 【52†Sean Corfield†corfield.org】

## Hozzájárulás

Az útmutató még mindig fejlesztés alatt áll – néhány irányelvhez hiányoznak példák, más irányelveknek nincs elég szemléletes példája. Az ilyen irányelvek javítása remek (és egyszerű) módja annak, hogy segítsd a Clojure közösséget!

Idővel remélhetőleg ezek a problémák megoldódnak – egyelőre tartsd őket észben.

Az útmutatóban semmi sincs kőbe vésve. Szeretném, ha mindenkit, akit érdekel a Clojure kódolási stílusa, együtt dolgozna velem azon, hogy végül egy olyan erőforrást hozzunk létre, amely az egész Clojure közösség javára válik.

Nyugodtan nyiss hibajegyeket vagy küldj pull requesteket a fejlesztésekért. Előre is köszönjük a segítségedet!

A stílus útmutatót (és minden Clojure projektemet, mint a CIDER, nREPL, orchard stb.) anyagilag is támogathatod az alábbi platformokon:

  * 【53†GitHub Sponsors†github.com】

  * 【54†ko-fi†ko-fi.com】

  * 【55†Patreon†www.patreon.com】

  * 【56†PayPal†www.paypal.me】

### Hogyan lehet hozzájárulni?

Egyszerű, csak kövesd az alábbi hozzájárulási irányelveket:

  * 【57†Forkold†help.github.com】 a 【58†bbatsov/clojure-style-guide†github.com】 repót GitHubon.

  * Végezdd el a fejlesztést vagy hibajavítást egy külön feature branch-ben.

  * Adj egy 【59†jó leírást†tbaggery.com】 a változtatásaidhoz.

  * Push-old fel a feature branchet a GitHubra.

  * Küldj egy 【60†Pull Requestet†help.github.com】.

## Kolofon

Ez az útmutató 【61†AsciiDoc†asciidoc.org】 formátumban készült, és HTML-ként kerül publikálásra a 【62†AsciiDoctor†asciidoctor.org】 segítségével. Az útmutató HTML verziója a GitHub Pages-en van hostolva.

Eredetileg az útmutató Markdownban íródott, de 2019-ben AsciiDocra konvertálták.

## Licenc

【75†Kép: Creative Commons License†guide.clojure.style】 Jelen mű licencelve van a 【63†Creative Commons Nevezd meg! 3.0 Unported†creativecommons.org】 licenc alatt.

## Terjeszd a hírt

Egy közösség által alakított stíluskalauz mit sem ér, ha a közösség nem is tud a létezéséről. Írj róla tweetet, oszd meg barátaiddal és kollégáiddal! Minden hozzászólás, javaslat vagy vélemény egy kicsit jobbá teszi az útmutatót. Márpedig a lehető legjobb útmutatót szeretnénk, nem igaz?

* * *

【64†1】. Ezeket az irányelveket magára a Clojure-ra és a hivatalos Clojure Contrib könyvtárakra szánják.

【65†2】. Esetenként javasolhatunk alternatívákat is az olvasónak.

【66†3】. Észre fogod venni, hogy a Clojure stílus útmutató felépítésében nagyon hasonlít a Ruby stíluskalauzhoz, ami a fő ihletforrás volt. A Ruby stíluskalauz sokkal hosszabb, főleg a Ruby nyelv összetettsége miatt.

【67†4】. Ez a szakasz nagyban a Python PEP-8-on alapul.

【68†5】. *BSD/Solaris/Linux/macOS felhasználók eleve így működnek, Windows felhasználóknak viszont erre figyelniük kell.

【69†6】. Ezek az irányelvek 【70†Stuart Sierra egy blogposztján†stuartsierra.com】 alapulnak.

【71†7】. Technikailag ez árnyékolja az `ns` makrót, de nagyon valószínűtlen, hogy egy függvény törzsében szükség legyen rá.

【72†8】. Erről bővebben 【73†itt olvashatsz†ask.clojure.org】.

【74†9】. Ezt először a CIDER 0.10 vezette be.

_Last updated 2024-03-06 06:43:06 UTC_
