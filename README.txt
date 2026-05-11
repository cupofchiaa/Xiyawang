# Updating Your Website

You never need to touch any HTML or CSS. There are just two plain-text files you edit to update your site, plus an `images/` folder for artwork photos.

---

## The files you'll edit

| File | What it controls |
|---|---|
| `cv-config.js` | Everything on the Info page — your statement, CV sections, exhibitions, press |
| `config.js` | Your artwork — titles, mediums, descriptions, images |

Open either file in a text editor. A free one that works well is **Visual Studio Code** — download it at code.visualstudio.com. You can also use TextEdit on Mac (make sure to use Format → Make Plain Text before saving).

---

## Updating your CV (`cv-config.js`)

Open `cv-config.js`. You'll see sections like this:

```
groupExhibitions: [
  { year: "2026", text: "<em>Student Exhibition</em>, Art Students League of New York, New York, NY" },
  { year: "2022", text: "<em>Fruits of Passion</em>, MOMO SUSHI, New York, NY" },
],
```

**To add a new entry**, copy an existing line and paste it above or below. Change the year and text to match your new entry. Keep the punctuation exactly as-is — the quotes, commas, and curly braces all matter.

**To remove an entry**, delete the whole line (from `{` to the `},` at the end).

**To italicize an exhibition title**, wrap it in `<em>` and `</em>`:
```
"<em>My Show Title</em>, Gallery Name, City"
```

**To update your artist statement**, find the `statement:` line near the top and replace the text between the quotes. Keep it on one line.

**To remove a placeholder entry** (the ones with `——`), simply delete that line.

---

## Adding artwork (`config.js`)

Each artwork looks like this:

```
{
  title: "Stray Cats in Hawaii I",
  titleChinese: "夏威夷的野猫",       ← optional, delete this line if not needed
  medium: "Lithograph on paper",
  dimensions: '???"',        ← optional, leave as "" if you don't want to show this
  category: "printmaking",       ← must be: "printmaking", "painting", or "sketches"
  image: "images/lotus.jpg",     ← filename of the image you added to the images/ folder
  originalAvailable: true,       ← set to true if you're open to selling the original
  shopifyProductId: "",          ← leave blank unless you're selling prints via Shopify
  description: "...",            ← optional short text shown under the artwork
},
```

**To add a new artwork:**
1. Drop the image file into the `images/` folder
2. Copy an existing block (from `{` to `},`) and paste it at the top of the list
3. Fill in the details — make sure the `image:` filename matches exactly what you named the file

**Works appear on the site in the order they appear in this file** — topmost first.

---

## Publishing changes to the website

Once you've saved your edits, you need to push them to GitHub so the site updates. This takes about 3 commands and 30 seconds.

### First-time setup (do this once)

1. Check that Git is installed: open Terminal (press `Cmd + Space`, type "Terminal", press Enter) and type:
   ```
   git --version
   ```
   If you see a version number, you're good. If not, follow the prompt to install it.

2. Navigate to your website folder:
   ```
   cd ~/Downloads/xiyawang
   ```
   (If you moved the folder, replace the path with wherever it lives.)

### Every time you want to publish a change

Open Terminal, then run these three commands one at a time:

```
cd ~/Downloads/xiyawang
```
*(goes to your website folder)*

```
git add .
```
*(stages all your changes)*

```
git commit -m "update website"
```
*(saves a snapshot — you can replace "update website" with a short note like "add new print" or "update cv")*

```
git push
```
*(sends the changes to GitHub, which updates the live site)*

Your site should update within a minute or two. You can visit xiyawang.org to confirm.

---

## Tips

- **Always save the file before running `git add .`** — unsaved changes won't be included.
- If you make a mistake and the site looks broken, don't panic. You can always go back to a previous version — just ask for help.
- The `images/` folder accepts `.jpg`, `.jpeg`, `.png`, and `.gif` files. For best results, resize photos to around 1800px wide before uploading (this keeps the site fast).
