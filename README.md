# La Mola TV — Calendari d'events

Signage digital per a la televisió del box de CrossFit La Mola. Mostra el calendari d'events en rotació automàtica amb 3 variants estètiques.

---

## 📺 Què hi ha

| Fitxer | Què fa |
|---|---|
| `index.html` | La pantalla de la TV. Obrir en pantalla completa al navegador. |
| `admin.html` | Panell per afegir, editar, eliminar events des de qualsevol navegador. |
| `events.json` | Font de dades. Aquí viuen tots els events. |
| `assets/` | Imatges i logos. Afegeix-hi noves imatges si cal. |

---

## 🚀 Posada en marxa (primer cop)

### 1. Crear el repositori a GitHub

1. Vés a [github.com/new](https://github.com/new)
2. Nom del repo: `lamola-tv` (o el que vulguis)
3. Visibilitat: **Public** (necessari per a GitHub Pages gratuït)
4. Crea'l sense README

### 2. Pujar els fitxers

**Opció A — via web (fàcil):**
1. Al repo buit, clica "uploading an existing file"
2. Arrossega `index.html`, `admin.html`, `events.json` i la carpeta `assets/` sencera
3. Commit changes

**Opció B — via git (si ja en saps):**
```bash
git clone https://github.com/TUUSUARI/lamola-tv.git
cd lamola-tv
# copia tot el contingut d'aquesta carpeta aquí
git add .
git commit -m "Primera versió"
git push
```

### 3. Activar GitHub Pages

1. Al repo → **Settings** → **Pages** (menú esquerre)
2. Source: **Deploy from a branch**
3. Branch: `main` · Folder: `/ (root)` → **Save**
4. Espera 1-2 minuts
5. Et donarà una URL tipus: `https://TUUSUARI.github.io/lamola-tv/`

### 4. Obrir a la TV

1. Obre el navegador de la TV (Chrome, Firefox, TV Bro a Android TV, etc.)
2. Vés a la URL de dalt
3. F11 o gest del navegador → pantalla completa
4. Opcional: guarda-ho com a pàgina d'inici / marcador ràpid

**Tecles a la TV:**
- `→` / espai: següent event · `←`: anterior
- `1` / `2` / `3`: canviar variant estètica

---

## ✏️ Administrar events

Obre `https://TUUSUARI.github.io/lamola-tv/admin.html` a qualsevol navegador (mòbil, ordinador, tauleta).

### Afegir un event
1. Clica **+ Afegir event**
2. Omple els camps (dates, títol, descripció, imatge…)
3. Clica **Publicar a GitHub** (primera vegada, configura el token — veure baix)
4. En ~1 minut la TV ja ho mostra

### Editar un event existent
1. Clica sobre la capçalera de l'event
2. Edita qualsevol camp
3. Els canvis es desen automàticament com a esborrany al navegador
4. **Publicar a GitHub** quan estiguin llestos

### Eliminar events passats
Clica **Netejar passats**. Elimina tots els events amb data final anterior a avui.

> 💡 **Nota**: els events passats també s'**amaguen automàticament** a la TV encara que no els esborris — així no cal netejar sovint.

### Descàrrega manual (alternativa a "Publicar")
Si no vols usar el token de GitHub, pots:
1. Clicar **Descarregar JSON** → et baixa `events.json`
2. Al repo de GitHub: `events.json` → ✏️ edit → substituir tot el contingut → commit
3. O drag & drop del fitxer dins del repo per sobreescriure

---

## 🔑 Configurar token de GitHub (només primer cop)

El token permet publicar des de l'admin automàticament. Es guarda **només al teu navegador** (localStorage). Mai surt d'aquí.

### Crear el token
1. Obre [github.com/settings/tokens/new](https://github.com/settings/tokens/new?scopes=repo&description=La%20Mola%20TV) (ja ve preconfigurat)
2. **Expiration**: tria "No expiration" per al màxim confort, o una data si prefereixes
3. Verifica que **repo** està marcat (dona permís per escriure al repo)
4. Clica **Generate token** al final
5. Copia el token (només es mostra un cop, tipus `ghp_xxxxx`)

### Configurar-lo a l'admin
1. A admin.html, clica **Publicar a GitHub**
2. Omple:
   - **Repositori**: `usuari/lamola-tv` (substitueix `usuari`)
   - **Branca**: `main`
   - **Token**: enganxa el token
3. **Desar i publicar**

> A partir d'ara, només has de clicar "Publicar a GitHub" i els canvis van directes al repo.

---

## 🖼️ Canviar imatges

### Opció A — substituir una imatge existent
1. Vés al repo a la carpeta `assets/`
2. Clica la imatge actual → **...** (dalt a la dreta) → **Delete file** → Commit
3. **Add file** → **Upload files** → puja la nova imatge **amb el mateix nom** → Commit

### Opció B — afegir una imatge nova
1. Puja la nova imatge a `assets/` (qualsevol nom, ex: `summer-2027.jpg`)
2. A admin.html, al camp **Imatge** de l'event, escriu: `assets/summer-2027.jpg`
3. Publicar

> 💡 **Mida recomanada**: mínim 1920×1080 px, format `.jpg`. Optimitza abans de pujar (≤ 500 KB per imatge) per no alentir la TV.

---

## 🎨 Canviar la variant estètica

La TV té 3 variants:
- **A — Refinat** (l'actual, tipografia editorial amb grans números)
- **B — Editorial/Magazine** (imatge gran al costat + text a la dreta)
- **C — Minimalista Apple TV** (centrat, molt espai)

Com canviar la variant per defecte:
1. A la TV, activa el mode tweaks (al toolbar superior del navegador si estàs a la preview, o tecles **1/2/3**)
2. La preferència es desa al navegador de la TV

> Per canviar-ho per defecte a tots, cal editar `index.html` (cerca `TWEAK_DEFAULS` a dalt del fitxer).

---

## 📐 Format dels events (events.json)

Cada event és un objecte amb aquests camps:

| Camp | Tipus | Obligatori | Exemple |
|---|---|---|---|
| `id` | string | sí | `"summer"` |
| `startDate` | `AAAA-MM-DD` | sí | `"2026-07-04"` |
| `endDate` | `AAAA-MM-DD` | sí | `"2026-07-04"` |
| `kicker` | string | sí | `"Competició interna · CrossFit La Mola."` |
| `num` | string | sí | `"4"` o `"9–10"` |
| `numRng` | bool | no | `true` si és rang |
| `mes` | string | sí | `"Juliol"` o `"Oct-Nov"` |
| `month` | `01`–`12` | sí | `"07"` |
| `title` | string (HTML) | sí | `"La Mola.<br><em class=\"serif\">Summer Fest</em>"` |
| `titleShort` | string | sí | `"La Mola. Summer Fest"` |
| `lede` | string | sí | paràgraf descriptiu |
| `pill` | string | sí | `"Places limitades"` |
| `pillKind` | `free`\|`interior`\|`exterior`\|`star` | sí | `"star"` |
| `rows` | array `{k,v}` | sí | `[{"k":"On","v":"Platja"}]` |
| `media` | string | sí | `"assets/nom.jpg"` |
| `sbSub` | string | no | subtítol al sidebar |
| `isHero` | bool | no | `true` = Save the date destacat (fons fosc) |

> L'admin s'encarrega de totes aquestes opcions — **no cal editar el JSON a mà**.

---

## 🔧 Resolució de problemes

**La TV mostra "No s'ha pogut carregar els events"**
- Comprova que `events.json` està a l'arrel del repo
- Comprova que el JSON és vàlid (admin.html t'ho valida automàticament)
- Refresca la pàgina a la TV (F5 o recarregar)

**Els canvis de l'admin no apareixen a la TV**
- GitHub Pages triga ~1 min a actualitzar-se
- Refresca la pàgina de la TV (els navegadors poden cachejar)
- Afegeix `?v=2` a la URL per forçar recàrrega

**Publicar a GitHub dona error 401**
- El token ha caducat → regenera'l i torna'l a configurar

**Publicar a GitHub dona error 404**
- El nom del repositori és incorrecte (ha de ser `usuari/repo`, no la URL)
- El token no té permisos `repo`

**Una imatge no es veu a la TV**
- Verifica que el nom del fitxer coincideix exactament (majúscules/minúscules importen)
- La ruta al camp `media` ha de ser relativa: `assets/nom.jpg` (no `/assets/nom.jpg`)

---

## 📂 Estructura del repo

```
lamola-tv/
├── index.html          ← la TV
├── admin.html          ← panell d'administració
├── events.json         ← dades dels events
├── README.md           ← aquest document
└── assets/
    ├── community-*.jpg
    ├── hero-*.jpg
    ├── detail-*.jpg
    ├── logo-full.png
    └── logo-short.png
```

---

## 💬 Dubtes?

Aquesta és una web 100% estàtica — no hi ha servidor, no hi ha base de dades, no hi ha costos. Tot viu al repo de GitHub, i GitHub Pages ho serveix gratis.
