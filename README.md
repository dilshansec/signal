# UAP World Monitor — Maintenance & Update Guide

This repository contains the **UAP World Monitor** static web application. The codebase has been refactored into a clean, modular architecture compatible with **GitHub Pages** static hosting.

Adding or modifying UFO/UAP incidents and gallery media requires editing **only** the data files inside `data/` and uploading images to `images/`. You **never** need to modify the core application files (`index.html`, `style.css`, or `app.js`).

---

## 📁 Project Architecture

```
/
├── index.html                  # Main website HTML layout & library entry point
├── style.css                   # High-contrast cybernetic theme & CoverFlow gallery styles
├── app.js                      # Application logic (D3 Map, Filtering, CoverFlow Engine, Modals)
├── data/
│   ├── incidents.js            # UFO/UAP Incident Dataset
│   └── gallery.js              # Side-Panel Gallery Media Dataset
├── images/
│   ├── incidents/              # Photos associated with specific UFO incidents
│   └── gallery/                # Photos displayed in the right-side media carousel
└── README.md                   # Complete update guide & templates
```

---

## 🛸 A. How to Add a New UFO Incident

When you want to add a new UFO/UAP incident to the world map and log list:

1. **Upload the Image**:
   - Place your image file (e.g. `sri-lanka-uap.jpg`) inside the `images/incidents/` folder.
   - Recommended formats: `.jpg`, `.jpeg`, `.png`, or `.webp`.
   - Recommended dimensions: ~800px × 600px (under 500 KB for fast loading).

2. **Open the Data File**:
   - Open [`data/incidents.js`](data/incidents.js) in a text editor or directly on GitHub.

3. **Copy & Paste the Incident Template**:
   - Scroll to the bottom of the `INCIDENTS` array.
   - Paste the template below right before the closing `];` bracket.

4. **Fill in the Incident Details**:
   - Update the properties (`id`, `title`, `date`, `coords`, `location`, `status`, `type`, `description`, `source`, `image`).

5. **Save & Commit**:
   - Save the file, commit, and push your changes to GitHub.

---

### 📋 Copy-Paste Incident Template

```javascript
  {
    id: "uap-19",
    title: "Kandy Mountain UAP",
    name: "KANDY MOUNTAIN UAP",
    date: "2025-01-15",
    year: 2025,
    location: "Kandy, Sri Lanka",
    country: "Sri Lanka",
    coords: [7.2906, 80.6337],
    status: "UNRESOLVED",
    category: "UNRESOLVED",
    type: "SILVER DISC / LUMINOUS ORB",
    description: "Multiple witnesses observed a silent glowing silver disc hovering over the Knuckles Mountain Range for 20 minutes before accelerating vertically.",
    source: "Civilian & Meteorological Station Witnesses",
    image: "images/incidents/sri-lanka-uap.jpg",
    images: ["images/incidents/sri-lanka-uap.jpg"]
  },
```

---

## 🖼️ B. How to Add Images to Incidents

- **Folder Location**: Always place incident images inside `images/incidents/`.
- **Filename Rules**: Use clean filenames without spaces (use hyphens `-` or underscores `_`), e.g., `incident-2025-kandy.jpg`.
- **Image Property Path**: Inside `data/incidents.js`, write the relative path:
  `"image": "images/incidents/incident-2025-kandy.jpg"`
- **Case-Sensitivity**: File extensions are case-sensitive on GitHub Pages (`.jpg` vs `.JPG`). Make sure the extension in `data/incidents.js` matches your image filename exactly.

---

## 📸 C. How to Add Photos to the Side Panel Gallery

The right-side vertical CoverFlow gallery is populated from [`data/gallery.js`](data/gallery.js).

1. Upload your photo to `images/gallery/` (e.g. `gallery-photo-20.jpg`).
2. Open [`data/gallery.js`](data/gallery.js).
3. Copy-paste the template below to the end of the `GALLERY_IMAGES` array.

### 📋 Copy-Paste Gallery Image Template

```javascript
  {
    id: "gal-10",
    title: "KANDY MOUNTAIN SIGHTING",
    date: "2025-01-15",
    status: "UNRESOLVED",
    image: "images/gallery/gallery-photo-20.jpg",
    description: "Photograph captured during the Knuckles Mountain Range UAP event."
  },
```

---

## 🚀 D. GitHub Upload & Deployment Procedure

```
   Edit data/incidents.js or data/gallery.js
                     ↓
   Upload image file to images/incidents/ or images/gallery/
                     ↓
   Commit Changes ("Add Kandy UAP Incident")
                     ↓
   Push to GitHub Repository
                     ↓
   GitHub Pages automatically rebuilds (10–30 seconds)
                     ↓
   Refresh Website (Ctrl + F5)
```

### Option 1: Direct Upload via GitHub Website
1. Open your repository on **GitHub.com**.
2. Navigate to `images/incidents/` or `images/gallery/`.
3. Click **Add file** → **Upload files**, drag your image file, and click **Commit changes**.
4. Navigate to `data/incidents.js`, click the pencil icon ✏️ to edit, paste your new incident object, and click **Commit changes**.
5. GitHub Pages will automatically update your live site in seconds!

### Option 2: Upload via Git / GitHub Desktop
1. Open your project folder on your computer.
2. Edit `data/incidents.js` and save image files into `images/incidents/`.
3. Open terminal or GitHub Desktop.
4. Run:
   ```bash
   git add .
   git commit -m "Add new UFO incident data"
   git push origin main
   ```

---

## 🔍 E. Troubleshooting Guide

| Issue | Cause | Solution |
| :--- | :--- | :--- |
| **New incident does not appear on map** | Invalid coordinates in `data/incidents.js` | Ensure `coords` is `[latitude, longitude]`, e.g., `[7.2906, 80.6337]`. Check browser Developer Console (F12) for validation warnings. |
| **Broken image icon on card/tooltip** | Typo or case mismatch in image path | Check case sensitivity (e.g. `.jpg` vs `.JPG`) and verify the file exists in `images/incidents/`. |
| **Changes not visible on live site** | Browser cache | Hard refresh your browser using `Ctrl + F5` (or `Cmd + Shift + R` on Mac). |
| **Script error or blank map** | Syntax error in `data/incidents.js` | Ensure all objects inside `INCIDENTS` array are separated by commas `,`. |
