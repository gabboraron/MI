# MI

**jetson**
https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-nano/learn-ai/
https://courses.nvidia.com/courses/course-v1:DLI+C-RX-02+V1/about

**inteligens rendszerek elmélete youtube sorozat (kb 15 óra)** https://www.youtube.com/watch?v=QP0bdol-5Y0&list=PLSBcNSXgMqreVXQV0dMaVrManDyfGnWvF

**korábbi vizsgakidolgozások**
http://zyxon.github.io/pages/mi-vizsga.html vagy [cache](http://webcache.googleusercontent.com/search?q=cache:jrdH-2LKvL8J:zyxon.github.io/pages/mi-vizsga.html+&cd=1&hl=en&ct=clnk&gl=hu&client=ubuntu)

## Vissszalépéses keresés 1
> - nincs kör és mélységi korlát figyelés
> - véges körmentes gráfon terminál, ha van megoldás talál egyet

## Vissszalépéses keresés 2
### elsődleges
> nem modelfüggő, nem merít a feladattól és annak modelljétől, nem  merít a feladat ismeretiből és a modell sajátosságaiból.
### másodlagos
> modellfüggő, nem függ a feladat imsereteitől, de építa feladat modelljének általános elemére, pl lineáris input stratégia
### heurisztikus
> feladattól származik, nem rögzített megoldással, de a feladatból ismert adatokat használja

## best first
> a csúcsoknak súlya van ~ heursiztika. ezeket figyelembe véve, minidg a **legkisebb fele indul**

https://www.youtube.com/watch?v=kNIEMi9OIwA

## A algoritmus
> van költsége az élnek, ez alapján tejeszti ki az lagoritmus, a legkisebb fle indul, mint az előző, az **út költsége + a csúcs heurisztikája, ha a csúcsn átmegy az út akkor nem kell figyelembe venni** a heurisztikáját.

https://www.youtube.com/watch?v=bK3Z61A8R48

## A*
> **az út hossza a csúcsba, a csúcs heurisztikája és az addig vezető utat is figyelembe veszi**, `CSÚCS, ÚTHOSSZ, ÚTHOSSZ+HEURISZTIKA` formában. Az, hogy melyik lépésben melyikkel foyltatja attól függ, a `ÚTHOSSZ+HEURISZTIKA`tól függ, ismét a legkisebbet veszi figyelembe. Ha egy csúcsot már érintettünk, de az úthossz nagyobb mint az előző alklaommal akkor nem lép tovább, mer előnytelen. Ha eléri a célt, de a heurisztika nagyobb mint a még be nem járt úton, akkor azzal folytatjuk, és tovább keresünk.

https://www.youtube.com/watch?v=hhCT9wyfEqE

> **`A` és `A*` közti különbség:** https://cs.stackexchange.com/questions/50722/algorithm-a-vs-algorithm-a-whats-the-difference

**Mintafeladat:** feladat: [06.HF_ABA.pdf](https://github.com/gabboraron/MI-EA/blob/master/06.HF_ABA.pdf) és mintamegoldás: [ABA.pdf](https://github.com/gabboraron/MI-EA/blob/master/ABA.pdf) **első és utolsó feladata!**

## B
Bemenő számok együtteséből kimenő értékeket előáállító rendszer,kapcsolódó, tanítható egységekből áll, pl: mesterséges neuron, hálózati topológia, tanulási szabály, neuronháló.

**Mintafeladat:** feladat: [06.HF_ABA.pdf](https://github.com/gabboraron/MI-EA/blob/master/06.HF_ABA.pdf) és mintamegoldás: [ABA.pdf](https://github.com/gabboraron/MI-EA/blob/master/ABA.pdf) **középső része!**

## minimax
> felváltva keres minimumot és maximumot a gyerekek között. **mindig `MAX` az első!!**

https://www.youtube.com/watch?v=vSXF-beEdko

## negamax
> felváltva keres maximumot és negáltak maximumát. **mindig `NEGMAX` az első!!**

https://www.youtube.com/watch?v=q4B72LU0ERI

**Mintafeladat:** feladat: [08.HF_game.pdf](https://github.com/gabboraron/MI-EA/blob/master/08.HF_game.pdf)és megoldás: [NegaMax.jpg](https://github.com/gabboraron/MI-EA/blob/master/NegaMax.jpg)

## átlagoló kiértékelés
> két érték adott `n` és `m`, ez egyébként egy `minimax` fa ahol a `MAX` szinteken `n` a `MIN` szinteken `m` darab elemet átlagolunk, értlemeszerűen a maxon az első m darab legnagyobb, a minen az első n darab legkisebb átlaga kell.

https://www.youtube.com/watch?v=f9LcjuwWcdw

## alfa béta vágás
> nem veszi figyelembe az egyébként előnytelen ágakat
>
> pl: ha adott szintre a minimum kell és a előző maximumot keres akkor ha a az egyk ág klegkisebb értéke is nagyobb mint a a másik ág maximuma úgy azon nm kell kisázmolni a maximumot, hiszen a végén úgyis csak a kisebb érdekel a következő szintre.

https://www.youtube.com/watch?v=80wILJOXFog
> gyakorlóprogram alfa-béta vágásra: http://inst.eecs.berkeley.edu/~cs61b/fa14/ta-materials/apps/ab_tree_practice/
**Mintafeladat:**: feladat: [08.HF_game.pdf](https://github.com/gabboraron/MI-EA/blob/master/08.HF_game.pdf)  és megoldás: [Alfa-béta.jpg](https://github.com/gabboraron/MI-EA/blob/master/Alfa_b%C3%A9ta.jpg)

## mesterséges genetikus algoritmusok/evolúciós algoritmusok
https://www.youtube.com/watch?v=_0TX-pHKRIc

> **Mintafeladat**
>
> Tervezzen evolúciós algoritmust az utazó ügynök probléma minél jobb megoládásának előállítására!
>
> Adott n város a közöttük vezető utak költségeivel. Melyik a legolcsóbb olyan útvonal, amely egy adott városból indulva mindegyik várost  pontosan egyszer érintve visszatér a kiinduló városba?
>
> Készítsen egy rövid dokumentációt:
> 
> - problématér (Mik legyenek a probléma egyedei?)
> - reprezentáció (Hogyan kódoljuk az egyedeket?)
> - rátermettségi függvény (Hogyan mérjük az egyedek rátermettségét?)
> - evolúciós operátorok (Javasoljon kiválasztásra, rekombinálásra, mutációra, visszahelyezésre egy-egy módszert.)
> - stratégiai paraméterek (Mi legyen populáció mérete, a mutáció valószínűsége, az utódképzési- és a visszahelyezési táta?)
> - Mutasson be egy evolúciós ciklust!
>
> **Mintamegoldás: [EvolúcióHF_mo.pdf](https://github.com/gabboraron/MI-EA/blob/master/Evol%C3%BAci%C3%B3HF_mo.pdf)**

## Automatikus következtetés
> **Mintafeladat**
>
> Axiómák: „Aki tud írni és olvasni, az nem analfabéta.  A delfinek analfabéták. Néhány delfin intelligens." 
>
> Célállítás: "Vannak olyan intelligens lények, akik nem tudnak írni és olvasni."
>
> Bizonyítsa be rezolúcióval és szabályalapú következtetéssel, hogy a célállítás következik az axiómákból.
> 
> Meg kell adni:
>
> - Az axiómák és a célállítás formuláit
> - Kiinduló klózokat
> - Cáfolati gráfot
> - Szabályalapú reprezentációt (tényállítás, szabályok, célállítás)
> - A szabályalapú következtetés irányát.
> - A bizonyítást leíró ÉS/VAGY gráfot
>
> Segítség:
> 
> 1. Használja az alábbi szimbólumokat
> 
> Predikátum szimbólumok:
> 
> - A(x)     : x analfabéa
> - I(x)      : x intelligens
> - D(x)    : x egy delfin
> - IO(x) : x ctud írni és olvasni
> 
> 2. A rezolúciónál mindig csak olyan klózpárt rezolváljon, ahol az egyik klóz a célállításból származik.
>
> 3. Ha van IO(x) → ! A(x) szabálya, akkor használhatja az A(x) → ! IO(x) (kontrapozitív) szabályt is.
>
> **Mintamegoldás: [KövetkeztetésHF_mo.pdf](https://github.com/gabboraron/MI-EA/blob/master/K%C3%B6vetkeztet%C3%A9sHF_mo.pdf)**

## bizonytalanság kezelés
https://www.inf.u-szeged.hu/~berendg/?pp=teaching&subj=dm

