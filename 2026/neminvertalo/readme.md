# MÉRÉSI JEGYZŐKÖNYV
**Téma:** Nem invertáló alapkapcsolás vizsgálata TL071 műveleti erősítővel  
**Mérés helye:** [V3 Labor]  
**Mérés ideje:** 2026. [01] [28]  
**Mérést végezte:** [Hilóczki Krisztián]  

---

## 1. A mérés célja
Egy TL071 típusú műveleti erősítővel felépített nem invertáló erősítő áramkör működésének vizsgálata NI myDAQ adatgyűjtő eszköz segítségével. A cél az elméleti úton számított és a gyakorlatban mért feszültségerősítés ($A_v$) összehasonlítása, valamint a bemeneti és kimeneti jelek fázisviszonyának ellenőrzése.

## 2. Felhasznált eszközök és szoftverek
* **Műszer:** NI myDAQ (Data Acquisition Device)
* **Szoftver:** NI ELVISmx Instrument Launcher (Function Generator, Oscilloscope)
* **Áramköri elemek:**
    * 1 db TL071 műveleti erősítő
    * Ellenállások:
        * $R_1 = 11,8\ k\Omega$ (Földelő ellenállás a visszacsatoló körben)
        * $R_2 = 100,5\ k\Omega$ (Visszacsatoló ellenállás)
        * $R_{bias} \approx 100,2\ k\Omega$ (Bemeneti lezáró ellenállás)
    * Próbapanel (Breadboard), vezetékek

## 3. Kapcsolási rajz és elméleti háttér
A mérés során egy nem invertáló (fázist nem fordító) alapkapcsolást vizsgáltunk. A bemeneti jelet a nem invertáló (+) lábra kapcsoltuk, míg a visszacsatolás a kimenetről az invertáló (-) lábra érkezik az $R_1-R_2$ feszültségosztón keresztül.

**Elméleti erősítés számítása:**
A nem invertáló erősítő feszültségerősítését az alábbi képlet határozza meg:

$$A_{v,elm} = 1 + \frac{R_2}{R_1}$$

A rendelkezésre álló alkatrészek értékeivel:

$$A_{v,elm} = 1 + \frac{100,5\ k\Omega}{11,8\ k\Omega} = 1 + 8,517 \approx \mathbf{9,517}$$

## 4. Mérési beállítások
A méréshez az NI ELVISmx szoftvermoduljait használtuk az alábbi paraméterekkel (a *funkciogenerator.png* alapján):

**Függvénygenerátor (FGEN - AO0):**
* **Jelalak:** Szinuszos (Sine)
* **Frekvencia:** $100\ Hz$
* **Amplitúdó:** $1,00\ V_{pp}$ (Csúcstól-csúcsig)
* **DC Offset:** $0,00\ V$

## 5. Mérési eredmények
Az áramkör kimenetét és bemenetét az NI ELVISmx oszcilloszkópjával vizsgáltuk (a *scope.png* alapján).

**Mért értékek:**

| Csatorna | Jelölés | Funkció | Mért Feszültség ($V_{pp}$) | Frekvencia |
| :--- | :--- | :--- | :--- | :--- |
| **Channel 0 (Zöld)** | $U_{be}$ | Bemeneti jel | **1,003 V** | 100,001 Hz |
| **Channel 1 (Kék)** | $U_{ki}$ | Kimeneti jel | **9,488 V** | 100,001 Hz |

**Megfigyelések:**
* A kimeneti jel (Kék) fázisban van a bemeneti jellel (Zöld), ami igazolja a **nem invertáló** működést.
* A jelalak tiszta szinuszos, nem látható torzítás vagy vágás (a kimenet nem érte el a tápfeszültség korlátját).

## 6. Kiértékelés és számítások

**Mért erősítés meghatározása:**
A mért csúcstól-csúcsig feszültségek ($V_{pp}$) aránya alapján:

$$A_{v,mért} = \frac{U_{ki}}{U_{be}} = \frac{9,488\ V}{1,003\ V} \approx \mathbf{9,46}$$

## 7. Összegzés
A mérés során sikeresen összeállítottuk és vizsgáltuk a TL071 műveleti erősítővel felépített nem invertáló kapcsolást.
* Az áramkör a vártnak megfelelően, fázisordítás nélkül erősítette a jelet.
* Az elméleti erősítés ($9,52$) és a mért erősítés ($9,46$) közötti eltérés elenyésző ($<1\%$), ami az ellenállások tűréshatárán és a mérési pontatlanságon belül van.
* A mérés igazolta a tervezett áramkör helyes működését.
