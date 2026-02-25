# How to Push Changes Using Only the GitHub Website

This guide explains how to safely make and submit changes to the repository without cloning the repo or using the command line.

You will:

- Create your own branch
- Make edits to the content
- Submit a Pull Request (PR)

This keeps the **main** branch protected and prevents accidental site breaks.

**Check** that your branch is [not behind in commits](#keeping-your-branch-up-to-date-with-main) from the main branch before trying to push changes

## Step 1 - Create Your Own Branch

- Got to the repository on GitHub
- At the top left, click the branch dropdown and type a new branch name

![](images/create-branch.png){width=50%}

For this example, we are using the branch madi-dev.

## Step 2 - Edit a file

- Navigate to the file you want to edit by clicking the pencil icon (in the red box)

![](images/make-edits.png)

- After making changes click "Commit Changes"

![](images/commit-changes.png)

Your edit is now saved to your branch.

## Step 3 - Open a Pull Request

After committing, GitHub will show this on the main branch:

![](images/compare-pull.png)

Then, add a short description:

![](images/create-pull-request.png)

## Step 4 - Merge 

Once the changes have been approved and there are no conflicts with main, click "Merge pull request"

![](images/merge-pull-request.png)

Then, confirm the merge:

![](images/confirm-merge.png)

The merge has been successful!

![](images/successful-merge.png)

## Step 5 - Check That There Are No Issues Merging

Go back to the main branch and wait for the brown dot (pending changes) to a green checkmark (successfully updated).

![](images/waiting-for-merge.png)

![](images/finished-merge.png)


---

# Keeping Your Branch Up to Date With Main

If other people are merging changes into **main**, your branch can fall behind.

Before opening (or merging) a Pull Request, you should make sure your branch is up to date. 

## Why This Matters

If your branch is behind **main**, you may see:

- "This branch is out of date"
- Merge conflicts
- Unexpected overwrites
- Broken navigation (for Quarto sites)

Keeping your branch current prevents conflicts.

## Step 1 - Open a Pull Request

Check that status of your branch first:

![](images/behind-commits-main.png)

The branch we are using as an example is 16 commits behind main.

Navigate to the Pull Requests and open a New Pull Request:

![](images/make-new-pull-request.png)

## Step 2 - Comparing Changes

After opening the PR, change the base to main, and the compare branch to the your branch.

If we can merge the branches, then a green check mark saying "Able to Merge" will appear next to the boxes. 

Now, Create the Pull Request.

## Step 3 - Merge the Branch with Main

Create title and description of why you are merging the branches. Then, create PR.

![](images/merge-madidev-to-main.png)

GitHub will automatically check for conflicts between branches, and then allow you to merge them.

![](images/successful-merge-madidev.png)

Now, your branch is sucessfully updated to the main branch! You can now make edits on your branch and push them to main. 

# How to Reverse Changes

Sometimes mistakes happen. You may:

* Merge a Pull Request too early
* Edit the wrong file
* Delete something accidentally
* Break navigation in a Quarto page

There are safe ways to reverse changes directly in the GitHub web interface.

## Scenario 1 – The Pull Request Has NOT Been Merged

If the PR is still open, the easiest solution is:

### Option A – Close the Pull Request

1. Go to the Pull Request.
2. Click **Close pull request**.
3. (Optional) Click **Delete branch**.

The changes will not be merged into `main`.

This is the safest option.

### Option B – Edit the File Again

If you only need to fix part of the change:

1. Go to the file.
2. Click the ✏️ pencil icon.
3. Restore the previous content manually.
4. Commit to your branch.

Then update the Pull Request.

## Scenario 2 – The Pull Request Has Already Been Merged

If the changes are already merged into `main`, do NOT try to manually edit files back.

Instead, use GitHub’s **Revert** feature.

### Step 1 – Go to the Merged Pull Request

Find the merged PR in the Pull Requests tab.

### Step 2 – Click “Revert”

In the top-right of the merged PR, click Revert as shown in the red box:

![](images/revert.png)

GitHub will:

* Create a new branch
* Create a new commit that undoes the previous merge
* Open a new Pull Request

### Step 3 – Create and Merge the Revert PR

Add a short description explaining why you are reverting.

Then:

* Click **Create pull request**
* Click **Merge pull request**
* Confirm merge

This safely restores the repository to its previous state.

# Important Notes for This Repository (Quarto Website)

Because this repository builds a website:

* Do NOT edit files inside the `docs/` folder to reverse changes.
* Always revert using the PR if possible.
* Reverting ensures the exact previous working state is restored.

Manually editing files back can miss small changes and cause layout issues.


# Quick Decision Guide

| Situation     | What To Do              |
| ------------- | ----------------------- |
| PR open       | Close PR                |
| PR merged     | Click Revert            |
| Minor mistake | Edit again and recommit |
| Major break   | Revert PR immediately   |