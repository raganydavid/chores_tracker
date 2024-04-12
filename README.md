# ChoresTracker

http://chorestracker.infinityfreeapp.com/chores_tracker/

## Bevezetés, a téma ismertetése, témaválasztás indoklása

A Chorestracker egy olyan szoftver, amely célja, hogy megkönnyítse a házimunkával kapcsolatos szervezési problémákat a család számára. 
Ennek érdekében lehetőséget biztosít arra, hogy egy megbízott személy felügyelje és koordinálja a feladatokat. Természetesen ez a jog az anyát illeti meg, aki általában a háztartás szervezője.
A regisztráció során az admin jogosultságot kap, amely lehetővé teszi számára, hogy további tagokat hozzon létre és kezeljen. 
Ez lehetővé teszi számára, hogy hatékonyan oszthassa szét a feladatokat és delegálja a felelősségeket a családtagok között.

Ebben a fejezetben szeretnénk egy kicsit írni a projekt születésének részleteiről.
Az alapötlet munkában használt jegykezelő rendszer adta. Az  IT support területet vettük alapul és ott szükség van a megoltdott problémák dokumentálására, adminisztrációjára és a megoldási folyamat részletes követésére. 

Ezt ültettük át egy másik kontextusba és egy otthon használt applikációt hoztunk létre. Beleképzeltük egy egy nagyon elfoglalt soktagú család helyzetébe ahol egy applikáció segíthet a ház körüli teendők ellátásának koordinálásában. 
Így született meg a ChoresTracker egy elsődlegesen böngészőben használható program formájában. Az applikáció lehetőséget biztosít arra, hogy egy ház körüli teendőt, létrehozzanak, új részfeladattal lássanak el, vagy egyéb különböző fontos információkkal lássanak el a feladat elvégzése előtt, közben és természetesen után.
A következő fejezetekben szemléltetjük részletesen a fejlesztői és felhasználói dokumentációkat.

## Fejlesztői dokumentáció

Ebben a fejezetben szeretnénk részletes képet adni a fejleszés menetérő és a felhasznált technológiákról amelyeket  meg kellett tanulnunk és használnunk ahhoz, hogy a projekt elérje a jelenlegi formáját.

### Felhasznált technológiák

A tervezés ideje alatt Figma-t használtunk, ez manapság egy népszerű ingyenesen is elérhető web-applikáció a web designer-ek körében. Ebben próbálkattuk először, hogyan nézne ki szépen és logikusan az elrendezés.
Ekkor még a HTML-be,  CSS- be JavaScript-be kezdtük átültetni a terveinket, de hamar rájöttünk, hogy a technológia amit végül választottunk az a PHP lesz.
Frontend: PHP  Tailwind CSS könyvtár felel a kinézetért.
Backend: szintén PHP
Adatbázis: MySQL PHPMYAdmin-nal XAMPP-ben.
A fejlesztőkörnyezet: Visual Studio Code 

### Frontend

A frontend és a backend megvalósítását is PHP-ban készítettük el, valamint JavaScript-et is használtunk frontend rész felépítéséhez és interaktivitásának megvalósításához.  PHP segítségével dinamikus tartalmat generálunk, ami aztán HTML formájában kerül kiszolgálásra a böngésző felé. A PHP kód a szerveren fut, és a kliens (böngésző) kéréseire válaszolva generálja a HTML-t. A HTML tartalom tartalmaz Tailwind CSS-t is, aminek a segítségével formáztuk és interaktívvá tettük a felhasználói felületet.

### I.
	A start.view.php kódban a weboldal fő tartalomrészét jelenítettük meg, ahol egy háttérképet használtunk fel. A háttérkép központosítva és kitöltve jelenik meg a képernyőn:

<div class="min-h-[70vh]  bg-cover bg-center flex items-center justify-center" style="background-image: url('/chores_tracker/images/family.jpeg');">

Ezt követően keretet hoztunk létre, amit középre igazítottunk,a LOGIN" és "SIGN UP" gombokat helyeztük el benne:

<a class="block text-3xl border-4 border-black p-1 rounded-md hover:bg-black hover:text-white" href="login.php">LOGIN</a>
<a class  <div class="max-w-[30%] mx-auto flex justify-center items-center gap-6 p-6 bg-white border-8 border-black rounded-md">="block text-3xl border-4 border-black p-1 rounded-md hover:bg-black hover:text-white" href="signup.php">SIGN UP</a>

Amikor a "SIGN UP" feliratú gombra kattint egy felhasználó(href="signup.php"), akkor átirányítja a böngészőt a "signup.php" oldalra.

## II.

 A signup.view.php kódban a regisztráció funkcióit hoztuk létre. Ha az oldalon a Felhasználó a „SIGN UP” gombra kattint, akkor egy űrlap jelenik meg számára, ahol meg kell adni a nevet (NAME), az Email címét (EMAIL) és a jelszavát kétszer (másodszor megerősítésként), valamint az elküldés (SUBMIT) gombra kattintva elküldheti a regisztrációt. 
Ezek az információk szükségesek ahhoz, hogy a felhasználó sikeresen regisztráljon az oldalon, és ezáltal hozzáférjen az oldal különböző funkcióihoz vagy tartalmaihoz. A jelszó kétszeri megadása azért fontos, hogy minimalizálja a gépelési hibákból adódó problémákat, és biztosítsa, hogy a felhasználó pontosan adja meg a kívánt jelszót.

<div class="flex flex-col justify-center items-center" >

Ebben az esetben a flex és a flex-col osztályokat használtuk a flexbox elrendezés beállítására, és a justify-center és items-center osztályokat használtuk a tartalom függőleges és vízszintes középre igazítására a <div> elemen belül.

<h1 class="text-3xl">SIGN UP</h1>

Az itt látható <h1> elem a "SIGN UP" szöveget tartalmazza a text-3xl -osztálynévvel nagyobb betűméretet határoztunk meg.

<form action="" method='POST' class="flex flex-col gap-2 mt-2">

Ezzel lehetővé tesszük, a felhasználó számára, hogy adatokat küldjön a szerver felé, a form elem beállításával az űrlap  kezdő tartalmát határoztuk meg, a küldési metódust ( A "POST" metódus esetén az adatokat a HTTP kérés testében küldi el a szerver felé, így azok nem láthatóak a böngésző címsorában. Ez általában biztonságosabb, és több adat küldhető el vele). Az action attribútumot üresen hagytuk, mert az űrlap ezen az oldalon marad, tehát az adatok visszaküldése a saját oldalra azt teszi lehetővé, hogy a szerver megkapja az űrlap által beküldött adatokat, ahol a backend kód feldolgozza őket. Ez a feldolgozás magában foglalja az adatok validálását (például, hogy megfelelő formátumú-e az e-mail cím), majd az adatok adatbázisba mentését.

<label class="flex flex-col text-2xl" for="name">NAME: <input required class="border-2 border-black pl-2" id="name" name="name" type="text" placeholder="Your name goes here">
</label>

A label elem a mezőhöz tartozó feliratot határozza meg, amely ez esetben a NAME volt. Az input elem egy beviteli mezőt határozz meg amely szöveg típusú. A required mező jelentése a mező kitöltésének kötelezettségére hívja fel a felhasználó figyelmét. A name attribútum meghatározza az input mező nevét, amit a szerveroldali PHP kód során ezáltal tudunk azonosítani.  A placeholder attribútummal egy alapértelmezett szöveget állítottunk be ( „Your name goes here”)

<?php
    if($view_bag){
        echo $view_bag;
    }
?>
</div>

A $view_bag egy olyan változó, amely átadja az üzeneteket, hibajelzéseket vagy más információkat a vezérlő (controller) rétegről a nézet (view) réteg felé. A nézet réteg ezeket az információkat felhasználja annak megjelenítésére a felhasználói felületen.

### III. 

A login.view.php kódban egy bejelentkező űrlapot hoztunk létre.
A felhasználó beviteli mezők segítségével adja meg az e-mail címét és jelszavát. Az űrlapot a "LOGIN" gombbal lehet elküldeni. A <h1> elem tartalmazza a "LOGIN" feliratot. Az e-mail és jelszó mezőket címkék kísérik, amelyek segítik az  megadandó adatok megértését. Az adatokat a POST metódus segítségével küldik el a szervernek a felhasználók. A szerver válaszát a bejelentkezési folyamat állapotáról egy esetleges üzenet formájában jelenítődik meg. A PHP kód ellenőrzi, hogy van-e üzenet az állapotról, és ha van, akkor azt megjeleníti. A felhasználók könnyen kitölthetik az űrlapot, és a stílusok segítenek a megfelelő megjelenítésben és interakciók támogatásában. Az űrlap gombját a hover hatás hangsúlyozza ki, ami világosabbá válik, ha a felhasználó az egerét fölé viszi. A formátumot és az elrendezést könnyen áttekinthetővé tettük, így a felhasználók könnyen navigálhatnak és használhatják az űrlapot.

### IV.

A layout.view.php kódrészletében szereplő linkek és metaadatok a weboldal megjelenését és stílusát befolyásolják:

<link rel="stylesheet" href="/chores_tracker/output.css">: Ez a sor arra utal, hogy a weboldal használja az output.css nevű CSS fájlt a megjelenésének formázásához. A href attribútum megadja a fájl elérési útját.
<link rel="preconnect" href="https://fonts.googleapis.com">: Ez a sor azt jelzi a böngészőnek, hogy előzetesen csatlakozzon a fonts.googleapis.com domainhez, ami javítja a betöltési teljesítményt, ha a weboldal használ külső betűtípusokat ezen a domain-en keresztül.
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>: Ez a sor egy másik előzetes csatlakozást jelöl ki, ezúttal a fonts.gstatic.com domainre. Ez is a külső betűtípusok betöltési teljesítményét javítja. A crossorigin attribútum azt jelzi, hogy az erőforrások kereszt eredetű kérései kerülnek végrehajtásra, ami a biztonságosságot szolgálja.
<link href="https://fonts.googleapis.com/css2?family=VT323&display=swap" rel="stylesheet">: Ez a sor hivatkozik egy külső CSS fájlra a fonts.googleapis.com-on keresztül, ami a VT323 nevű betűtípust tartalmazza. Ez a fájl importálja és állítja be a VT323 betűtípust a weboldal számára. A display=swap paraméter azt jelzi a böngészőnek, hogy a betűtípus betöltésekor cserélje ki az alapértelmezett stílust a letöltés befejezése előtt, hogy ne legyenek érzékelhető ugrások az oldalon.
Ebben a kódrészletben a fejléc részben található egy navigációs menü, amely tartalmazza az "About" és "Contact" linkeket. Ezek a linkek a felhasználók számára lehetővé teszik, hogy az "About" és "Contact" oldalakra navigáljanak.
Ez az alábbi részlet a kódban:

<nav>
            <ul class="flex gap-4 pr-4 text-3xl">
                <?php echo  isset($_SESSION['user_logged_in']) ? '<li> <a class="hover:border-4 border-black rounded-md p-2" href="/chores_tracker/logout.php"> LOGOUT </a>  </li>' :'' ?>
                <li><a class="hover:border-4 border-black rounded-md p-2" href="h"> ABOUT </a></li>
                <li><a class="hover:border-4 border-black rounded-md p-2" href="h"> CONTACT </a></li>
            </ul>
        </nav>

A footer részben pedig szintén navigációs linkek találhatók, ezek a "SETUP"( beállítások) "Terms of Use" ( használati feltételek) és "Privacy Policy" ( Adatvédelmi) linkek. Ezek a webhely felhasználási feltételeit és adatvédelmi irányelveit tartalmazzák, és fontosak a felhasználók számára a webhely használata során felmerülő jogi és adatvédelmi kérdésekkel kapcsolatban.
Ez az alábbi részlet a kódban:

    <footer class="border-8 border-black rounded-md">
        <nav class="flex justify-between items-center">
            <ul class=" p-4 justify-end text-3xl">
                <li> <a class="hover:border-4 border-black rounded-md p-1"  href="/chores_tracker/setup.php">SETUP</a> </li>
            </ul>
            <ul class="flex gap-4 p-4 justify-end text-3xl">
                <li><a class="hover:border-4 border-black rounded-md p-1" href="h"> TERMS OF USE </a></li>
                <li><a class="hover:border-4 border-black rounded-md p-1" href="h"> PRIVACY POLICY </a></li>
            </ul>
        </nav>
    </footer>

### V.

A details.view.php kódban az adott kódrészlet az "EDIT" gombra kattintva meg lehet jeleníteni a házimunka részleteit, és szerkesztheti azokat. Létrehoztunk egy PHP változót ($status), amely tárolja a házimunka aktuális állapotát. Definiáltunk egy tömböt ($array_of_options), amely tartalmazza a lehetséges állapotokat. Létrehoztunk egy másik tömböt ($array_of_options_without_current_status), amely kizárja az aktuális állapotot a választható opciók közül. Összefűztük ezeket a tömböket egy új tömbbe ($array_to_display), amely a szerkesztő formban megjelenítendő opciókat tartalmazza.
A HTML kódban egy div elemet hoztunk létre, amely a házimunka részleteit tartalmazza, és lehetőséget ad azok szerkesztésére. Egy gombot helyeztünk el a felhasználó irányítópultjának visszatérésére. Létrehoztunk egy űrlapot, amely lehetővé teszi a feladat részleteinek szerkesztését. Megjelenítettük a feladat címét, létrehozásának dátumát, határidő dátumát és egy legördülő menüt az állapotváltoztatáshoz. Rejtett input mezőt helyeztünk el az azonosító átviteléhez a szerver felé a változtatások mentésekor. Megjelenítettük a feladat leírását és lehetőséget adtunk azok szerkesztésére. Hozzáadtunk egy gombot a változtatások mentéséhez. Létrehoztunk egy kommentszekciót, ahol további megjegyzéseket lehet fűzni. A kód végén megjelenítettük a feladathoz tartozó kommenteket.
		
### VI.
	
A dashboard.view.php kódban  a felhasználók számára láthatóvá válik a bejelentkezett állapot. Továbbá látni lehet számára az elvégzendő feladatot, amit a admin oszt ki. A felhasználó szerkesztheti illetve készként megjelölheti a kapott feladatot. Ez a kódrészlet a weboldalon megjelenít egy felhasználó által elvégzendő tevékenységek listáját: az elvégzett és az el nem végzett feladatokat. Először létrehoztunk két változót: az "incomplite_chores" azokat a feladatokat tartalmazza, amelyek még nincsenek befejezve, míg a "complete_chores" azokat, amelyek már befejeződtek.

<?php
    $incomplite_chores = array_filter($model,fn($object)=>$object->status != 'done');
    $complete_chores = array_filter($model,fn($object)=>$object->status == 'done');
?>

A HTML kódban két külön konténert hoztunk létre a két csoport feladatok megjelenítéséhez. Mindkét konténer egy címet és egy táblázatot tartalmaz, ahol a feladatok részletei jelennek meg.

<div class="border-8 border-black rounded-md mt-4 max-h-[500px] min-h-[300px] overflow-y-scroll">
    <h3 class="text-center my-5 text-3xl ">MY CHORES</h3>
    <div class="mx-4 my-2 grid grid-rows-auto repeat(7,minmax(80px,1fr) gap-5 max-w-[1500px]">
        <!-- ... -->
    </div>
</div>

<div class="border-8 border-black rounded-md my-4 max-h-[500px] min-h-[300px] overflow-y-scroll">
    <h2 class="text-center my-5 text-3xl ">DONE CHORES</h2>
    <div class="mx-4 my-2 grid grid-rows-auto repeat(7,minmax(80px,1fr) gap-5 max-w-[1500px]">
        <!-- ... -->
    </div>
</div>

Minden táblázat sorában megjelenítettük a feladat címét, létrehozóját, létrehozás dátumát, határidő dátumát, állapotát és leírását.

<?php foreach ($incomplite_chores as $key=>$value) : ?>
    <div class="col-start-1">
        <?= $incomplite_chores[$key]->title ?>
    </div>
    <div class="col-start-2">
        <?= $incomplite_chores[$key]->creator ?>
    </div>
    <div class="col-start-3">
        <?= $incomplite_chores[$key]->creation_date ?>
    </div>
    <div class="col-start-4">
        <?= $incomplite_chores[$key]->due_date ?>
    </div>
    <div class="col-start-5">
        <?= $incomplite_chores[$key]->status ?>
    </div>
    <div class="col-start-6">
        <?= $incomplite_chores[$key]->description ?>
    </div>
    <div class="col-start-7">
        <!-- $model[$key]->id  -->
        <a class="bg-green-300 p-2 border-2 border-black hover:bg-green-500 rounded-md" href="details.php?id=<?php echo $incomplite_chores[$key]->id ?>">EDIT</a>
        <a class="bg-red-300 border-2 border-black hover:bg-red-500 rounded-md  p-2" href="dashboard.php?action=quick_done&id=<?php echo $incomplite_chores[$key]->id; ?>&status=done" >DONE</a>
    </div>

<?php endforeach; ?>
Az "incomplete_chores" konténerben minden feladathoz hozzáadtunk két gombot: egy "EDIT" gombot a feladat részleteinek szerkesztéséhez, valamint egy "DONE" gombot, amely lehetővé teszi a feladat jelölését befejezettnek.

<div class="col-start-7">
    <!-- $model[$key]->id  -->
    <a class="bg-green-300 p-2 border-2 border-black hover:bg-green-500 rounded-md" href="details.php?id=<?php echo $incomplite_chores[$key]->id ?>">EDIT</a>
    <a class="bg-red-300 border-2 border-black hover:bg-red-500 rounded-md  p-2" href="dashboard.php?action=quick_done&id=<?php echo $incomplite_chores[$key]->id; ?>&status=done" >DONE</a>
</div>

A "complete_chores" konténerben csak az elvégzett feladatok vannak felsorolva, és a feladathoz egy "EDIT" gomb található, ami a feladat szerkesztő oldalára irányít.

<div class="col-start-7">
    <!-- $model[$key]->id  -->
    <a class="bg-green-300 hover:bg-green-500 border-2 border-black rounded-md p-2" href="details.php?id=<?php echo $complete_chores[$key]->id ?>">EDIT</a>
</div>

Ez a kódrészlet tehát egy áttekinthető módon jeleníti meg a felhasználó feladatait, és lehetőséget ad a feladatok szerkesztésére vagy megjelölésére.	

### VII.

Az edit_chore.view.php forráskódjában egy űrlapot és hozzá tartozó komment szekciót jelenítettünk meg az Admin számára. Itt lehetősége van az Adminak a házimunkák részleteinek szerkesztésére és a hozzászólások hozzáadására.
A <div> elem egy keretet hoz létre az űrlap és a komment szekció körül. A keret stílusát a border-8 border-black és rounded-md osztályokkal állítottuk be.
A "BACK TO DASHBOARD" link visszairányítja az Admint a főoldalra(index.php). Az űrlapban lehetőség van a házimunka részleteinek szerkesztésére, mint például a cím, az elvégzett dátum, a határidő, az állapot és a leírás. Az "ASSIGNED TO" legördülő menüben az Admin választhat, hogy a házimunkát kihez rendelje.
Az Admin  hozzáadhat új kommenteket a házimunkához az "ADD COMMENT" gombbal. A komment szekcióban láthatók a korábban hozzáadott kommentek, minden egyes komment tartalmazza a komment szövegét és a nevet. A kódrészlet áttekinthető módon jeleníti meg az Admin által szerkeszthető házimunka részleteit és lehetőséget biztosít új kommentek hozzáadására.

### VIII.

A create_chore.view.php-kódban is főleg a stíluselemekről írnánk. A Tailwind CSS különböző osztályok segítségével használható a stílusok beállításához, például keretek, háttérszínek, betűméretek és margók definiálásához. A weboldal bejelentkezésekor az Admin CREATE CHORE + felületre kattint, akkor egy űrlapot jelenít meg számára, ami lehetővé teszi a feladatok létrehozását.
 Az űrlap fő mezői:
Cím (TITLE): szövegmező, ahol megadható a feladat címe.
Az űrlapnak van egy kerete, ami egy stílusos megjelenést ad neki, az űrlap kerete a következő rész a kódban.

<div class="border-8 border-black rounded-md relative mt-4 mb-4">

Itt a <div> elemet egy keretben hoztuk létre létre az űrlap körül, amelynek vastagsága és stílusa a border-8 border-black és a rounded-md osztályoknak megfelelően állítottunk be. Ez a keret stílusos megjelenést biztosít az űrlapnak, és kiemeli azt a többi tartalomtól a weboldalon.
A kód felső részén a  "BACK TO DASHBOARD" nyomógomb látható, ami visszavezeti az admint  vezérlőpultra.
Ez a következő rész a kódban:

<a class="bg-red-300 block border-4 border-black hover:bg-red-500 rounded-md max-w-[150px] text-center p-1 absolute left-1 top-1" href="index.php"> <- BACK TO DASHBOARD</a>

Az űrlap egy címet(TITLE),egy hozzárendelt személyt(Assigned to), egy határidőt(DUE DATE) és egy leírást(DESCRIPTION) kér be az admintól .
Ezek a mezők a HTML kódban az alábbiak szerint helyezkednek el:

  <label for="title" class="text-2xl">TITLE:
    <input class="pl-2 border-2 border-black rounded-md min-w-[100%]" name="title" id="title" type="text">
</label>

<label for="assigned_to" class="text-2xl flex flex-col">ASSIGNED TO:
    <select class="border-2 border-black rounded-md" name="assigned_to" id="assigned_to">
        <?php foreach($model as $item) : ?>
            <option value="<?= $item ?>"><?= $item ?></option>
        <?php endforeach; ?>
    </select>
</label>

<label for="due_date" class="text-2xl flex flex-col">DUE DATE:
    <input class="border-2 border-black rounded-md pl-2" id="due_date"  name="due_date" type="date" >
</label>

<label for="description" class="text-2xl flex flex-col">DESCRIPTION:
    <textarea class="border-2 border-black rounded-md pl-2" name="description" id="description"></textarea>
</label>

ASSIGNED TO: Egy legördülő lista, ahol az admin kiválaszthatja, hogy melyik hozzárendelt személy felelős a feladatért.
A legördülő lista a következő a kódban:

<select class="border-2 border-black rounded-md" name="assigned_to" id="assigned_to">
    <?php foreach($model as $item) : ?>
        <option value="<?= $item ?>"><?= $item ?></option>
<?php endforeach; ?>
</select>

Due Date (határidő): Egy dátumválasztó mező, amelyben kiválasztható az admin számára a feladat határideje.
Ez a következő a kódban:

<label for="due_date" class="text-2xl flex flex-col">DUE DATE:
    <input class="border-2 border-black rounded-md pl-2" id="due_date"  name="due_date" type="date" >
</label>

Leírás (Description): Egy nagyobb szövegmező, ahol részletes leírás adható meg a feladatról.
Ez a következő rész a kódban:

<label for="description" class="text-2xl flex flex-col">DESCRIPTION:
    <textarea class="border-2 border-black rounded-md pl-2" name="description" id="description"></textarea>
</label>

Mindez alatt látható egy "SAVE" feliratú gomb, amelyet az admin nyomhat meg az űrlapon megadott adatok elküldéséhez és mentéséhez.
Ez a kövtekező a kódban:

<input class="bg-green-300 p-2 cursor-pointer border-2 border-black rounded hover:bg-green-500" type="submit" value="SAVE">

### IX.

	A dashboard.view.php kódról:
Ebben a kódban egy adminisztrációs felületet valósítottunk meg, amely a feladatok(chorok) kezelésére és csoporttagok hozzáadására/eltávolítására szolgál.
<!-- CONTAINER START -->
<div class=" border-8 border-black mt-4 rounded-md"> 

Ez a kódrészlet egy „box”-ot hoz létre a weboldalon, amelynek fekete kerete van, enyhén lekerekített sarkokkal.
<!-- BUTTONS DIV START   -->

A weboldal felső részén látható Gombok: ( CREATE CHORE + , ADD MEMBER +, REMOVE MEMBER -)
A "CREATE CHORE" (feladat létrehozása) feliratú hivatkozás egy (link), amely egy új chore(új feladat) létrehozását teszi lehetővé.
Az alábbi a kódban: 

 <a class="flex p-2 m-2 border-4 border-black items-center gap-4 bg-green-300 hover:bg-green-500 max-w-[220px] text-3xl rounded-md mb-2 group " href="create_chore.php">CREATE CHORE<span class="text-5xl">+</span>  </a>

Az "ADD MEMBER"( tag hozzáadása) feliratú gomb, amely mellett egy plusz jel (+) látható. Ez a gomb arra szolgál, hogy új tagokat lehessen hozzáadni.   
Az "Add Member" opció segítségével az admin könnyedén hozzáadhat új tagokat a rendszerhez, akik ezután részt vehetnek a feladatok végrehajtásában és a háztartás szervezésében.

Ez a rész a kódban:

<button class="flex p-2 m-2 border-4 border-black items-center gap-4 bg-green-300 hover:bg-green-500 max-w-[220px] text-3xl rounded-md mb-2 group disabled:bg-gray-500" <?php if($model5 == false){echo 'disabled';} ?>  id="add_new_member_btn">ADD MEMBER <span class="text-5xl" >+</span></button>

A "REMOVE MEMBER" feliratú gomb, amely mellett egy mínusz jel (-) látható. Ez a gomb arra szolgál, hogy a tagokat( member) el lehessen távolítani.
A kitörlő funkcióval csak az email címet kell beírnunk és törölhetjük.
Ez a részlet alábbi a kódban:

<button class="flex p-2 m-2 border-4 border-black items-center gap-4 bg-red-300 hover:bg-red-500 max-w-[220px] text-3xl rounded-md mb-2 group "  id="remove_member_btn">REMOVE MEMBER <span class="text-5xl" >-</span></button>
<!-- GROUP MEMBERS DIV START -->
Ebben a kódrészben egy olyan keretet és struktúrát definiáltunk, amely a csoporttagokat jeleníti meg. 
A a kód az alábbiakat tartalmazza:
Egy címet ("Group members:") a csoporttagok listájának címzésére.
Ez az alábbi kódrészlet:

<h2 class="m-2 static top-0 left-0 text-2xl">Group members:</h2>

Valamint két alcímet: az egyik a felhasználókat ("Admins:") a másik pedig a csoporttagokat ("Members:") jelzi.
Ez a követekező a kódban:
Az "Admins:" alcím:

<h3 class="text-2xl">Admins:</h3>

A "Members:" alcím:

<h3 class="text-2xl">Members:</h3>

A "text-2xl" azonosító a szöveg méretét állítja be a weboldalon.
Egy fő keretet, amelyben a csoporttagok listája található. 
Ez  a következő a kódban:

<div class="flex gap-2 border-4 border-black rounded-md m-2 relative"> 

Az felhasználók listáját tartalmazó rész, amiben minden felhasználó nevet, egy-egy <p> elembe ágyaztunk be.

(<div class="m-2 border-2 border-black p-2 flex flex-col ">
    <h3 class=" text-2xl">Admins:</h3>
    <?php foreach($model3 as $item) : ?>
        <div class="">
            <p class="text-xl"> <?= $item  ?> </p>
        </div>
    <?php endforeach; ?>
</div>)

A csoporttagok listáját tartalmazó rész, ahol minden csoporttag neve egy-egy <p> elembe ágyaztunk be. Ez a lista  "flex-wrap" osztálynak köszönhetően vízszintesen rugalmasan illeszkedik a rendelkezésre álló helyhez, és szükség esetén több sorba is helyezi a csoporttagok neveit.
ez az alábbi a kód részlet:

<div class="m-2 border-2 border-black p-2 flex flex-wrap">
    <h3 class="text-2xl">Members:</h3>
    <?php foreach($model2 as $item) : ?>          
        <div class="min-w-[80px] mx-2">
            <p class="text-xl"> <?= $item  ?> </p>
        </div>
    <?php endforeach; ?>
</div>
<!-- ADD MEMBER DIALOG -->

Ebben a kódrészletben egy dialógusablakot(felugró ablakot) definiáltunk az új felhasználó hozzáadásához. Ha az ADD MEMBERS + gombra kattintunk a weboldalon akkor felugrik egy dialógusablak, ahol a Name (Név) az E-MAIL, és a Password(jelszó) látható, valamint az ADMIN-t lehet megjelölni. A dialógusablak tartalmazza a felhasználó nevének, e-mail címének és jelszavának megadásához szükséges űrlapot, valamint egy gombot a hozzáadás( ADD ) végrehajtásához. Emellett tartalmaz egy bezáró gombot is a dialógusablak bezárásához. Amikor a felhasználó az űrlap elküldése gombra kattint, az adatok POST kéréssel lesznek elküldve a szervernek az új felhasználó létrehozásához.
A kód részletezve:
A dialógusablak (felugró ablak) elem

<dialog id="add_member_dialog" class="border-4 border-black relative rounded-md">

Az id attribútum segítségével azonosítható, a class attribútum pedig stílust ad hozzá a dialógus ablakhoz.
A kódban szereplő, X ami a dialógusablak bezárására szolgál. 

<button id="close_add_member_modal" class="absolute top-1 left-1 font-3xl border-2 border-black p-1 hover:bg-red-300 rounded-sm" >X</button>

Ezzel a HTML kóddal egy űrlapot definiáltunk és formáztunk meg. Amikor a weboldal betöltődik  a böngésző az űrlapot megjeleníti a felhasználónak a meghatározott stílusokkal együtt.

<form class="flex flex-col border border-green-300 items-end gap-3 p-3" method="POST">

method="POST"
Amikor a felhasználó kitölti az űrlapot, és elküldi azt, az űrlap adatai a HTTP kérés testében (azaz a HTTP kérés body-jában) küldődnek el a szervernek. A felhasználó által bevitt adatok nem jelennek meg a böngésző címmezőjében, és nem láthatók közvetlenül a URL-ben, mint a GET kérés esetén.
Itt az űrlapon egy olyan mezőt definiáltunk, ami a felhasználónak lehetőséget ad a nevének megadására.

<label for="new_user_name">NAME:
            <input required class="border border-black pl-1 rounded-md" id="new_user_name" name="new_user_name" type="text">
        </label>

Ebben a JavaScript kód részletben, egy interaktív felhasználói felületet készítettünk a weboldalon,amely néhány fontos tevékenységet végrehajt, amik segítenek az oldal működésében:

<script>
    const add_new_member_btn = document.getElementById('add_new_member_btn');
    const add_new_member_btn_submit = document.getElementById('add_new_member_btn_submit');
    const add_member_dialog = document.getElementById('add_member_dialog');
    const close_add_member_modal = document.getElementById('close_add_member_modal');
    const close_delete_member_modal = document.getElementById('close_delete_member_modal');
    const delete_member_dialog = document.getElementById('delete_member_dialog');
    const remove_member_btn = document.getElementById('remove_member_btn');
    add_new_member_btn.addEventListener('click',() => openModal(add_member_dialog));
    close_add_member_modal.addEventListener('click',() => closeModal(add_member_dialog));
    add_new_member_btn_submit.addEventListener('click',() => closeModal(add_member_dialog));
    remove_member_btn.addEventListener('click',() => openModal(delete_member_dialog));
    close_delete_member_modal.addEventListener('click', () => closeModal(delete_member_dialog));

    function openModal(modal){
        modal.showModal();
    }
    function closeModal(modal){
        modal.close();
    }
</script>
                 
A kódban az addEventListener függvényt használtuk, hogy különböző eseményekre reagáljon, például a gombokra való kattintásra. Az add_new_member_btn gombra kattintva megnyitja az "add_member_dialog" dialógusablakot, ahol új tagokat lehet hozzáadni a csoportba. A REMOVE MEMBER gomb pedig megnyitja a "delete_member_dialog" dialógusablakot, amelyben a csoportból való tageltávolítást lehet elvégezni.
Dialógusablakok megnyitása és bezárása: A openModal és closeModal függvények segítségével megnyitja és bezárja a dialógusablakokat, amelyek az új tag hozzáadását és a tag eltávolítását végzik. Amikor az egyik gombra kattintanak, az azonosítójuk alapján kiválasztja a megfelelő dialógusablakot, majd megnyitja azt vagy bezárja.
Ez a kódrészlet az interaktivitást biztosítja az adminisztrátorok számára az oldalon, lehetővé téve számukra az új tagok hozzáadását és eltávolítását a csoportból, valamint az interaktív dialógusablakok használatát a felhasználói élmény javítása érdekében.

### Backend

A backend mint a frontend PHP-ben készült.
Az adatok tárolásához MySQL-t használtunk.
Az adatbázishoz PDO-val csatlakozunk.
Az adatbázis elérési útvonalát, felhasználóját és
jelszavát az app/config.php tárolja.
A hosting szolgáltató az infinityfree.com
A használt webszerver az Apache.

A telepítés lépései:
• fájlok feltöltése a htdocs mappába(file manager,FTB)
• adatbázis létrehozása
• adatbázis elérési útvonalának, felhasználónevének és jelszavának rögzítése az
app/config.php fájlba
• Az alkalmazáson belül SEUP menüpontban piros gomb megnyomása
Ezt követően a config.php ban megadott adatbázisban
létrejönnek a szükséges táblák:
chores, comments, groups, users
Az alkalmazás most már működik.

Adatok(Model)
Az adatbázis eléréséhez(CRUD)
az app/data/data.class.php ban található Data osztályt
használjuk. Ez az osztály úgy lett kialakítva, hogy akár
a PDO akár a mysql lecserélhető legyen összhangban
a polimorfizmus irányelvével, valamint az absztrakció

elvével( a Data class csak a MySQLDataProvider metódusait
hívja, de ha egy másik osztályt írunk, ami pl. MongoDB-t használ, azzal is
működni fog)

A MySQLDataProvider “prepared statement”-eket használ a
biztonság érdekében(MySQL injection prevention)
Amikor adatokat olvasunk be a 4 táblából(chores, comments, groups, users)
azokat osztályokba “csomagolva” kérjük, hogy könnyebben kezelhetők
legyenek.

Irányítók(Controller)
Minden .view.php(View) egy controller által kerül betöltésre.
A controller tartalmazza a logikát, fér hozzá az adatbázishoz ,
a view pedig megjeleníti a felületet a felhasználónak.
Minden controller először betölti a funkciókat és
a szükséges osztályokat, elvégzi a logikai lépéseket
majd megjeleníti a felületet.

Felhasznló beléptetése
A felhasználói email és jelszavakat(és minden user inputot)
filterezünk és a queryket prepared staementekkel hajtjuk végre.
A belépést követően “session”-ökkel biztosítjuk, hogy a felhasználó
folyamatosan “belépve maradjon”.

## Tesztelés

A tesztelés célja, az hogy részletesen átnézzük, pontosan mik az adott funkciók pontos reakciói. Ezen dokumentáció során szeretnénk erről egy részletes képet adni.
Mivel ez egy iskolai projekt, a domain ami kiszolgáltatja az oldalt, egy ingyenes szolgáltatás. A funkciók úgy működnek, mint amikor lokálisan vannak a forrásfájlok tárolva. 
A következőkben a különböző funkciókról szeretnénk részletesen írni.

Az applikáció URL-je:
http://chorestracker.infinityfreeapp.com/chores_tracker/

Itt a fő cél az, hogy az applikáció sikeresen megnyílik egy webböngészőben. Az eredmény az, hogy böngésző mivoltától függetlenül megnyílik az oldal. Kipróbáltuk Google Chrome-ban (ez volt az elsődleges böngésző), Microsoft EDGE-ben és Mozilla Firefox-ban ezetúl Android-om is Google Chrome-ban. Az említett platformokon elfogadható sebességgel megnyílik az applikácó. Ezen eredmények a további tesztesetekre is jellemzőek.

Amikor a SIGN UP oldalra lépünk, egyértelműen a felhasználó dokumentációban is részletezett lehetőségek tárulnak elénk. A név szempontjából nincs szigorú megkötés, a jelszó szempontjából sem(ezt lehet a későbbiekben szigorítani), viszont az email címnél fontos, hogy a formátuma a bevitt email címnek megfelelő legyen, különben sikeresen megkapjuk a várt felszólítást, hogy az email címnek @ karaktert kell tartalmaznia.
	
A LOGIN oldalesetében szintén az email formátuma egy fontos eset, amire figyelni kell, hogy nem megfelelő és természetesen nem regisztrált email cím és jelszó nem kerül elfogadásra. Itt különbséget kell tenni a helytelen email cím esetében: 
„Please enter a valid email address” -  amikor az email formátuma nem megfelelő 
“The provided credentials are not correct” – amikor a formátuma az email címnek megfelelő, de nem egyeznek az adok regisztrált értékekkel.
A továbbiakban nézzük meg az adminként beregisztrált felület eredményeit. (DASHBOARD)

A az első fontos eredmény az ADMIN-ok és MEMBER-ek esetében kell meghatároznunk, méghozzá az adminok és felhasználók számának behatárolása. Két admin után a lehetőség újabb admin hozzáadására sikeresen megszűnik. A felhasználók esetében (MEMBER) ez a szám kilenc után szűnik meg, ez után nem lehetséges további tagokat hozzáadni. (az ADD MEMBER és értelemszerűen a REMOVE MEMBER gombokkal).

Az ALL CHORES szekcióban  láthatjuk  megjelent regisztrált feladatok eredményeit. Ezekről részletesebben  egy későbbi bekezdésben írnánk.
A következők ben a CREATE CHORE oldalról szeretnénk írni. Itt szabadon tudunk megadni adatokat egy bizonyos feladatról, cím is opcionális, bár logikus megadni, az email cím csak a meglévők közül lehetséges és határidő és leírás sem fontos, hogy meg legyen adva. Amint elmentettük teljesen lehet a részleteket adminként változtatni ez nagyon előnyös az admin szempontjából, viszont a megbízott szempontjából kevésbé. Itt végül is a cél a fontos, mindkét fél számára fontos, hogy jó legyen a kommunikáció, de mégis ad egy flexibilis mozgásteret.
	
Itt ragadnánk meg az alkalmat, hogy írjunk a  meglévő feladatok részleteinek eseteiről.
Az EDIT CHORE oldalon megmarada a flexibilitás a feladat részleteinek módosítására és a COMMENTS szekció teret ad egy részletes folyamat  és kommunikáció dokumentálására ez alapján lehet a későbbiekben információt gyűjteni és tanulni egy feladat egyszerűbbé tételéről.
	
A továbbiakban nézzük meg a MEMBER jogosultság esetleges kevésbé flexibilis helyzetét.
	A MEMBER DASBOARDON egy kicsit átláthatóbbak a feladatok, mivel itt kettéoszlik meglévő és elvégzett feladatokra. Ez azért lehet előnyös a megbízott számára, mert az ADMIN abból indul ki, hogy a megbízott igenis foglalkozik a rábízott feladatokkal és az elvégzett feladatok listáját elkülönítve láthatja.

	A MEMBER EDIT CHORE oldalán logikusan  van módosíthatóvá téve a meglévő részletek listája, és a részletes és flexibilis kommunikáció  megbízott oldalról is kitűnően lehetséges. Ami a hozzászólások(COMMENT) számát illeti nincs limit amennyi az adatbázisban elfér, lehetséges..

Ami még a kijekentjkezét illeti, egyszerű LOGOUT gombbal van erre lehetőség és ezután akár ADMIN akár MEMBER, megfelelően működik és újra authentikációt és belépést igényel ha ezt az opciót választjuk. 
Utolsó témáink egyike lenne a még a további statikus oldalak megjelenítése, névszerint:
ABOUT, CONTACT, TERMS OF USE és PRIVACY POLICY. Ezek informatív fukcióikat töltik be sikeresen.
Még egy paragrafusban a SETUPról írnánk egy kicsit:
Ez sikeresen teszi lehetővé a továbbfeljesztést, mivel lokálisan van ennek az oldalnak funkciója, ezáltal könnyen létrehozhatjuk az adatbázisunkat localhost-on.
Legutolsó sorban a reszponzívitásról írnánk, igyekeztünk minden oldalon a lehető legjobban láthatóvá tenni a legalább 340px szélességnél is az oldal tartalmát.

## Felhasználói dokumentáció

A Chorestracker egy olyan szoftver, amely célja, hogy megkönnyítse a házimunkával kapcsolatos szervezési problémákat a család számára. 
Ennek érdekében lehetőséget biztosít arra, hogy egy megbízott személy felügyelje és koordinálja a feladatokat. Természetesen ez a jog az anyát illeti meg, aki általában a háztartás szervezője.
A regisztráció során az admin jogosultságot kap, amely lehetővé teszi számára, hogy további tagokat hozzon létre és kezeljen. 
Ez lehetővé teszi számára, hogy hatékonyan oszthassa szét a feladatokat és delegálja a felelősségeket a családtagok között.
Az applikáció angol nyelven íródott, ez a dokumentáció igyekszik részletesen bemutatni a funkciókat a felhasználó számára és ezen fejezet elolvasása megmagyarázza az össze funkciót magyar nyelven.
Kétféle felhasználó lehetséges az alkalmazásban, a kiterjesztett jogokkal rendelkező, továbbiakban ADMIN és az általános jogokkal rendelkező MEMBER.

Az applikáció megnyitása a következő internetes linken érhető el és a Landing Page/Főoldal
-ra vezet:
http://chorestracker.infinityfreeapp.com/chores_tracker/

Landing Page/Főoldal:
A főoldalon több lehetőség tárul elénk, itt a két legfontosabb a LOGIN (bejelentkezés) és SIGN UP(regisztráció) gombok. Ezekről később többet.
Ezentúl az ABOUT/ABOUT US (rólunk) gomb elvezet egy információs lapra a fejlesztőkről. A CONTACT(kapcsolat) gomb elvezet egy oldalra ami további információt ad a fejlesztők elérhetőségéről (jelnleg ez az iskolánk címét mutatja az iskolai email címekre, mivel egy ez iskolai vizsgaprojekt).
A TERMS AND CONDITIONS és PRIVACY POLICY (Felhasználási feltételek/adatvédelem) is fontos az oldal számára, ha élő környezetben használjuk(jelenleg csak példaként szolgál).
A SETUP gomb a fejlesztőknek fontos, felhasználói szempontból, nem jelentős, kérjük ezt a gombot ne használják, a megfelelő feltételek nélkül nem működőképes.
Visszatérés a főoldalra a ’ChoresTracker’ logó ikonjára való kattintással lehetséges.

SIGN UP(regisztráció)
Ha az oldadon a felhasználó a SIGN UP gombra kattint, akkor egy űrlap jelenik meg számára, ahol meg kell adni a Nevet (Name), az Email címét (Email) és a jelszavát kétszer (másodszor megerősítésként), valamint az elküldés (Submit) gombra kattintva elküldheti a regisztrációt. 
Ezen az oldalon szükséges a megfelelő email cím formátumot használni, különben a felhasználó kap egy hibaüzenetet és egy felszólítást helyes email cím formátum használatára (nev@domain.hu).
A jeszó kétszeri megadása  gépelési hibák elkerülése végett szükséges. 
Ezután a SUBMIT(beküldés) gomb megnyomásával lehet a regisztrációt elküldeni/megerősíteni.
A további lépések csak sikeres regisztráció során lehetségesek. Fontos megjegyezni, hogy az új profil létrehozása automatikusan ADMIN jogosultságot ad a felhasználónak.
A sikeres regisztráció utan az ADMIN átkerül a bejelentkezési oldalra(LOGIN).

LOGIN(bejelentkezés)
A sikeres regisztráció után  lehetősége van az ADMIN-nak a bejelentkezésre.
Fontos megjegyezni, hogy a regisztrált email címmel (EMAIL) lehet belépni nem a megadott névvel. 
A megadott jelszó megjegyzése fontos, mert a továbbiakban ezzel lesz a felhasználó hitelesítve.
A MEMBER jogosultsgú felhasználók is tudják ezt az oldalt használni, mivel az ő profiljukat az ADMIN fogja létrehozni.

ADMIN DASHBOARD
Ezen az oldalon adatik meg a lehetőség a ház körüli feladatokkal kapcsolatos minden nemű művelet elvégzésére.
Az eddigi alapvető informatív gombon kívül megjelennek a fontos funkciók gombjai.
A legfontosabb az első gomb a CREATE CHORE (ház körűli feladat létrehozása). Itt van lehetőség arra, létrehozzunk egy feladatot.
Az ADD MEMBER gomb megnyomásával ugrik fel egy kis ablak ahol hozzá lehet adni legfeljebb egy társ ADMIN-t vagy maximum 9 tagot (MEMBER).
Fontos, hogy az ADMIN-nak kell megadni az új tagok belépési adatait. EMAIL NAME, PASSWORD(jhelszó) és ADMIN jog megadásával.
Természetesen lehetséges el is lehet távolítani a tagokat a REMOVE MEMBER gombbal és az érintett email cím megadásával.
A meglévő csoporttagok(Group Members) megjelenítése ezen az oldalon látható, továbbá a csoport aktuális és elvégzett feladatai.
Innen kétféle egyéni oldal érhető el. Az első a CHEATE CHORE(feladat létrehozása) és az EDIT(a meglévő feladat megtekintése és további műveletek elvégzése).

CREATE CHORE	
Kitöltendő sorok ezen az oldalon a következőek(elsőször is amit a bal oldalon látunk):
TITLE – ez a feladat megnevezése
ASSIGNED TO – az a tag akire rá lesz bízva a feladat
DUE DATE – az elvégzendő feladat határideje
DESCRIPTION - a feladat részletes leírása
A SAVE gombbal lehet a feladatot elmenteni és ezzel elküldeni a megbízottnak.
A BACK TO DASHBOARD gombbal léphetünk vissza az ADMIN főoldalára.

ADMIN EDIT(DETAILS)
Ezen lehet egy bizonyos CHORE-ral mindennemű adminisztrációt elvégezni.
Látható vagy változtatható adatok
TITLE – az adott neve a feladatnak, ezt itt már nem lehet megváltoztatni.
CREATION DATE – a feladat létrehozásának pontos időpontja, ez sem változtatható elem.
ASSIGNED TO – a megbízott, ezt átadható egy másik tagnak ha szükséges
DUE DATE – a határidő ez változtatható, természetesen indokoltan.
STATUS – alapértelmezetten not started(nem elkezdett)
	további státuszok: in progress(folyamatban), delay(késés), done(elkészült)
DESCRIPTION – ez a részletes leírás ami változtatható
Ez alatt a mentések változtatása lehetséges (SAVE CHANGES), továbbá itt lehet kitörölni a feladatot (DELETE CHORE)
COMMENT – ez az egyik fontos funkció, mivel itt lehet esetleges hozzászólásokat írni.
Ezek a hozzászóláksok a COMMENT-ben lesz látható.

MEMBER DASBOARD
Itt lehet a meglévő és elkészült feladatok megnézni MEMBER jogosultsággal.
MEMBER EDIT(DETAILS)
Ami itt különbség az adminhoz képest az hogy bizonyos mezők nem változtathatóak:
DUE DATE(határidő), DESCRIPTION(leírás), 
Ami lehetséges:
STATUS változtatása
COMMENT hozzáadása
SAVE CHANGES(változtatások mentése) is lehetséges.

LOGOUT
Az oldal elhagyása előtt természetesen fontos lépés kijelentkezni.


Hasznos időtöltést kívánunk a ChoresTracker használata során!


## Összefoglalás

Összefoglalásként szeretnénk írni tapasztalaltainkról a fejleszést kitevő előző pár hónapban. Mint első közös projektkünk sok új élmény ért minket. Természetesen sok akadály került elénk és sok olyan megoldást kívánó részfeladat ami sok munkát és újragondolást vett igénybe. 
Többször kellt újragonodolnuk a projektet menet közben, valalmilyen szinten újrakezdeni. A tervezés a Figma szolgáltatás segítségével készült, nyilván a végső megvalósításban születtek máshogy kinéző megoldások. A folyatás a HTML CSS és Javasscipt segítségével egy idő után kicsit követhetetlenné tette a folyamatokat.
Amikor elkezdtük áltültetni PHP-ba a projektet elsőzör a technológi megismerése jelentette a nagy kihívást ezentúl a Talilwind CCS is egy újdonság volt, őszintén szólva kissé összezavaró amikor az ismert CSS elemeket is igyekezni kellett a könyvtár szabályai szerint értelmezni.
Továbbá teljes mértékben állythatjuk, hogy sokat tanultunk a fejlesztési folyamat során bár nem eleget, természetesen nem kizárt, hogy a későbbiekben igyekszünk az eredetileg eklképzelt funkciókat megvalósítani akár közösen is. Az itt szerzett tapasztalat hasznos lesz későbbi projekteink esetében is. 
Az sem véletlen, hogy az applikáció angol nyelven íródott, hiszen akármilyen projekt amelely angolul kerül közzétételre, nagyobb számú közönséget tud megszólítani. Itt ismét említeném a multinacionális IT cégeket, ott elképzelhetetlen, hogy egy szoftverfejlesztőnek ne kelljen közös munkát végezni más nemzetisélghez tartozó kollégákkal.
Csapatunk tagjainak többynire ezen szempontokat tartják szem előtt a jövőben elképzelt „álommunkávát”-t tekintve is.
