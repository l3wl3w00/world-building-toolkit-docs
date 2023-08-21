# Worldbuilding Toolkit Specifikáció

## 1. Rövid leírás
A toolkit célja, hogy felhasználóiknak platformot biztosítson bonyolult világépítési projektek létrehozásához és kezeléséhez, elsősorban egy interaktív világtérkép és egy eseménynaptár építésére összpontosítva.

---

# 2. Általános leírás:

## 2.1 Felhasználói felületek:
A kliensalkalmazás intuitív grafikus felhasználói felületet biztosít a térképpel és az idővonalakkal történő interakcióhoz. A felület lehetővé teszi a felhasználó számára olyan feladatok elvégzését, mint a térkép földrajzi jellemzőinek hozzáadása/törlése/módosítása és az eseménynaptár eseményeinek kezelése. A világ egy 3D-s gömbként jelenik meg, ami egy bolygót reprezentál. Ezt forgatva lehet tetszőlegesen módosítani. Lehet pontszerű világelemeket és kiterjedt világrészeket hozzáadni. Egy kiterjedt világrész összeállítása úgy működik, hogy a felhasználó a gömbön meghúz egy körvonalat, majd leokézza, ezzel elmentve a részt.    

---

# 3. Rendszerfunkciók:

## 3.1 Authentikáció
Az akalmazás használatához regisztrálni kell. Minden felhasználó csak az általa készített világot látja. Az authentikáció történhet klasszikus e-mail cím/felhasználó és jelszó módon, vagy pedig egy Oauth 2.0 providerrel, pl.: Google.

## 3.2 Interaktív világtérkép:
A felhasználó létrehozhatja és szerkesztheti világának térképét. Ez magában foglalja a nagyobb földrajzi jellemzők elhelyezését és módosítását.
A megszerkesztés menete:
- A felhasználó megnyom a felhasználói felületen egy gombot, amivel belépt a szerkesztő módba.
- A felhasználó kiválasztja, hogy milyen típusú földrajzi elemet akar felvenni (pontszerű / kitejedt zárt / kiterjedt nem zárt)
- kiterjedt testek esetén a felhasználó megrajzolja a test körvonalát az egérrel, kattintásokkal, zárt testek esetén pedig csak kattintással egyből elhelyezi.
- A felhasználó kiválasztja, hogy milyen színű legyen, és hogy milyen típusú földrajzi elem az 

A változásokat a szerverhez küldik feldolgozásra és az adatbázis frissítésére.
A szerver az aktualizált adatokkal válaszol a változások tükrözésére.

## 3.3 Alapvető leíró elemek:
A felhasználó hozzáadhat és módosíthat leírásokat és egyéb attribútumokat minden földrajzi jellemzőhöz.
Felhasználói bemenet a leírásokhoz és attribútumokhoz.
A változásokat a szerverhez küldik feldolgozásra és az adatbázis frissítésére.
A szerver az aktualizált adatokkal válaszol a változások tükrözésére.

## 3.4 Földrajzi elemek:
Több fajta földrajzi elem van.
Kiterjedtség szempontjából:
- pontszerű
- kitejedt (zárt)
- kiterjedt (nem zárt)

Földrajzi szempontból:
- Kontinens
- Város
- Erdő
- Folyó
- Tó
- stb...

## 3.5 Személyek:
Lehessen fikcionális személyeket is felvenni/lekérni/törölni/módosítani.

Személyeket eseményekhez lehessen linkelni, egyelőre szemantikai jelentés nélkül, csak annyit, hogy ott voltak, vagy valamilyen módon kapcsolódnak hozzá

## 3.6 Egyszerű idővonal:
A felhasználó létrehozhat egy idővonalat, és hozzáadhat, módosíthat vagy eltávolíthat jelentős történelmi eseményeket. A legtöbb eseményt egy földrajzi helyhez lehet kötni.
Felhasználói bemenet az események hozzáadásához, módosításához vagy eltávolításához.
A változásokat a szerverhez küldik feldolgozásra és az adatbázis frissítésére.
A szerver az aktualizált adatokkal válaszol a változások tükrözésére.

---

# 4. Jövőbeli fejlesztési lehetőségek
- Több bolygó
- Több entitás felvétele:
    - Személyekhez tartozó külső / belső tulajdonságok
    - Politikai rendszerek -> személyeknek lehet politikai/társadalmi státusza
    
- Különböző szabályok felvétele amik megszegésekor figyelmezteti a felhasználót az inkozisztenciára
    pl.: 
    - Egy esemény, ahol két olyan ember találkozik, akik nem éltek egyszerre.
    - Ha egy olyan országban valaki uralomra kerül, de még az ő uralma alatt valaki más van megemlítve az ország vezetőjeként
    - Személyek tulajdonságai alapján ha olyat cselekednek ami nem jellemző rájuk, akkor azt emelje ki
    - Ha egy völgy közelében nincsenek hegyek
    - Óceánon belülre ne lehessen erdőt tenni
    - Lehessen saját földrajzi elemeket megadni saját szabályokkal
    - stb...
- chatgpt beépítése, hogy adjon ötleteket

---

# 5. Tech stack

## Kliens:
- C#, .NET 8
- Unity Engine

## Backend:
- C#, .NET 8
- ASP.NET Core
- Entity Framework Core
- MySql

A kettő RESTful API-val kommunikál egymással