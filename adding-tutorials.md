# Adding a Tutorial to the Code Gallery (For Satellite Data Tutorials and Software Tutorials)

The Code Galleries are automatically generated from a CSV file.

You do **not** edit the webpage directly.

Instead, you:

1. Add the tutorial files to the correct folder  
2. Add a new row to the CSV  
3. Open a Pull Request  
4. GitHub Actions rebuilds and deploys the site automatically  

---

## 1. Where the Code Gallery CSVs Lives

The Satellite Data Tutorials Code Gallery is generated from:

```
tutorials/code_gallery.csv
```

The Software Tutorials Code Gallery is generated from:

```
tutorials/softwarecodegallery.csv
```

⚠️ Do not change column names  
⚠️ Do not reorder columns  
⚠️ Do not delete existing rows  

You only add a **new row** at the bottom of the file.

---

## 2. Required Folder Structure

Each tutorial must live inside:

```
tutorials/<slug>/
```

Example:

```
tutorials/Tutorial1-basics/
```

Inside that folder, organize by language:

```
tutorials/Tutorial1-basics/
├── python/
│ └── Tutorial1-basics.ipynb
├── r/
│ └── Tutorial1-basics.qmd
├── matlab/
│ └── Tutorial1-basics.qmd
└── images/
├── tut1_1_py.png
├── tut1_2_py.png
├── tut1_1_r.png
└── tut1_1_m.png
```

You only need folders for the languages you are providing.

---

## 3. Understanding the CSV Columns

Each row in the csv represents one tutorial.

### Core Fields

| Column | Description |
|---------|-------------|
| `title` | Display title of the tutorial |
| `category` | Category grouping shown in the gallery |
| `slug` | Folder name inside `tutorials/` |
| `description` | Short summary shown in the gallery |

---

### View & Download Links

Each language has two types of links:

- `*_view` → used for preview icons
- `*_download` → used for download icons

Example (Python):

| Column | Example |
|--------|----------|
| `py_view` | `Tutorial1-basics/python/Tutorial1-basics.ipynb` |
| `py_download` | `tutorials/Tutorial1-basics/python/Tutorial1-basics.ipynb` |

**Important:**

- `*_view` uses a relative path without `tutorials/`
- `*_download` includes `tutorials/`

Follow the existing pattern exactly.

---

### Preview Images

These images are for the preview card when you click the eye icon on the gallery table.

#### Columns:
- `py_img`
- `r_img`
- `m_img`

#### Format:

```
filename.png::Caption text | filename2.png::Caption text
```

#### Example:

```
tut1_1_py.png::Time series plot | tut1_2_py.png::Map of SST
```

Preview images must be placed in:

```
tutorials/<slug>/images/
```

---

## 4. Adding a New Tutorial (Step-by-Step)

### Step 1 — Create the Folder

```
tutorials/my-new-tutorial/
```


Add language subfolders and files.

---

### Step 2 — Add Images

Place preview images inside:

```
tutorials/my-new-tutorial/images/
```

Place images that belong inside the tutorial (for the .qmd pages) inside:

```
tutorials/my-new-tutorial/coding-language/images/
```

---

### Step 3 — Add a Row to the CSV

Open:

```
tutorials/code_gallery.csv
```

or

```
tutorials/softwarecodegallery.csv
```

Add a new row following the format of existing tutorials.

Do not modify header row.

---

### Step 4 — Commit and Open a Pull Request

```bash
git checkout -b add-my-new-tutorial
git add .
git commit -m "Add new tutorial: My New Tutorial"
git push origin add-my-new-tutorial
```

Open a PR into main.

Once merged:

- GitHub Actions runs
- Quarto renders the site
- The tutorial appears automatically

--- 

## 5. Common Mistakes to Avoid

❌ Changing column names in the CSV
❌ Using inconsistent slug names
❌ Incorrect file paths
❌ Forgetting to add the tutorial to the sidebar (if needed)
❌ Editing docs/ manually

--- 

## 6. Troubleshooting

If the tutorial does not appear:

- Check the slug matches the folder name exactly
- Check for typos in CSV paths
- Ensure images are in the correct folder
- Review the GitHub Actions log for errors
