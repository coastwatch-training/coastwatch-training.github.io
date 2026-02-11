
# CoastWatch Training Website — Collaborator Guide

This repository hosts the CoastWatch Training website, built using Quarto and deployed automatically via **GitHub Actions + GitHub Pages**.

You do **NOT** need to install Quarto.
You do **NOT** need to run quarto render.
You do **NOT** need to touch the docs/ folder.

GitHub automatically builds and deploys the site when changes are merged into main.

## 1. What this repository is

This is a Quarto website.

You edit source files (mostly .qmd files), and GitHub handles:

- rendering the site
- executing Python code
- deploying the updated website

## 2. Important: What NOT to Do

- Do NOT run quarto render
- Do NOT edit anything inside docs/
- Do NOT push directly to main

The docs/ folder is automatically generated during deployment and should never be edited manually.

## 3. How the Site is Structured

### Main Pages

| Page | File |
|------|------|
| Welcome | `index.qmd` |
| News & Announcements | `news-announcements.qmd` |
| Office Hours | `officehours.qmd` |
| About | `about.qmd` |
| Help | `help.qmd` |

---

### Trainings

| Type | Location |
|------|----------|
| Trainings landing page | `trainings/index.qmd` |
| Upcoming trainings | `trainings/upcoming/*.qmd` |
| Past trainings | `trainings/past/*.qmd` |

Inside the trainings folder, is the presentations folder where presentations from each course is stored and referenced to by either the upcoming or past training pages.

---

### Tutorials

| Page | Location |
|------|----------|
| Tutorials landing page | `tutorials/index.qmd` |
| Code Gallery | `tutorials/codegallery.qmd` |
| Software tutorials | `tutorials/*.qmd` |

Software tutorials also has pages that teach users more about ERDDAP, NetCDF, Panoply, and CWUtils; there is also a code gallery for these tools. 

### Sidebar Navigation

The sidebar is controlled by:

``` yml
_quarto.yml
```
Under:

``` yml
website:
  sidebar:
    contents:
```
If you add a new page and it does not appear in the sidebar, it must be added here.

## 4. Standard Workflow (Edit → PR → Merge)

This is the only workflow collaborators should use.

#### Step 1 — Create a new branch

``` bash
git checkout -b my-branch-name
```

#### Step 2 — Make your edits

Edit the relevant .qmd file(s).

You may edit:

- text
- images
- tables
- links
- page content

**Do not edit docs/.**

#### Step 3 — Commit your changes

``` bash
git add .
git commit -m "Brief description of changes"
git push origin my-branch-name
```

#### Step 4 — Open a Pull Request

Open a PR from your branch into main.

#### Step 5 — Automated Rendering & Deployment

Once your PR is merged:

- GitHub Actions runs automatically
- Quarto renders the site
- Python code (if present) is executed
- The website is deployed to GitHub Pages

You do not need to do anything else.

## 5. How Deployment Works (for context)

When changes are merged into main:

- GitHub installs Quarto
- GitHub installs required Python packages
- GitHub runs quarto render
- The rendered site (in docs/) is deployed automatically

The docs/ folder is not manually maintained.

## 6. Adding a New Page

Example: Add a new Upcoming Training

#### 1. Create the file:

```
trainings/upcoming/newtraining26.qmd
```

#### 2. Add it to _quarto.yml under:

``` yml
website:
  sidebar:
    contents:
```

Example:

``` yml
- section: "Upcoming Trainings"
  contents:
    - href: trainings/upcoming/newtraining26.qmd
      text: 2026 New Training Name
```

#### 3. Commit and open a PR.

That’s it.

## 7. Common Issues

#### Page does not appear in sidebar

It was not added to _quarto.yml.

#### Deployment fails after merge

This usually means:

- A syntax error in YAML
- A broken Python code chunk
- A missing file path

Check the Actions tab in GitHub to see the error log.

Do not attempt to manually fix docs/.

#### Page title looks strange in the browser tab

Page titles are controlled by the YAML frontmatter at the top of each .qmd file.

If unsure, ask the maintainer (madison.richardson@noaa.gov).

## 8. Best Practices

- Always work on a branch
- Always open a Pull Request
- Never push directly to main
- Never edit docs/
- Keep commits focused and small
- If something breaks, check the GitHub Actions log

## 9. Getting Help

If something behaves unexpectedly:

- Do not force a merge
- Check the Actions tab for error logs
- Take a screenshot or copy the error message
- Contact the site maintainer (madison.richardson@noaa.gov)

# HOW TO ADD A TUTORIAL TO THE WEBSITE

If you are adding tutorials, please read the guide:

[Adding Tutorials](adding-tutorials.md)

# HOW TO ADD A LECTURE TO THE WEBSITE

If you are adding lectures, please read the guide:

[Adding Lectures](adding-lectures.md)