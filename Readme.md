# Entwickler KFT. – weboldal

```text
█████  █   █  █████  █   █  ███   ████  █   █  █      █████  ████
█      ██  █    █    █   █   █   █      █  █   █      █      █   █
████   █ █ █    █    █ █ █   █   █      ███    █      ████   ████
█      █  ██    █    ██ ██   █   █      █  █   █      █      █  █
█████  █   █    █    █   █  ███   ████  █   █  █████  █████  █   █

█   █  █████  █████
█  █   █        █
███    ████     █         ─────────────────────────────────────────
█  █   █        █          Generálkivitelezés · Könnyűszerkezetes
█   █  █        █    ██    házak · Szakipari munkák
                          ─────────────────────────────────────────
                                              „Építjük a Jövőt”
```

Az Entwickler KFT. (generálkivitelezés, könnyűszerkezetes házak, szakipari munkák) bemutatkozó weboldala.

Tiszta, statikus HTML/CSS/JavaScript oldal: **nincs build lépés, nincs függőség, nincs szerver oldali kód**. Bármelyik böngészőben megnyitható, és bármilyen statikus tárhelyre (pl. GitHub Pages) feltölthető.

---

## Tartalom

- [Fájlszerkezet](#fájlszerkezet)
- [Helyi futtatás](#helyi-futtatás)
- [Az oldalak felépítése](#az-oldalak-felépítése)
- [Látványtervek kezelése](#látványtervek-kezelése)
- [Szövegek és elérhetőségek módosítása](#szövegek-és-elérhetőségek-módosítása)
- [Stílus és színek](#stílus-és-színek)
- [Reszponzív működés](#reszponzív-működés)
- [Git munkafolyamat](#git-munkafolyamat)
- [Közzététel](#közzététel)
- [Licenc](#licenc)

---

## Fájlszerkezet

```
entwickler_kft/
├── index.html               # Főoldal (egyoldalas, szekciókkal)
├── latvanytervek.html       # Külön Látványtervek galéria oldal
├── images/
│   └── latvanytervek/       # Ide kerülnek a saját látványterv képek
├── .vscode/launch.json      # VS Code: "Open index.html" indítási konfiguráció
├── Readme.md                # Ez a dokumentáció
├── JAVASLATOK.md            # Továbbfejlesztési javaslatok, teendők
└── LICENSE                  # Apache 2.0
```

A CSS és a JavaScript az egyes HTML fájlokon belül, `<style>` és `<script>` blokkban található.

Külső erőforrások (CDN-ről töltődnek):

| Erőforrás | Forrás | Mire kell |
|---|---|---|
| Montserrat, Open Sans betűtípus | Google Fonts | Címsorok és szövegtörzs |
| Font Awesome 6.4.0 | cdnjs.cloudflare.com | Ikonok (`fa-solid fa-...`) |
| Mintaképek | images.unsplash.com | Hero háttér és ideiglenes látványtervek |

---

## Helyi futtatás

Három lehetőség, a legegyszerűbbtől:

1. **Dupla kattintás** az `index.html` fájlra – megnyílik a böngészőben.
2. **VS Code:** *Run and Debug* (Ctrl+Shift+D) → **Open index.html**.
3. **Helyi szerver** (valósághűbb, a relatív linkek pontosan úgy működnek, mint élesben):
   ```bash
   # Python
   python -m http.server 8000
   # vagy Node.js
   npx serve .
   ```
   Majd: <http://localhost:8000>

**Telefonos nézet tesztelése:** böngészőben F12 → eszköz ikon (Ctrl+Shift+M) → válassz egy telefont (pl. iPhone 12, Galaxy S20).

---

## Az oldalak felépítése

### `index.html` – főoldal

A menüpontok a szekciók `id`-jára ugranak (`#kezdolap`, `#szolgaltatasok`, ...).

```text
┌──────────────────────────────────────────────────────────────┐
│  ☎ +36 30 ...   ✉ ...@gmail.com                  .top-bar    │
├──────────────────────────────────────────────────────────────┤
│  ENTWICKLER KFT.    Kezdőlap · Szolgáltatások · Látványtervek│
│                      · Rólunk · Kapcsolat         header     │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│                    ÉPÍTJÜK A JÖVŐT                           │
│              Prémium generálkivitelezés ...       #kezdolap  │
│                  [ KÉRJEN AJÁNLATOT ]                        │
│                                                              │
├──────────────────────────────────────────────────────────────┤
│                    Szolgáltatásaink          #szolgaltatasok │
│   ┌──────────┐      ┌──────────┐      ┌──────────┐           │
│   │ Generál- │      │ Könnyű-  │      │ Szakipari│           │
│   │ kivit.   │      │ szerkezet│      │ munkák   │           │
│   └──────────┘      └──────────┘      └──────────┘           │
├──────────────────────────────────────────────────────────────┤
│░░ LÁTVÁNYTERVEK ░░░░░░░░░░░░░░░░░░░░░░░░░░░ #latvanytervek ░░│
│░░ Tervtől a kulcsrakész otthonig        [ Összes terv → ] ░░░│
│░░ ┌───────────┬───────────┐ ░░ (sötét háttér, tervrajz-rács)░│
│░░ │    01     │    02     │ ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░│
│░░ └───────────┴───────────┘ ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░│
├──────────────────────────────────────────────────────────────┤
│                         Rólunk                      #rolunk  │
├──────────────────────────────────────────────────────────────┤
│                 Lépjen velünk kapcsolatba         #kapcsolat │
│   [ Kátai-Kis Anna ]   [ Kátai Ottó ]   [ E-mail ]           │
├──────────────────────────────────────────────────────────────┤
│  © 2026 Entwickler KFT.                            footer    │
└──────────────────────────────────────────────────────────────┘
```

| Sorrend | Szekció | `id` | CSS osztály |
|---|---|---|---|
| – | Felső info sáv (telefon, e-mail) | – | `.top-bar` |
| – | Fejléc + menü (rögzített, `sticky`) | – | `header`, `nav` |
| 1 | Hero („Építjük a Jövőt”) | `kezdolap` | `.hero` |
| 2 | Szolgáltatásaink (3 kártya) | `szolgaltatasok` | `.services-grid`, `.service-card` |
| 3 | Látványtervek (portfólió, bento rács) | `latvanytervek` | `.lt-section`, `.lt-grid`, `.lt-card` |
| 4 | Rólunk | `rolunk` | `.about-section` |
| 5 | Kapcsolat (3 kártya) | `kapcsolat` | `.contact-section`, `.contact-card` |
| – | Lábléc | – | `footer` |

### `latvanytervek.html` – galéria oldal

- Ugyanaz a fejléc és lábléc, mint a főoldalon; a menüpontok visszamutatnak az `index.html` szekcióira.
- A galériát JavaScript építi fel egy listából (lásd lent).
- Képre kattintva **nagyító nézet (lightbox)** nyílik: nyilakkal / ← → billentyűkkel lapozható, `Esc`-re vagy a háttérre kattintva bezárul.
- Amíg nincs feltöltött kép, 6 „Hamarosan” helyőrző kártya jelenik meg.

---

## Látványtervek kezelése

> ⚠️ A főoldali Látványtervek szekció jelenleg **ideiglenes Unsplash mintaképeket és kitalált adatokat** (pl. „180 m²”, „Budapest környéke”) tartalmaz. Élesítés előtt ezeket cserélni kell saját anyagra.

### 1. Képek előkészítése

- Formátum: `.jpg` vagy `.webp`
- Méret: kb. **1600 px** széles (a kiemelt kártyához), fájlméret lehetőleg **300 KB alatt**
- Fájlnév: kisbetű, ékezet és szóköz nélkül, pl. `csaladi-haz-godollo-1.jpg`
- Helye: `images/latvanytervek/`

### 2. Galéria oldal (`latvanytervek.html`)

Az oldal alján lévő `<script>` blokkban a `latvanytervek` listába kell felvenni egy sort képenként:

```js
const latvanytervek = [
    { src: 'images/latvanytervek/csaladi-haz-1.jpg', title: 'Családi ház', description: 'Könnyűszerkezetes, 140 m²' },
    { src: 'images/latvanytervek/nappali-1.jpg',     title: 'Nappali',     description: 'Belsőépítészeti terv' },
];
```

- `src` – a kép útvonala (kötelező)
- `title` – cím a kártyán és a nagyító nézetben
- `description` – rövid leírás (elhagyható)

Ha a lista nem üres, a helyőrzők automatikusan eltűnnek.

### 3. Főoldali szekció (`index.html`)

A főoldalon 4 kiemelt kártya van, ezek kézzel szerkesztett HTML-ek a `<section id="latvanytervek">` blokkban. Kártyánként ezeket kell átírni:

```html
<a href="latvanytervek.html" class="lt-card lt-card--featured">
    <img src="images/latvanytervek/csaladi-haz-1.jpg" alt="Családi ház látványterve" loading="lazy" onerror="this.remove()">
    ...
    <span class="lt-num">01</span>
    <div class="lt-info">
        <span class="lt-tag">Generálkivitelezés</span>      <!-- kategória címke -->
        <h3>Modern családi ház</h3>                        <!-- cím -->
        <div class="lt-meta">
            <span><i class="fa-solid fa-ruler-combined"></i>180 m²</span>
            <span><i class="fa-solid fa-location-dot"></i>Budapest környéke</span>
        </div>
    </div>
</a>
```

Kártyaméretek (asztali nézetben, 4 oszlopos rács):

| Osztály | Méret |
|---|---|
| `lt-card lt-card--featured` | 2 oszlop × 2 sor (nagy, kiemelt) |
| `lt-card lt-card--wide` | 2 oszlop × 1 sor (széles) |
| `lt-card` | 1 oszlop × 1 sor |

```text
 ASZTALI  (> 1024 px, 4 oszlop)          TABLET  (≤ 1024 px, 2 oszlop)

 ┌─────────────┬─────────────┐           ┌─────────────────┐
 │             │ 02  --wide  │           │                 │
 │ 01          ├──────┬──────┤           │ 01  --featured  │
 │ --featured  │  03  │  04  │           │                 │
 │             │      │      │           ├─────────────────┤
 └─────────────┴──────┴──────┘           │ 02  --wide      │
                                         ├────────┬────────┤
 TELEFON  (≤ 700 px, oldalra húzható)    │  03    │  04    │
                                         └────────┴────────┘
 ┌──────────────────┐┌──
 │                  ││
 │ 01               ││ 02    ← húzd →
 │                  ││
 └──────────────────┘└──
   ☝ Húzza oldalra a további tervekért
```

A jelenlegi elrendezés (1 featured + 1 wide + 2 normál) pontosan kitölti a 4×2-es rácsot. Ha több kártyát adsz hozzá, figyelj arra, hogy a sorok kiteljenek (pl. +4 normál kártya = egy újabb teljes sor).

Ha egy kép nem töltődik be, az `onerror="this.remove()"` eltávolítja, és a kártyán tervrajzmintás háttér marad – így nem jelenik meg „törött kép” ikon.

---

## Szövegek és elérhetőségek módosítása

A telefonszámok és az e-mail cím **több helyen** szerepelnek – módosításkor mindenhol cserélni kell:

| Adat | Hol található |
|---|---|
| Telefon, e-mail | `index.html` → `.top-bar` és `#kapcsolat` kártyák |
| Telefon, e-mail | `latvanytervek.html` → `.top-bar` |
| Lábléc szöveg, évszám | Mindkét fájl `<footer>` része |

Tipp: VS Code-ban **Ctrl+Shift+H** (keresés és csere az összes fájlban).

Telefonszám link formátuma: `href="tel:+36301234567"` (szóköz nélkül, országkóddal).

---

## Stílus és színek

A színek CSS változókban vannak megadva, mindkét HTML fájl `:root` blokkjában:

| Változó | Érték | Használat |
|---|---|---|
| `--primary-dark` | `#121E2A` | Felső sáv, lábléc, Látványtervek háttér |
| `--primary-blue` | `#1C3144` | Címsorok, logó, Kapcsolat háttér |
| `--accent-gold` | `#C59B6D` | Kiemelések, gombok, ikonok |
| `--accent-gold-hover` | `#A67D50` | Gomb hover |
| `--bg-light` | `#F4F6F8` | Oldal háttér |
| `--bg-white` | `#FFFFFF` | Kártyák, fejléc |

> A két HTML fájl külön-külön tartalmazza a közös stílusokat (fejléc, menü, lábléc, színek). **Ha a közös részen változtatsz, mindkét fájlban meg kell tenni.** (Lásd a [JAVASLATOK.md](JAVASLATOK.md) fájlt a közös CSS fájlba szervezésről.)

Betűtípusok: címsorok `Montserrat`, szövegtörzs `Open Sans`.

---

## Reszponzív működés

| Képernyő | Töréspont | Viselkedés |
|---|---|---|
| Asztali | > 1024 px | Teljes elrendezés, Látványtervek 4 oszlopos bento rács |
| Tablet | ≤ 1024 px | Látványtervek 2 oszlop, a szekció fejléc egymás alá kerül |
| Kisebb tablet / nagy telefon | ≤ 900 px | Fejléc: logó és menü egymás alatt, menü tördelve, kisebb hero cím |
| Telefon | ≤ 700 px | Látványtervek: oldalra húzható (swipe) kártyasor, 16 px oldalmargó, „Húzza oldalra” felirat |

---

## Git munkafolyamat

- Fő ág: `master`
- Új funkció külön ágon: `Feature/<Nev>` (pl. `Feature/Latvanyterv`)
- Kész munka → Pull Request a `master` ágba a GitHubon

```text
 master ──●──────────●─────────────────────●──────▶
           \                              /
            \  Feature/Latvanyterv       /  Pull Request
             ●──────●──────●──────●─────●   + review
           branch  commit commit commit
```

```bash
git checkout master
git pull
git checkout -b Feature/UjFunkcio
# ... módosítások ...
git add .
git commit -m "Rövid leírás a változásról"
git push -u origin Feature/UjFunkcio
```

---

## Közzététel

Mivel statikus oldal, a legegyszerűbb a **GitHub Pages**:

1. GitHub → a repó → **Settings → Pages**
2. *Source*: **Deploy from a branch**, ág: `master`, mappa: `/ (root)`
3. Mentés után pár perccel elérhető: `https://<felhasznalonev>.github.io/entwickler_kft/`
4. Saját domain (pl. `entwickler.hu`) ugyanitt, a *Custom domain* mezőben állítható be.

Alternatívák: Netlify, Vercel, Cloudflare Pages, vagy bármilyen hagyományos tárhely FTP-vel (a teljes mappát kell feltölteni).

---

## Licenc

[Apache License 2.0](LICENSE)
