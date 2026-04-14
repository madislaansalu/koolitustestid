# KoolitusTest — Admin paneel

Veebirakendus testide loomiseks ja haldamiseks. Töötab täielikult brauseris, ei vaja serverit ega installatsioonitööriistu.

## Funktsioonid

- Loo ja halda valikvastustega teste
- Kakskeelne kasutajaliides (eesti / vene)
- Seadista läbimise lävi (%)
- Automaatne e-posti teavitus läbi EmailJS
- Ekspordi test iseseisva `.html` failina
- Impordi varem eksporditud teste
- Andmed salvestatakse brauseri `localStorage`-sse

## Failide struktuur

```
koolitustestid/
├── admin.html    ← Peamine admin paneel
├── styles.css    ← Kõik stiilid (CSS muutujad, komponendid, mobiilivaade)
├── script.js     ← Kogu loogika (i18n, CRUD, eksport/import, login)
└── README.md
```

## Kasutamine

1. Ava `admin.html` brauseris (topeltklõps failil)
2. Sisesta parool: `admin`
3. Loo test → lisa küsimused → salvesta
4. Klõpsa **Ekspordi** → laadib alla `test.html` mida saad jagada õpilastele

## Muutmine

| Fail | Mida muuta |
|------|-----------|
| `styles.css` | Värvid (CSS muutujad `:root` plokis), fondid, paigutus |
| `script.js` | Tõlked (`langs` objekt), loogika, EmailJS seaded, parool |
| `admin.html` | HTML struktuur, sektsioonide järjestus |

### Parooli muutmine

Ava `script.js` ja otsi üles rida:
```js
const ADMIN_PASSWORD = "admin";
```
Muuda `"admin"` oma soovitud parooliks.

### Värvi teema muutmine

Ava `styles.css` ja muuda `:root` plokis CSS muutujaid:
```css
:root {
  --ink:     #1a1a2e;  /* Peamine teksti värv */
  --paper:   #f5f0e8;  /* Taustavärv */
  --accent:  #c84b31;  /* Rõhutusvärv (nupud, ikoonid) */
  --success: #2d6a4f;  /* Edukas olek */
}
```

### Tõlgete muutmine

Ava `script.js` ja leia `const langs = { ... }` objekt. Seal on kõik kasutajaliidese tekstid eesti (`et`) ja vene (`ru`) keeles.

## Tehniline info

- Puhas HTML/CSS/JavaScript — sõltuvusi pole
- Font: [DM Sans + DM Serif Display](https://fonts.google.com/) (Google Fonts)
- E-post: [EmailJS](https://www.emailjs.com/) integratsioon
- Andmehoidla: `localStorage` (püsiv) + `sessionStorage` (sisselogimine)
- Eksport: test.html genereeritakse base64 mallina
