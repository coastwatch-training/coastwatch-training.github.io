# Adding a Lecture to the Website

The Course Lectures page is automatically generated from a CSV file.

You do **not** edit the webpage directly.

Instead, you:

1. Upload the lecture files (PDF / PPTX)
2. Add a new row to `lectures.csv`
3. Open a Pull Request
4. GitHub Actions rebuilds and deploys the site automatically

---

## 1. Where the Lectures CSV Lives

The lectures table is generated from:

```
lectures/lectures.csv
```

⚠️ Do not change column names  
⚠️ Do not reorder columns  
⚠️ Do not delete existing rows  

Only add a new row at the bottom.

---

## 2. Upload Lecture Files

Lecture files should be stored in:

```
lectures/
```


Example:

```
lectures/
├── NewTraining.pdf
└── NewTraining.pptx
```

If you have a transcript file, place it in:

```
lectures/transcripts/
```

Example:

```
lectures/transcripts/new-training.qmd
```

---

## 3. Understanding the CSV Columns

`lectures.csv` contains the following columns:

| Column | Description |
|----------|-------------|
| `title` | Lecture title displayed on the site |
| `preview_url` | Link to the PDF version (viewable in browser) |
| `download_url` | Link to the PowerPoint file |
| `description` | Short summary shown in the table |
| `video_url` | YouTube link (optional) |
| `transcript_url` | Path to transcript file (optional) |

---

## 4. Adding a New Lecture (Step-by-Step)

### Step 1 — Upload Files

Add your files to:

```
lectures
```

Example:

```
lectures/02-NewTopicLecture.pdf
lectures/02-NewTopicLecture.pptx
```

If you have a transcript:

```
lectures/transcripts/02-new-topic.qmd
```

---

### Step 2 — Add a Row to `lectures.csv`

Open:

```
lectures/lectures.csv
```

Add a new row following the format of existing lectures.

### Important:

- `preview_url` should link to the **PDF** file on GitHub
- `download_url` should link to the **PPTX** file
- `video_url` can be left blank if no video exists
- `transcript_url` should be a relative path (no GitHub URL)

---

## 5. Commit and Open a Pull Request

```bash
git checkout -b add-new-lecture
git add .
git commit -m "Add new lecture: Satellite 201"
git push origin add-new-lecture
```

Open a PR into main.

Once merged:

- GitHub Actions runs
- Quarto rebuilds the site
- The lecture automatically appears in the table

--- 

## 6. Common Mistakes to Avoid

❌ Changing the CSV header row
❌ Using incorrect GitHub file paths
❌ Forgetting to upload the PDF or PPTX
❌ Using absolute local file paths
❌ Editing docs/ manually

---

## 7. Troubleshooting

If the lecture does not appear:

- Check for typos in lectures.csv
- Confirm the file paths are correct
- Ensure the PDF/PPTX files were committed
- Review the GitHub Actions log for errors
