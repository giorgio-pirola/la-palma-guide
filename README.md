# 🌋 La Palma - Travel Guide App

A simple interactive web app with a map of La Palma (Canary Islands), showing curated recommendations for restaurants, attractions, the astronomical observatory, beaches, trails, and local products.

**Live site:** https://yourusername.github.io/la-palma-guide/
*(replace with your actual GitHub Pages link)*

---

## 📂 Project structure

This is a single-file static web app:

```
la-palma-guide/
├── index.html      ← everything (HTML, CSS, JS) lives here
└── README.md       ← this file
```

No build tools, no dependencies to install. It uses:
- [Leaflet.js](https://leafletjs.com/) for the interactive map (loaded from a CDN)
- [OpenStreetMap](https://www.openstreetmap.org/) for map tiles (free, no API key needed)

---

## ✏️ How to add a new place

All content lives inside the `data` object near the top of the `<script>` section in `index.html`. Look for this block:

```js
const data = {
  restaurants: { ... },
  attractions: { ... },
  observatory: { ... },
  beaches: { ... },
  nature_trails: { ... },
  products: { ... }
};
```

Each category contains an `items` array. To add a new place, add a new object to the relevant array, following this format:

```
{
  name: "Name of the place",
  desc: "Short description — what it is, why it's worth visiting, any tips.",
  lat: 28.6619,
  lng: -17.9157
}
```
### Example — adding a new restaurant

Find the `restaurants` section and add your entry inside the `items: [ ... ]` array:

```
restaurants: {
    label: "🍽️ Restaurants",
    color: "#e63946",
    items: [
      {
        name: "New Restaurant Name",
        desc: "Great tapas place in Santa Cruz, try the croquettes.",
        lat: 28.6850,
        lng: -17.7650
      },
      // ... keep existing entries below
    ]
  },
```

⚠️ Don't forget the **comma** after each entry (except the very last one in the array).

---

## 📍 How to find coordinates (lat/lng)

1. Open [Google Maps](https://www.google.com/maps)
2. Search for the place
3. Click on the correct pin
4. Look at the **URL in the address bar** — it will contain something like:
   ```
   https://www.google.com/maps/place/Chipi+Chipi/@28.6619,-17.9157,17z/...
   ```
5. The two numbers right after the `@` symbol are your coordinates:
   ```
   lat: 28.6619,
   lng: -17.9157
   ```

---

## 🧭 Items without a map location (optional)

Some entries (e.g. generic local products like "Mojo sauce" or "Papas Arrugadas") don't correspond to one specific spot. For these, simply **omit** `lat` and `lng`:

```
{
  name: "Mojo (rojo y verde)",
  desc: "Classic Canarian sauces available in most local shops and markets."
}
```

These items will still appear in the sidebar list, but won't show a pin on the map.

---

## 📁 Adding a whole new category
To add a new top-level menu section (e.g. "Nightlife"), add a new key to the `data` object:

```
nightlife: {
    label: "🌙 Nightlife",
    color: "#ff6b6b",
    items: [
      {
        name: "Example Bar",
        desc: "Nice place for a drink.",
        lat: 28.6800,
        lng: -17.7600
      }
    ]
  },
```

- `label`: the text shown in the sidebar menu (emoji optional, but nice for visual scanning)
- `color`: the hex color used for both the menu dot and the map pins for this category

You can also add an optional `description` field to any category (shown when the menu is expanded) — currently used for the Observatory section to explain visiting rules:

```
observatory: {
    label: "🔭 Observatory",
    color: "#6a4c93",
    description: "General info or rules shown at the top of this category.",
    items: [ ... ]
  },
```

---

## 🧪 Testing changes locally before publishing

**Option 1 — Just open the file**
Double-click `index.html` to open it directly in your browser. Good enough for quick checks (map tiles and Leaflet still load fine via CDN).

**Option 2 — Local server (recommended for consistent testing)**
If you have Node.js installed:
```bash
npx live-server
```
This opens the app in your browser and auto-refreshes every time you save a change.

---

## 🚀 Publishing changes

This repo is connected to **GitHub Pages**. Any change pushed to the `main` branch automatically updates the live site within 1–2 minutes.

```bash
git add index.html
git commit -m "Add new restaurant: [name]"
git push
```

---

## ✅ Checklist when adding a new place

- Correct `name`
- Short, useful `desc`
- Verified `lat`/`lng` from Google Maps (or omitted if not location-specific)
- Comma placed correctly after the entry
- Tested locally before pushing
- Pushed to GitHub and checked the live site after ~1 minute

---

## 🗺️ Current categories

| Category | Key in `data` |
|---|---|
| 🍽️ Restaurants | `restaurants` |
| 📸 Attractions | `attractions` |
| 🔭 Observatory | `observatory` |
| 🏖️ Beaches & Sea Spots | `beaches` |
| 🥾 Nature & Trails | `nature_trails` |
| 🛍️ Local Products | `products` |