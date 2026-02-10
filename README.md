# CoastWatch Training Website — Collaborator Guide

This repository hosts the **CoastWatch Training** website, built using **Quarto** and published via **GitHub Pages**.

This guide is written for collaborators who **may not have used Quarto before**. It explains:

- how the site is structured
- where to make changes
- how to safely render the site
- how to push updates to GitHub without breaking anything

---

## 1. What this repository is

This is a **Quarto website**.

You edit source files (mostly `.qmd`), then run Quarto to build the website into a folder called:

```
docs/
```

GitHub Pages publishes the site **from `docs/`**.

**Workflow overview:**

edit source files → quarto render → commit changes → push → open PR

---

## 2. How the site is configured (`_quarto.yml`)

### Output directory

``` yml
project:
  output-dir: docs
```

- All rendered website files go into docs/
- Do not manually edit files inside docs/

### Files that get rendered

``` yml
project:
  render: 
    - "**/*.qmd"
    - "**/*.ipynb"
    - "!**/*.Rmd"
```

Quarto will:

- render all .qmd pages
- render all .ipynb notebooks
- ignore .Rmd files

### Sidebar navigation

Everything under:

``` yml
website:
  sidebar:
    contents:
```

controls:

- what appears in the left navigation
- the order of pages

If you add a new page and it doesn’t appear in the sidebar, it needs to be added here.

### Styling

``` yml
format:
  html:
    theme: cosmo
    css: styles.css
```

The site uses:

- the Cosmo Bootstrap theme
- custom styling in styles.css

---

## 3. Repository structure (where things live)

### Main pages

| Page | File |
|---|---|
| Welcome | `index.qmd` |
| News & Announcements | `news-announcements.qmd` |
| Office Hours | `officehours.qmd` |
| About | `about.qmd` |
| Help | `help.qmd` |

---

### Trainings

| Type | Location |
|---|---|
| Trainings landing page | `trainings/index.qmd` |
| Upcoming trainings | `trainings/upcoming/*.qmd` |
| Past trainings | `trainings/past/*.qmd` |

---

### Tutorials

| Page | Location |
|---|---|
| Tutorials landing page | `tutorials/index.qmd` |
| Code Gallery | `tutorials/codegallery.qmd` |
| Software tutorials | `tutorials/*.qmd` |

### Site output (auto-generated)

```
docs/
```

⚠️ Do not manually edit files in docs/.
This folder is overwritten every time Quarto renders the site.

--- 

## 4. One-time setup for collaborators

### Install Quarto

Download and install Quarto from:  
https://quarto.org

Verify installation:

``` bash
quarto --version
```

### Clone the repository

``` bash
git clone <repo-url>
cd coastwatch-training.github.io
```

---

## 5. Standard workflow (edit → render → push)

### Step 1 — Create a new branch

```bash
git checkout -b my-branch-name
```
### Step 2 — Make your edits

Edit the relevant .qmd files.

### Step 3 — Preview locally (recommended)

``` bash
quarto preview
```

This launches a local preview server and updates automatically as you save.

Stop preview with:

Ctrl + C

### Step 4 — Render the website

From the repository root:

``` bash
quarto render
```

This updates the docs/ folder.

### Step 5 — Check changes before committing

``` bash
git status
git diff --stat
```

If you only edited one page, you should see a small number of changed files.

### Step 6 — Commit and push

``` bash
git add filename
git commit -m "Brief description of changes"
git push -u origin
```

### Step 7 — Open a Pull Request

Open a PR from your branch into main.

Once merged, GitHub Pages will automatically update the live site.

---

## 6. Avoiding massive deletions (VERY IMPORTANT)

If you ever see thousands of deletions, STOP.

This usually happens if:

- docs/ was deleted or cleaned
- Quarto was run from the wrong directory
- everything was staged without checking

### Safety checks before committing

Always run:

``` bash
git status
```

If you see a huge list of deletions in docs/, do not commit.

### Undo staged changes

``` bash
git restore --staged .
```

### Restore files to last commit

⚠️ This discards local changes:

``` bash
git restore .
```

### Restore only the rendered output

``` bash
git restore docs/
```

Then re-run:

``` bash
quarto render
git status
```

---

## 7. Adding a new page correctly
### Example: Add a new Past Training page

Create the file:

```
trainings/upcoming/newtraining26.qmd
```

Add it to the sidebar in _quarto.yml:

``` yml
- section: "Upcoming Trainings"
  contents:
    - href: trainings/upcoming/newtraining26.qmd
      text: 2026 New Training Name
```

Render and preview:

``` bash
quarto render
quarto preview
```

Commit, push, and open a PR.

---

## 8. Common issues
### Page doesn’t appear in the sidebar

The page exists but hasn’t been added to:

``` yml
website:
  sidebar:
    contents:
```

### Page title looks odd in the browser tab

Quarto uses YAML frontmatter metadata for titles. Some layouts hide visible titles while still needing metadata for the browser tab.

Ask the site maintainer (madison.richardson@noaa.gov) if unsure.

### Render fails due to missing packages

Some pages may execute code during render. If this happens:

- required packages must be installed locally, or
- the page should be rendered with pre-saved outputs

Ask the maintainer before troubleshooting.

---

## 9. General best practices

- Always work on a branch
- Always run git status before committing
- Never manually edit docs/
- If something looks wrong, stop and ask before pushing

---

## 10. Getting help

If something behaves unexpectedly:

- do not force a commit
- take a screenshot or copy terminal output
- ask the site maintainer (madison.richardson@noaa.gov) for guidance
