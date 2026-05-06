# Instrukce pro projekt: Ohnivá žena — Astro + AstroPaper

## Účel projektu
Migrace webu https://ohnivazena.cz z WordPressu do statického generátoru **Astro** s šablonou **AstroPaper v5**. Web patří Janince **Živě** — průvodkyni ženskou spiritualitou, přírodou, obřady a přirozeným bytím.

---

## Struktura nové prezentace

Nová prezentace obsahuje tři hlavní stránky:

1. **Úvodní stránka** (`src/pages/index.astro`)
2. **Čím se zabývám** (`src/pages/cim-se-zabyvam.astro`)
3. **O mně — medailonek** (`src/pages/kdo-jsem.astro`)

Web neobsahuje blog ani žádné další stránky.

---

## Klíčový obsah a sdělení

### Úvodní stránka
- Obsahuje slogan/název: **„naraJana"**
- Hlavní motto: **„Pojďme žít sjednoceni se sebou, nalezením spojení se Zemí a Vesmírem."**
- Úvodní půlhodina konzultace je **zdarma** — tuto informaci vždy uvádět prominentně

### Logo / nápis „naraJana"

Nápis vychází z digitálního návrhu:
- Písmena **NARA** a **ANA** jsou velká, čistá, geometrická — styl **sans-serif** (ne serif, ne hand-lettered)
- Doporučený font: **Montserrat SemiBold** nebo **Raleway** (oba na Google Fonts); finální výběr k upřesnění — Janinka říká „písmo ještě není ONO"
- Středové **J** je vizuální dominanta: tenká svislá čára **bez příčky**, s velkou ozdobnou spodní smyčkou sestupující hluboko pod účaří — stylem odpovídá **malému písmenu j** zvětšenému na výšku celého nápisu
- Nad J je malé plné **srdíčko** (♥) ve stejné barvě, umístěné těsně nad svislou čárou
- Doporučený způsob implementace: **inline SVG** uložené jako `src/assets/narajana.svg`
- Barva nápisu: `--accent` (#d4620f) na světlém pozadí webu

### Zaměření Janinky
- **Magie Země:** obřady, spolupráce s přírodou, přírodní cykly, živly
- **Magie Vesmíru:** andělé, archandělé, nanebevzetí mistři, vesmírné energie
- **Šetrný přístup ke zdraví:** alternativy ke klasické medicíně, homeopatie, RAW výživa
- **Péče o děti:** individuální vzdělávání, domácí porody, přirozené rodičovství

Všechny texty musí tyto oblasti reflektovat — nepoužívat neutrální nebo korporátní jazyk, ale vřelý, spirituální tón v souladu s osobností Janinky.

### Reference a doporučení

Web nepoužívá komentáře ani diskuze. Vybraná svědectví jsou zakomponována **staticky** přímo do stránek.

**Na úvodní stránce** (`index.astro`) — tři krátká svědectví jako citáty, umístěná pod mottem nebo před CTA tlačítkem konzultace:

> „Spolupráce s Janinkou je skvělá. Hledala jsem východisko z komplikovaných vztahů s muži a našla. Cítím se svěže, svobodně, blíž své přirozenosti."
> — *Kristýna Magnusková*

> „Parádní spolupráce. Nádherné uvolnění. Hodinka utekla jako nic. Mám hned lepší den a věřím, že to tak bude už pořád."
> — *Ianete*

> „Plnohodnotné rady od úžasné ženy. Je úžasná žena, která umí vždy moudře poradit."
> — *Pavlína*

**Na stránce „Čím se zabývám"** (`cim-se-zabyvam.astro`) — jedno delší svědectví jako příběh, u sekce duchovní práce a obřadů:

> „Byl jsem čerstvě po rozchodu se svou nejmilovanější přítelkyní. Oslovil jsem Janinku. Probrala se mnou vztyčné body, šli jsme na věc. Byl úplněk a svátek Valentína. Cítil jsem hlubokou ztrátu a žal, který vyvrcholil ve vyhrknuté slzy — ale pak jsem se cítil lehce, svobodně. Jako kdybych se poprvé svobodně nadechl. Pokud máte jakýkoli problém, co vás oslabuje, nečekejte. Oslovte tuto skvělou ženu. Má informace přímo ze zdroje."
> — *Gabriel Angell*

Svědectví stylizovat jako blokové citáty (`<blockquote>`) s akcentní barvou (`--accent`) nebo jako karty s jemným pozadím (`--muted`).

---

## Technologický stack

- **Framework:** Astro (nejnovější stabilní verze)
- **Šablona:** AstroPaper v5 (pnpm create astro@latest --template satnaing/astro-paper)
- **Styling:** TailwindCSS (již součástí AstroPaper)
- **Správce balíčků:** pnpm
- **Jazyk obsahu:** česky (`lang: "cs"`, `timezone: "Europe/Prague"`)
- **Nasazení:** GitHub Pages

---

## Konfigurace webu (`src/config.ts`)

Vždy použij tato nastavení jako základ:

```ts
export const SITE = {
  website: "https://ohnivazena.cz/",
  author: "Janinka Živa",
  profile: "https://ohnivazena.cz/kdo-jsem/",
  desc: "Průvodkyně na cestě k přirozenosti ženy, přírodě a vědomí sebe.",
  title: "Ohnivá žena",
  ogImage: "og-ohnivazena.jpg",
  lightAndDarkMode: false,           // pouze světlý režim
  lang: "cs",
  timezone: "Europe/Prague",
} as const;
```

---

## Barevná paleta — oranžovobílá

Vždy použij tuto paletu v `src/styles/global.css`. **Nikdy nepoužívej výchozí modrou paletu AstroPaper.**

```css
:root,
html[data-theme="light"] {
  --background: #fffaf5;      /* teplá bílá */
  --foreground: #2d1f0e;      /* tmavě hnědá — čitelný text */
  --accent: #d4620f;          /* hluboká oranžová — odkazy, akcenty */
  --muted: #fde8d0;           /* světle broskvová — karty, hover */
  --border: #f5c99a;          /* zlatavě oranžová — orámování */
}
```

Tmavý režim je vypnutý (`lightAndDarkMode: false`). Pokud je přesto potřeba, použij:

```css
html[data-theme="dark"] {
  --background: #1c1007;
  --foreground: #f5e6d3;
  --accent: #f5901e;
  --muted: #3a2210;
  --border: #7a4010;
}
```

---

## Mandala na pozadí

SVG soubor `mandala-duha.svg` je umístěn v `public/mandala-duha.svg`.

Přidej mandalu jako fixní dekorativní pozadí do `src/layouts/Layout.astro` (nebo do hlavního layout souboru AstroPaper):

```astro
<!-- Mandala pozadí — vkládat těsně za <body> -->
<div
  aria-hidden="true"
  class="pointer-events-none fixed inset-0 z-0 flex items-center justify-center overflow-hidden"
>
  <img
    src="/mandala-duha.svg"
    alt=""
    width="700"
    height="700"
    class="h-[700px] w-[700px] opacity-[0.04] select-none"
    fetchpriority="low"
    loading="lazy"
  />
</div>
```

Pravidla pro mandalu:
- `opacity` vždy mezi `0.03` a `0.06` — jen jemný stín, nesmí rušit čitelnost
- `pointer-events-none` a `aria-hidden="true"` — nesmí ovlivnit přístupnost ani interakci
- `z-0` — vždy za veškerým obsahem
- pozice: vycentrovaná na stránce, ne opakující se dlaždice
- nemenší velikost SVG bez uživatelova pokynu

---

## Stránky

Web obsahuje přesně čtyři stránky — žádné další nevytvářet:

| URL | Soubor |
|---|---|
| `/` | `src/pages/index.astro` |
| `/cim-se-zabyvam/` | `src/pages/cim-se-zabyvam.astro` |
| `/kdo-jsem/` | `src/pages/kdo-jsem.astro` |
| `/kontakt/` | `src/pages/kontakt.astro` |

---

## Navigace

Navigace obsahuje pouze položky odpovídající stránkám webu:

```ts
export const NAV_LINKS = [
  { href: "/", title: "Úvod" },
  { href: "/cim-se-zabyvam/", title: "Čím se zabývám" },
  { href: "/kdo-jsem/", title: "Kdo jsem" },
  { href: "/kontakt/", title: "Kontakt" },
];
```

**Nikdy nepřidávat** další položky do navigace bez explicitního pokynu.

---

## SEO a metadata

- Vždy nastav `lang="cs"` v `<html>`
- OG image generovat dynamicky (`dynamicOgImage: true` v config)
- Zachovat původní URL slugy kvůli SEO (301 redirecty řešit přes vlastní doménu v GitHub Pages + `404.html` fallback nebo middleware)
- Nevkládat žádné analytické skripty bez explicitního pokynu

---

## Typografie

- Výchozí font AstroPaper: ponechat (systémový nebo Google Fonts — viz `astro.config.ts`)
- Doporučený česky přívětivý sans-serif: **Inter** nebo **Nunito** (oba dobře pokrývají diakritiku)
- Velikosti a řádkování neupravovat bez explicitního zadání

---

## Migrace obrázků

- Stáhnout obrázky z `ohnivazena.cz` a uložit lokálně (ne externí CDN)
- Cesta: `public/images/` pro statické assety, `src/assets/images/` pro zpracovávané obrázky
- Vždy nastavit smysluplný `alt` text (česky)
- Formát: preferovat WebP, pokud je originál JPEG/PNG > 200 kB

---

## Kontaktní formulář

Formulář je umístěn na stránce `src/pages/kontakt.astro`. Na úvodní stránce (`index.astro`) je pouze CTA sekce s krátkým textem o bezplatné konzultaci a tlačítkem odkazujícím na `/kontakt/`. Web je statický (GitHub Pages), takže odesílání zajišťuje externí služba.

### Primární řešení — Web3Forms (e-mail)

Registrace na https://web3forms.com — zdarma, 250 zpráv/měsíc, bez nutnosti backendu.

```astro
---
// src/pages/index.astro nebo src/components/ContactForm.astro
---
<form
  action="https://api.web3forms.com/submit"
  method="POST"
  class="flex flex-col gap-4"
>
  <!-- Access key získaný z web3forms.com — uložit do .env jako PUBLIC_WEB3FORMS_KEY -->
  <input type="hidden" name="access_key" value={import.meta.env.PUBLIC_WEB3FORMS_KEY} />
  <input type="hidden" name="subject" value="Nová zpráva z ohnivazena.cz" />
  <input type="hidden" name="from_name" value="Ohnivá žena — web" />
  <!-- Honeypot proti spamu -->
  <input type="checkbox" name="botcheck" class="hidden" style="display:none" />

  <label class="flex flex-col gap-1 text-sm font-medium">
    Jméno
    <input
      type="text"
      name="name"
      required
      placeholder="Vaše jméno"
      class="rounded border border-[var(--border)] bg-[var(--background)] px-3 py-2 focus:outline-none focus:ring-2 focus:ring-[var(--accent)]"
    />
  </label>

  <label class="flex flex-col gap-1 text-sm font-medium">
    E-mail
    <input
      type="email"
      name="email"
      required
      placeholder="vas@email.cz"
      class="rounded border border-[var(--border)] bg-[var(--background)] px-3 py-2 focus:outline-none focus:ring-2 focus:ring-[var(--accent)]"
    />
  </label>

  <label class="flex flex-col gap-1 text-sm font-medium">
    Zpráva
    <textarea
      name="message"
      required
      rows="4"
      placeholder="Napište mi, s čím vám mohu pomoci…"
      class="rounded border border-[var(--border)] bg-[var(--background)] px-3 py-2 focus:outline-none focus:ring-2 focus:ring-[var(--accent)]"
    ></textarea>
  </label>

  <button
    type="submit"
    class="rounded bg-[var(--accent)] px-6 py-3 font-semibold text-white hover:opacity-90 transition-opacity"
  >
    Odeslat zprávu
  </button>
</form>
```

Do `.env` (a do GitHub Actions secrets jako `PUBLIC_WEB3FORMS_KEY`):

```
PUBLIC_WEB3FORMS_KEY=váš-klíč-z-web3forms
```

### Volitelné rozšíření — Telegram notifikace (Cloudflare Worker)

Pokud Janinka chce okamžitou notifikaci do Telegramu místo (nebo vedle) e-mailu:

1. Janinka si přes [@BotFather](https://t.me/BotFather) vytvoří bota a získá `BOT_TOKEN`
2. Zjistí své `CHAT_ID` (např. přes [@userinfobot](https://t.me/userinfobot))
3. Vytvoří Cloudflare Worker (zdarma, 100 000 req/den):

```js
// worker.js — nasadit na Cloudflare Workers
export default {
  async fetch(request) {
    if (request.method !== "POST") return new Response("Method Not Allowed", { status: 405 });

    const data = await request.json();
    const text = `📩 Nová zpráva z ohnivazena.cz\n\n👤 ${data.name}\n📧 ${data.email}\n\n${data.message}`;

    await fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ chat_id: CHAT_ID, text }),
    });

    return new Response("OK");
  },
};
```

4. Do formuláře přidat skrytý fetch při odeslání (progressive enhancement — primárně funguje Web3Forms, Worker je bonus).

### Pravidla pro formulář

- Vždy přidat honeypot pole (`botcheck`) proti spamu
- Nikdy nevkládat API klíče přímo do `.astro` souborů — pouze přes `import.meta.env`
- Po úspěšném odeslání zobrazit česky potvrzení: „Zpráva odeslána. Ozveme se vám co nejdříve. 🙏"
- Pole pojmenovat česky v `placeholder`, atribut `name` ponechat anglicky

---

## Nasazení — GitHub Pages

Astro musí mít v `astro.config.ts` nastaven `site` a případně `base`, pokud web běží v podadresáři:

```ts
// astro.config.ts
import { defineConfig } from "astro/config";

export default defineConfig({
  site: "https://ohnivazena.cz",
  // base: "/", // ponechat výchozí — vlastní doména bez podadresáře
  output: "static",
});
```

CI/CD pipeline (`.github/workflows/deploy.yml`) — nasazení přes `actions/deploy-pages`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: pages
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: pnpm/action-setup@v3
        with:
          version: latest
      - uses: actions/setup-node@v4
        with:
          node-version: 22
          cache: pnpm
      - run: pnpm install
      - run: pnpm run build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: dist/

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - id: deployment
        uses: actions/deploy-pages@v4
```

Vlastní doména (`ohnivazena.cz`):
- Do `public/` přidat soubor `CNAME` s obsahem `ohnivazena.cz`
- V nastavení GitHub repozitáře → Pages → Custom domain nastavit `ohnivazena.cz`

---

## Komentáře

Původní WordPress komentáře **nepřenášet** do statického webu. Pokud klient požaduje systém komentářů, navrhnout:
1. **Giscus** (GitHub Discussions) — doporučeno
2. **Disqus** — pouze jako záložní varianta

---

## Zakázané vzory

- **Nikdy nepoužívat** výchozí modro-šedou paletu AstroPaper beze změny
- **Nikdy nenastavovat** `lightAndDarkMode: true` bez explicitního souhlasu klienta
- **Nikdy nevkládat** mandalu opakovaně (pattern/tile) — pouze jednou vycentrovaně
- **Nikdy nepřidávat** komentářový systém bez vyžádání
- **Nikdy nevytvářet** další stránky ani navigační položky nad rámec čtyř definovaných
- **Nikdy nepřidávat** blog ani zápisníček
