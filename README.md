
# CoastWatch Training Website — Collaborator Guide

This repository hosts the **CoastWatch Training website**, built using **Quarto** and deployed automatically using **GitHub Actions + GitHub Pages**.

You do **NOT** need to install Quarto.
You do **NOT** need to run `quarto render`.
You do **NOT** need to edit anything inside `docs/`.

GitHub automatically builds and deploys the website when changes are merged into `main`.

Each automated build step typically takes **2–5 minutes**.

---

# 1. What This Repository Is

This is a **Quarto website**.

You edit the source files (mostly `.qmd` files), and GitHub automatically handles:

* rendering the site
* executing Python code
* publishing the website

Two types of builds occur automatically:

| Build Type           | What It Does                                                 |
| -------------------- | ------------------------------------------------------------ |
| **Preview Build**    | Creates a preview version of the website for your branch     |
| **Production Build** | Updates the live website when changes are merged into `main` |

---

# 2. Important: What NOT to Do

* Do **NOT** run `quarto render`
* Do **NOT** edit anything inside `docs/`
* Do **NOT** push directly to `main`

The `docs/` folder is automatically generated during deployment and should **never be edited manually**.

---

# 3. How the Site is Structured

## Main Pages

| Page                 | File                     |
| -------------------- | ------------------------ |
| Welcome              | `index.qmd`              |
| News & Announcements | `news-announcements.qmd` |
| Office Hours         | `officehours.qmd`        |
| About                | `about.qmd`              |
| People               | `people.qmd`             |
| Help                 | `help.qmd`               |

---

## Trainings

| Type                   | Location                   |
| ---------------------- | -------------------------- |
| Trainings landing page | `trainings/index.qmd`      |
| Upcoming trainings     | `trainings/upcoming/*.qmd` |
| Past trainings         | `trainings/past/*.qmd`     |

Inside the `trainings` folder is the **presentations folder**, where course presentations are stored and referenced by either the upcoming or past training pages.

---

## Tutorials

| Page                   | Location                    |
| ---------------------- | --------------------------- |
| Tutorials landing page | `tutorials/index.qmd`       |
| Code Gallery           | `tutorials/codegallery.qmd` |
| Software tutorials     | `tutorials/*.qmd`           |

Software tutorials include pages explaining how to use:

* ERDDAP
* NetCDF
* Panoply
* CoastWatch Utilities

There is also a **code gallery** for these tools.

---

## Sidebar Navigation

The sidebar navigation is controlled by:

```
_quarto.yml
```

Under:

```yml
website:
  sidebar:
    contents:
```

If you add a new page and it does not appear in the sidebar, it must be added here.

---

# 4. Standard Workflow (Edit → Preview → PR → Merge)

This is the workflow collaborators should follow when working locally through the terminal.

If you are committing changes through the GitHub web interface, follow the steps in this guide:

[github-branches-merging.md](github-branches-merging.md)

---

## Step 1 — Create a new branch

```
git checkout -b my-branch-name
```

---

## Step 2 — Make your edits

Edit the relevant `.qmd` file(s).

You may edit:

* text
* images
* tables
* links
* page content

**Do not edit `docs/`.**

---

## Step 3 — Commit your changes

```
git add .
git commit -m "Brief description of changes"
git push origin my-branch-name
```

---

# 5. Automatic Preview Builds

When you push changes to your branch, GitHub automatically builds a **preview version of the website**.

This usually takes **2–5 minutes**.

The preview allows you to view your changes without affecting the live site.

### Preview URL

Your preview will be available at:

```
https://coastwatch-training.github.io/preview/<your-branch-name>/
```

Example:

```
https://coastwatch-training.github.io/preview/madi-dev/
```

Once the workflow finishes, you can open this link to see your preview site.

You can check the progress of the build under:

```
GitHub → Actions → Quarto Branch Preview
```

---

# 6. Open a Pull Request

Once you have reviewed your preview and confirmed everything looks correct:

Open a Pull Request from your branch into `main`.

Example:

```
my-branch-name → main
```

This allows collaborators to review your changes before they are merged.

---

# 7. Production Deployment

When the Pull Request is merged into `main`, GitHub automatically runs the **production deployment workflow**.

This workflow:

1. Installs Quarto
2. Installs required Python packages
3. Runs `quarto render`
4. Publishes the website to GitHub Pages

This process also takes about **2–5 minutes**.

Once complete, the live site updates here:

```
https://coastwatch-training.github.io/
```

---

# 8. How Deployment Works (for context)

The repository contains two automated workflows:

| Workflow             | Purpose                              |
| -------------------- | ------------------------------------ |
| `quarto-preview.yml` | Builds preview versions for branches |
| `quarto-site.yml`    | Deploys the production site          |

The production site is served from the **`gh-pages` branch**, which stores the rendered website.

The `main` branch contains the **source Quarto files**.

The `docs/` folder is automatically generated during rendering and should not be edited manually.

---

# 9. Adding a New Page

Example: Add a new Upcoming Training.

### 1. Create the file

```
trainings/upcoming/newtraining26.qmd
```

---

### 2. Add it to `_quarto.yml`

Under:

```yml
website:
  sidebar:
    contents:
```

Example:

```yml
- section: "Upcoming Trainings"
  contents:
    - href: trainings/upcoming/newtraining26.qmd
      text: 2026 New Training Name
```

---

### 3. Commit and open a PR

Once merged, the page will automatically appear on the website.

---

# 10. Common Issues

### Page does not appear in sidebar

It was not added to `_quarto.yml`.

---

### Preview site does not appear

Check the workflow under:

```
Actions → Quarto Branch Preview
```

Preview builds usually take **2–5 minutes**.

---

### Deployment fails after merge

This usually means:

* a YAML syntax error
* a broken Python code chunk
* a missing file path

Check the **Actions tab** in GitHub to view the error log.

Do **not** attempt to manually fix `docs/`.

---

### Page title looks strange in the browser tab

Page titles are controlled by the YAML frontmatter at the top of each `.qmd` file.

If unsure, ask the maintainer:

```
madison.richardson@noaa.gov
```

---

# 11. Best Practices

* Always work on a branch
* Always open a Pull Request
* Review your **preview site** before merging
* Never push directly to `main`
* Never edit `docs/`
* Keep commits focused and small
* If something breaks, check the **GitHub Actions log**

---

# 12. Getting Help

If something behaves unexpectedly:

* Do not force a merge
* Check the **Actions tab** for error logs
* Take a screenshot or copy the error message
* Contact the site maintainer

```
madison.richardson@noaa.gov
```

---

# HOW TO ADD A TUTORIAL TO THE WEBSITE

If you are adding tutorials, please read the guide:

**[Adding Tutorials](adding-tutorials.md)**

---

# HOW TO ADD A LECTURE TO THE WEBSITE

If you are adding lectures, please read the guide:

**[Adding Lectures](adding-lectures.md)**
 
