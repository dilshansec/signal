==============================================================================
                    UAP OBSERVATORY — MAINTENANCE & UPDATE GUIDE
==============================================================================

This repository contains the UAP Observatory static web application. 
The codebase is structured into a clean, modular architecture compatible with 
GitHub Pages static hosting.

Adding or modifying UFO/UAP incidents and gallery media requires editing ONLY 
the data files inside 'data/' and uploading images to 'images/'. You NEVER 
need to modify the core application files (index.html, style.css, or app.js).

==============================================================================
1. PROJECT ARCHITECTURE
==============================================================================

UAP_WEB/
├── index.html                  # Main website HTML layout & library entry point
├── style.css                   # Cybernetic theme & CoverFlow gallery styles
├── app.js                      # Application logic (Map, D3, Search, Modals, Carousel)
├── data/
│   ├── incidents.js            # UFO/UAP Incident Dataset
│   └── gallery.js              # Side-Panel Gallery Media Dataset
├── images/
│   ├── incidents/              # Photos associated with specific UFO incidents
│   └── gallery/                # Photos displayed in right-side media carousel
├── README.md                   # Markdown maintenance guide
└── README.txt                   # Text file maintenance guide (this file)

==============================================================================
2. HOW TO ADD A NEW UFO INCIDENT
==============================================================================

When you want to add a new UFO/UAP incident to the world map and log list:

Step 1: Upload the Image
- Place your image file (e.g. sri-lanka-uap.jpg) inside 'images/incidents/'.
- Recommended formats: .jpg, .jpeg, .png, or .webp.
- Recommended size: under 500 KB for fast loading.

Step 2: Open the Data File
- Open 'data/incidents.js' in a text editor or directly on GitHub.

Step 3: Copy & Paste the Incident Template
- Scroll to the bottom of the INCIDENTS array.
- Paste the template below right before the closing ]; bracket.

Step 4: Fill in the Incident Details
- Update properties: id, title, date, coords, location, status, description, image.

Step 5: Save & Commit
- Save the file, commit, and push your changes to GitHub.


------------------------------------------------------------------------------
COPY-PASTE INCIDENT TEMPLATE
------------------------------------------------------------------------------

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

==============================================================================
3. HOW TO ADD IMAGES TO INCIDENTS
==============================================================================

- Folder Location: Always place incident images inside 'images/incidents/'.
- Filename Rules: Use clean filenames without spaces (use hyphens or underscores), 
  e.g., incident-2025-kandy.jpg.
- Image Property Path: Inside data/incidents.js, write the relative path:
  "image": "images/incidents/incident-2025-kandy.jpg"
- Case-Sensitivity: File extensions are case-sensitive on GitHub Pages (.jpg vs .JPG).
  Make sure the extension in data/incidents.js matches your image filename exactly.

==============================================================================
4. HOW TO ADD PHOTOS TO THE SIDE PANEL GALLERY
==============================================================================

The right-side vertical CoverFlow gallery is populated from data/gallery.js.

1. Upload your photo to 'images/gallery/' (e.g. gallery-photo-20.jpg).
2. Open 'data/gallery.js'.
3. Copy-paste the template below to the end of the GALLERY_IMAGES array.

------------------------------------------------------------------------------
COPY-PASTE GALLERY IMAGE TEMPLATE
------------------------------------------------------------------------------

  {
    id: "gal-10",
    title: "KANDY MOUNTAIN SIGHTING",
    date: "2025-01-15",
    status: "UNRESOLVED",
    image: "images/gallery/gallery-photo-20.jpg",
    description: "Photograph captured during the Knuckles Mountain Range UAP event."
  },

==============================================================================
5. GITHUB UPLOAD & DEPLOYMENT PROCEDURE
==============================================================================

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

Option A: Direct Upload via GitHub Website
1. Open your repository on GitHub.com.
2. Navigate to 'images/incidents/' or 'images/gallery/'.
3. Click "Add file" -> "Upload files", drag your image file, and click "Commit changes".
4. Navigate to 'data/incidents.js', click pencil icon (Edit), paste new incident object, and click "Commit changes".
5. GitHub Pages will automatically update your live site!

Option B: Upload via Git / GitHub Desktop
1. Open your project folder on your computer.
2. Edit 'data/incidents.js' and save image files into 'images/incidents/'.
3. Open terminal or GitHub Desktop.
4. Run:
   git add .
   git commit -m "Add new UFO incident data"
   git push origin main

==============================================================================
6. TROUBLESHOOTING GUIDE
==============================================================================

- New incident does not appear on map:
  Ensure coords is [latitude, longitude], e.g., [7.2906, 80.6337]. 
  Check Developer Console (F12) for validation warnings.

- Broken image icon on card/tooltip:
  Check case sensitivity (e.g. .jpg vs .JPG) and verify the file exists in 
  images/incidents/.

- Changes not visible on live site:
  Hard refresh your browser using Ctrl + F5 (or Cmd + Shift + R on Mac).

- Script error or blank map:
  Ensure all objects inside INCIDENTS array are separated by commas.
