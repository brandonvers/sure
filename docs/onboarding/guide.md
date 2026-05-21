# Üdvözöl a Sure!

Ez az útmutató segít az új felhasználóknak:

1. Sure fiók létrehozásában
2. Az első számlák hozzáadásában
3. Tranzakciók rögzítésében

Az útmutató kitér az **eszköz** és **kötelezettség** számlák közötti különbségekre is – ez egy kulcsfontosságú fogalom a Sure egyenlegeinek megértéséhez!

> [!IMPORTANT]
> A Sure gyorsan fejlődik. Ha valami pontatlanságot találsz az útmutató követése közben, kérjük:
> 
> - Kérdezz a [Discordon](https://discord.gg/36ZGBsxYEK)
> - Nyiss egy [issue-t](https://github.com/we-promise/sure/issues/new/choose)
> - Vagy ha tudod a választ, nyiss egy [PR-t](https://github.com/we-promise/sure/compare)!


## 1. Sure fiókod létrehozása

Miután a Sure telepítve van, nyiss egy böngészőt és navigálj a [localhost:3000](http://localhost:3000/sessions/new) címre.<br />
Látni fogod a **bejelentkezési oldalt** (lásd lent). Mivel még nincs fiókunk, kattints a **Sign Up** gombra a kezdéshez.

<img width="2508" height="1314" alt="Kezdőoldal friss telepítés után." src="https://github.com/user-attachments/assets/2319dc87-5615-4473-bebc-8360dd983367" />
<br />
<br />

Néhány rövid képernyőn keresztül beállíthatod a **bejelentkezési adataidat**, **személyes információidat** és **preferenciáidat**.<br />
Ha megérkezel a főoldalra, ahol **Még nincsenek számlák** felirat látható – készen vagy!

<img width="2508" height="1314" alt="A Sure üres főoldala, számlák nélkül." src="https://github.com/user-attachments/assets/f06ba8e2-f188-4bf9-98a7-fdef724e9b5a" />
<br />
<br />

> [!NOTE]
> Az útmutató következő részei bemutatják, hogyan lehet **manuálisan hozzáadni számlákat és tranzakciókat** a Sure-ban.<br />
> Ha inkább adatszolgáltatói integrációt szeretnél használni, lásd:
> 
> - [**Lunch Flow**](https://www.lunchflow.app/)
> - [**Plaid**](/docs/hosting/plaid.md)
> - [**SimpleFIN**](https://beta-bridge.simplefin.org/)
> - [**Enable Banking**](https://enablebanking.com/) (béta)
> - [**CoinStats**](https://coinstats.app/) (béta)
>
> Még ha integrációt is használsz, javasoljuk, hogy olvasd végig ezt az útmutatót, hogy megértsd a **számlatípusokat** és azok működését a Sure-ban.


## 2. Számlatípusok a Sure-ban

A Sure többféle számlatípust támogat, amelyek **Eszközökre** (amid van) és **Tartozásokra/Kötelezettségekre** (amivel tartozol) oszthatók:

| Eszközök         | Tartozások/Kötelezettségek |
| ---------------- | -------------------------- |
| Készpénz         | Hitelkártya                |
| Befektetés       | Hitel                      |
| Kripto           | Egyéb kötelezettség        |
| Ingatlan         |                            |
| Jármű            |                            |
| Egyéb eszköz     |                            |


## 3. Hogyan működnek az eszközszámlák?

A készpénz-, folyószámla- és megtakarítási számlák **növekednek**, amikor pénzt helyezel el, és **csökkennek**, amikor pénzt költesz.

Példa:

- Kezdő egyenleg: 500 $
- 20 $ kiadás rögzítése → az egyenleg most 480 $
- 100 $ bevétel rögzítése → az egyenleg most 580 $


## 4. Hogyan működnek az adósságszámlák (kötelezettségek)?

A kötelezettségszámlák azt követik, hogy mennyi pénzzel **tartozol**, ezért a számítás *fordítottnak* tűnhet az eszközszámlákhoz képest.

**Alapszabály:**

- **Pozitív egyenleg** = tartozol pénzzel
- **Negatív egyenleg** = a bank tartozik *neked* (pl. túlfizetés vagy visszatérítés esetén)

**A tranzakciók így viselkednek:**

- **Kiadások** (pl. vásárlások) => növelik a tartozásodat (többel tartozol)
- **Befizetések vagy visszatérítések** => csökkentik a tartozásodat (kevesebbet tartozol)

Hitelkártya példa:

1. Egyenleg: **200 $ tartozás**
2. 20 $ elköltve => Most 220 $-ral tartozol (az egyenleg *nő*, piros)
3. 50 $ befizetve => Most 170 $-ral tartozol (az egyenleg *csökken*, zöld)

Túlfizetés példa:

1. Egyenleg: -44 $ (a bank 44 $-ral tartozik neked)
2. 1 $ elköltve => A bank most **43 $-ral** tartozik neked (az egyenleg -43 $-ként jelenik meg, nullához közeledve)

> [!TIP]
> Miért működik így? Ez megfelel a standard könyvelési elveknek, és ugyanúgy jelenik meg, ahogy a hitelkártya-szolgáltatód mutatja online. Gondolj a kötelezettség egyenlegére mint „**Tartozás összege**"-re, nem mint elérhető készpénzre.


## 5. Gyors összefoglaló: Eszköz vs. Kötelezettség viselkedése

| Művelet           | Eszközszámla (pl. folyószámla) | Kötelezettségszámla (pl. hitelkártya) |
| ----------------- | ------------------------------ | ------------------------------------- |
| 20 $ elköltve     | Egyenleg ↓ 20 $                | Egyenleg ↑ 20 $ (több a tartozás)     |
| 50 $ megkapva     | Egyenleg ↑ 50 $                | Egyenleg ↓ 50 $ (kevesebb a tartozás) |
| Negatív egyenleg  | Folyószámlahitel               | A bank tartozik *neked*               |


## 6. Számlák hozzáadása

Ebben a példában egy **Megtakarítási számlát** adunk hozzá.<br />

> [!TIP]
> Ha **hitelkártyát**, **hitelt** vagy bármilyen **tartozást** adsz hozzá, ügyelj arra, hogy **Hitelkártya** vagy **Kötelezettség** számlatípust válassz a **Készpénz** helyett. Ez biztosítja, hogy az egyenlegek helyesen frissüljenek és megegyezzenek azzal, amit a bankod mutat.

A legtöbb bankszámla (folyószámla, megtakarítás, pénzpiaci számla) **Készpénzszámla**.
1. Kattints a **+ Számla hozzáadása** → **Készpénz** → **Számlaegyenleg megadása** lehetőségre
2. Töltsd ki az adatokat:
   - Számla neve
   - Jelenlegi egyenleg
   - Számla altípusa (itt adhatod meg, hogy folyószámla, megtakarítás vagy egyéb)
3. Kattints a **Számla létrehozása** gombra, amikor készen állsz.

<img width="500" height="303" alt="Készpénzszámla létrehozási menü" src="https://github.com/user-attachments/assets/e564a447-c85e-403e-979b-efe770ea2a61" />
<br />
<br />

A létrehozás után visszakerülsz a **Főoldalra**.<br />
Most látni fogod:
- Az új készpénzszámládat a **Számlák** listában (bal oldal)
- A számlák áttekintését a középső részen, a nettó vagyon sáv alatt.

Hogy ez a sáv mozogni kezdjen, adjunk hozzá néhány tranzakciót!

<img width="2508" height="1314" alt="A Sure főoldala egy számlával, tranzakciók nélkül." src="https://github.com/user-attachments/assets/7766a0cd-6b20-48f0-9ba2-87dfddd77236" />


## 7. Tranzakciók hozzáadása

Tranzakció hozzáadásához:
1. Menj a **Tranzakciók** oldalra (bal oldalsáv, a **Főoldal** alatt, a **Költségvetések** felett)
2. Kattints a **+ Új tranzakció** gombra (jobb felső sarok)
3. Válaszd ki a tranzakció típusát:
   - **Kiadás** → Pénzköltés
   - **Bevétel** → Pénzbevétel
   - **Átutalás** → Pénz mozgatása számlák között
4. Add meg az adatokat, majd kattints a **Tranzakció hozzáadása** gombra

Ezután látni fogod a hozzáadott tranzakciót a **tranzakciótörténetedben**, valamint a **nettó vagyon diagram** is ennek megfelelően frissül.

<img width="500" height="512" alt="Kitöltött kiadás űrlap" src="https://github.com/user-attachments/assets/7c1d38d1-edb8-4d12-8b3e-bbef4836cc92" />


## 8. Befektetési számlák kezelése

Ha befektetéseket is követsz a Sure-ban, további funkciók állnak rendelkezésedre a portfóliód pontos kezeléséhez.

### Bekerülési érték (Cost Basis) követése

A bekerülési érték követése segít megérteni a befektetéseid eredeti vételárát, ami elengedhetetlen a hozamszámításhoz és az adóbevalláshoz.

#### Bekerülési érték forrásai

A Sure három forrásból követi a bekerülési értéket:

| Forrás          | Leírás                                                        |
| --------------- | ------------------------------------------------------------- |
| **Manuális**    | Általad közvetlenül megadott értékek                          |
| **Kalkulált**   | Vételi tranzakcióidból és tranzakciótörténetedből számított   |
| **Szolgáltató** | Pénzügyi intézményedtől importált (Plaid, SimpleFin, stb.)   |

#### Prioritási sorrend

Ha több forrás is ad bekerülési értéket, a Sure ezt a prioritást alkalmazza:

**Manuális > Kalkulált > Szolgáltató**

Ez azt jelenti:
- A manuális értékek mindig elsőbbséget élveznek
- A kalkulált értékek felülírják a szolgáltatói adatokat
- A szolgáltatói adatokat akkor használja, ha más forrás nem áll rendelkezésre

#### Zárolás védelme

Amikor manuálisan állítasz be bekerülési értéket, a Sure automatikusan zárolja azt, hogy az automatikus frissítések ne írják felül. Ez biztosítja, hogy a manuális bejegyzéseid megmaradjanak a szinkronizálások során.

#### Bekerülési érték manuális beállítása

A bekerülési értéket kétféleképpen állíthatod be:

**A Pozíciók listájából:**

1. Navigálj a befektetési számládhoz
2. Keresd meg a pozíciót a portfóliódban
3. Kattints az átlagos bekerülési érték melletti ceruza ikonra
4. Add meg:
   - **Teljes bekerülési érték**: az összes részvényért fizetett teljes összeg
   - **Részvényenkénti bekerülési érték**: az átlagos részvényenkénti ár
5. Az űrlap automatikusan konvertál a kétféle érték között
6. Kattints a **Mentés** gombra

A rendszer megerősítést kér, ha meglévő bekerülési értéket írsz felül.

<img width="531" height="597" alt="image" src="https://github.com/user-attachments/assets/b5a6aafe-de9e-447e-95a6-6000e68fb695" />

**A Pozíció részletező panelből:**

1. Kattints egy pozícióra a részletező panel megnyitásához
2. Az Áttekintés részben kattints az „Átlagos bekerülési érték" melletti ceruza ikonra
3. Add meg a bekerülési értéket (összesített vagy részvényenkénti)
4. Kattints a **Mentés** gombra

Mentés után látni fogod:
- Egy lakat ikont, ami jelzi, hogy az érték védett
- Egy forrásjelzést: „(manuális)"

#### Zárolás feloldása

Ha engedélyezni szeretnéd az automatikus frissítéseket a bekerülési érték újraszámításához:

1. Nyisd meg a pozíció részletező panelt
2. Görgess a **Beállítások** részhez
3. Keresd meg a „Bekerülési érték zárolva" opciót
4. Kattints a **Feloldás** gombra

Feloldás után:
- A lakat ikon eltűnik
- A jövőbeli szinkronizálások frissíthetik a bekerülési értéket
- A kalkulált értékek (tranzakciókból) felváltják a manuális értéket

<img width="529" height="231" alt="image" src="https://github.com/user-attachments/assets/89d4c64f-7151-4702-b79f-1e22d47a2bee" />

#### Kétirányú konverzió

A bekerülési érték szerkesztő valós idejű konverziót biztosít az összesített és a részvényenkénti értékek között:

- Összesített költség megadása → automatikusan kiszámítja a részvényenkénti értéket
- Részvényenkénti érték megadása → automatikusan kiszámítja az összesített értéket

Ez megkönnyíti a bekerülési érték megadását, bármelyik formátumban is áll rendelkezésedre az adat.

### Befektetési tevékenység címkék

A tevékenység címkék segítenek osztályozni és megérteni a befektetési tranzakciókat. Jelzőként jelennek meg a tranzakciólistádban, és használhatók a befektetési tevékenységed rendszerezéséhez és szűréséhez.

#### Elérhető tevékenységtípusok

A Sure ezeket a befektetési tevékenység címkéket támogatja:

| Címke             | Leírás                                      |
| ----------------- | ------------------------------------------- |
| **Vétel**         | Értékpapírok vásárlása                      |
| **Eladás**        | Értékpapírok eladása                        |
| **Befizetés**     | A befektetési számlára utalt pénz           |
| **Kifizetés**     | A befektetési számláról kivett pénz         |
| **Osztalék**      | Kapott osztalékfizetések                    |
| **Kamat**         | Megszerzett kamat                           |
| **Újrabefektetés**| Újrabefektetett osztalékok vagy kifizetések |
| **Beáramlás**     | Számlára áramló készpénz                    |
| **Kiáramlás**     | Számláról kiáramló készpénz                 |
| **Díj**           | Számla- vagy tranzakciós díjak              |
| **Váltás**        | Deviza- vagy értékpapírcsere                |
| **Átutalás**      | Számlák közötti átutalások                  |
| **Egyéb**         | Vegyes tranzakciók                          |

#### Tevékenység címkék beállítása

A tevékenység címkéket kétféleképpen állíthatod be:

**Manuálisan, egyedi tranzakcióknál:**

1. Nyiss meg egy tranzakciót egy befektetési vagy kripto számlán
2. Görgess a **Beállítások** részhez
3. Keresd meg a „Tevékenység típusa" opciót
4. Válassz egy címkét a legördülő menüből
5. A változtatás automatikusan mentődik

**Automatikusan, szabályokkal:**

Hozz létre szabályokat a tranzakciók automatikus címkézéséhez minták alapján:

1. Menj a **Beállítások > Szabályok** menübe
2. Hozz létre egy új szabályt
3. Állíts be feltételeket (pl. „HA a tranzakció neve tartalmazza: 'DIVIDEND'")
4. Add hozzá a műveletet: „Befektetési tevékenység címke beállítása"
5. Válaszd ki a címkét (pl. „Osztalék")
6. Mentsd el a szabályt

<img width="577" height="666" alt="image" src="https://github.com/user-attachments/assets/6660a3cc-af78-4199-8edc-18c198bbaad3" />

Példa szabályok:
- HA a név tartalmazza: „DIVIDEND" → állítsd a címkét: „Osztalék"
- HA a név tartalmazza: „INTEREST" → állítsd a címkét: „Kamat"
- HA a név tartalmazza: „FEE" → állítsd a címkét: „Díj"

A szabályok automatikusan érvényesülnek az új tranzakciókra, és futtathatók a meglévő tranzakciókon is.

#### Tevékenység címkék megtekintése

A tevékenység címkék jelzőként jelennek meg:
- Tranzakciólistákban
- Tranzakció részletező panelekben
- Számla-tevékenység nézetekben

Segítenek gyorsan azonosítani az egyes befektetési tranzakciók jellegét anélkül, hogy el kellene olvasnod a teljes tranzakció nevet.


## 9. Következő lépések

Most, hogy van egy számlád és az első tranzakciód:
- Fedezd fel a Sure által kínált többi számlatípust, és add hozzá a pénzügyeidhez relevánsakat.
- **Kategorizáld** és **jelöld meg** (tag) a tranzakciókat a jobb kereshetőség és riportolás érdekében.
- Kísérletezz a **Költségvetések** funkcióval a kiadási szokásaid nyomon követéséhez.
- Ha sok historikus tranzakciód van, használd a **Tömeges importálást** azok betöltéséhez.

A funkciók részletesebb útmutatói hamarosan érkeznek™.
