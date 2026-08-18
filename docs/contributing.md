# Contributing to This Site

This site is built with [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/){:target="_blank"}. Every page you see is a plain Markdown file in the `docs/` folder — MkDocs renders those files into a static website, and we push the rendered result to GitHub Pages. You do not need to know HTML or CSS to help. If you can write Markdown, you can write a page here.

This guide covers the whole loop: setting up your computer once, previewing your changes while you write, and publishing the site when you're done.

## What You Need

- **Python 3.8 or newer.** Check with `python --version`. If you don't have it, install it from [python.org](https://www.python.org/downloads/){:target="_blank"} and tick "Add Python to PATH" during the Windows installer.
- **Git.** Check with `git --version`. Install from [git-scm.com](https://git-scm.com/downloads){:target="_blank"} if missing.
- **Write access to the repo.** Ask an officer to add you to the [GT-Nanotech org](https://github.gatech.edu/GT-Nanotech){:target="_blank"} on GitHub Enterprise.

## One-Time Setup

You only do this once per computer.

### 1. Clone the repository

```bash
git clone git@github.gatech.edu:GT-Nanotech/documentation.git
cd documentation
```

### 2. Create a virtual environment

A virtual environment (venv) is a private folder of Python packages that belongs to this project alone. It keeps the exact MkDocs version this site needs from colliding with anything else you have installed, and it means everyone builds the site identically.

From the repo root, create one named `.venv`:

```bash
python -m venv .venv
```

### 3. Activate the virtual environment

The command differs by shell. Pick the line that matches yours:

| Shell / OS | Command |
| ---------- | ------- |
| Windows PowerShell | `.venv\Scripts\Activate.ps1` |
| Windows Command Prompt | `.venv\Scripts\activate.bat` |
| Git Bash on Windows | `source .venv/Scripts/activate` |
| macOS / Linux | `source .venv/bin/activate` |

Your prompt will gain a `(.venv)` prefix. That prefix is how you know it worked — no prefix means `mkdocs` commands will not be found.

!!! note "PowerShell blocks the activate script"

    If PowerShell answers with *"running scripts is disabled on this system"*, allow local scripts for your user account once:

    ```powershell
    Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
    ```

    Then run the activate command again.

To leave the environment later, run `deactivate`. You'll need to activate again in every new terminal you open.

### 4. Install the dependencies

```bash
pip install -r requirements.txt
```

`requirements.txt` pins the exact versions the site is built with. If someone bumps a version there, re-run this command to catch up.

!!! warning "Never commit `.venv/`"

    The `.venv/` folder is already listed in `.gitignore`, along with the generated `site/` folder. Both are rebuilt from source on any machine, so they should never end up in a commit.

## Everyday Workflow

Once set up, writing a page looks like this:

1. **Activate the venv** (step 3 above) — every new terminal, every time.

2. **Make a branch** so you're not editing the shared history directly:
   ```bash
   git checkout -B my-new-page
   ```

3. **Start the live preview:**
   ```bash
   mkdocs serve --livereload
   ```
   Open <http://127.0.0.1:8000> in a browser. Every time you save a Markdown file, the page reloads on its own. Leave this running in its own terminal while you write.

4. **Edit or add Markdown files** under `docs/`.

5. **Watch the terminal for warnings.** MkDocs prints a warning for broken internal links and for pages missing from the nav. Fix them before publishing.

6. **Commit and push:**
   ```bash
   git add .
   git commit -m "Added a page on wafer cleaning"
   git push -u origin my-new-page
   ```

7. **Publish** with `mkdocs gh-deploy` — see [Publishing the Site](#publishing-the-site) below.

Press `Ctrl+C` in the preview terminal to stop the server.

## MkDocs Commands

There are only three commands you need to know.

| Command | What it does |
| ------- | ------------ |
| `mkdocs serve` | Builds the site in memory and serves it at <http://127.0.0.1:8000> with live reload. This is what you use while writing. |
| `mkdocs build` | Renders the site to the `site/` folder on disk. You rarely need this — `gh-deploy` runs a build for you. Useful to confirm a clean build without publishing. |
| `mkdocs gh-deploy` | Builds the site and publishes it to GitHub Pages. |

A few flags worth knowing:

- `mkdocs serve -a localhost:8001` — serve on a different port if 8000 is already taken.
- `mkdocs serve --strict` — turn warnings into errors, so a broken link fails the build instead of scrolling past. A good final check before you publish.

## Adding a New Page

Two steps. Missing the second one is the most common mistake on this site.

1. **Create the Markdown file** in the right folder — `docs/projects/` for a project, `docs/resources/` for a tutorial or reference. Use lowercase-with-hyphens filenames, like `wafer-cleaning.md`.

2. **Add it to the `nav:` block in `mkdocs.yml`.** The nav is an explicit list, so **a page that isn't listed there won't appear in the sidebar at all**, even though it builds fine. Add a line at the matching indent level:

    ```yaml
    nav:
      - Resources:
        - resources/index.md
        - Intro to FabuBlox: resources/fabublox-tutorial.md
        - Wafer Cleaning: resources/wafer-cleaning.md   # <- your new page
    ```

    The label on the left of the colon is what shows in the sidebar, and it overrides the page's H1. Entries appear in exactly the order you list them.

### Images and Assets

Keep images next to the page that uses them, in an `assets/` folder named after the page:

```
docs/resources/assets/ece-server-tutorial/1.png
```

Reference them with a relative path:

```markdown
![Description of the image](./assets/ece-server-tutorial/1.png)
```

### Useful Markdown Extras

These are enabled site-wide in `mkdocs.yml`:

```markdown
!!! note "Callout title"

    Indent the body by four spaces. Swap `note` for `warning`, `tip`, or `danger`
    to change the color and icon.
```

Links that should open in a new tab take an attribute suffix:

```markdown
[Hacker Fab Documentation](https://docs.hackerfab.org/home){target="_blank"}
```

The full reference for callouts, card grids, icons, and the rest lives in the [Material for MkDocs docs](https://squidfunk.github.io/mkdocs-material/reference/){:target="_blank"}.

## Publishing the Site

We publish with MkDocs' built-in `gh-deploy` command. There is no CI pipeline — the site updates when a person runs this command, and not before.

```bash
mkdocs gh-deploy
```

That single command does three things: builds the site into `site/`, copies the result onto the `gh-pages` branch, and pushes that branch to `origin`. GitHub Pages serves whatever is on `gh-pages`, so the live site updates a minute or so later.

!!! warning "Commit your source before you deploy"

    `gh-deploy` publishes the files **currently in your working folder**, but it stamps the deploy commit with your last commit's hash — `Deployed 0a1c74e with MkDocs version: 1.6.1`. Deploy with uncommitted edits and the live site will contain work that no commit on the repo accounts for, which makes it impossible to tell later what was actually published. Always `git commit` and `git push` your Markdown first, then deploy.

!!! danger "Never edit the `gh-pages` branch by hand"

    It holds generated HTML only. `gh-deploy` overwrites it wholesale on every run, so any manual edit there is silently destroyed on the next deploy. All real work happens on `main` and feature branches.

After a successful run you'll see `Your documentation should be available shortly.` Because we're on GitHub Enterprise rather than public GitHub, MkDocs can't work out the URL and won't print one. Ours is:

**<https://github.gatech.edu/pages/GT-Nanotech/documentation/>**

Give it a minute, then hard-refresh (`Ctrl+Shift+R`) if you still see the old version — browsers cache these pages aggressively.

### When gh-deploy Complains

| Message | What to do |
| ------- | ---------- |
| `Deployment terminated: Previous deployment was made with MkDocs version X; you are attempting to deploy with an older version` | Your MkDocs is behind whoever deployed last. Run `pip install -r requirements.txt` to catch up rather than reaching for `--ignore-version`, which would publish an older build over a newer one. |
| `Updates were rejected because the remote contains work that you do not have` | Someone else deployed since you last fetched. Run `git fetch origin` and deploy again. Only use `mkdocs gh-deploy --force` if you're certain your build should overwrite theirs. |
| `Cannot deploy - this directory does not appear to be a git repository` | You're in the wrong folder. `cd` to the repo root, where `mkdocs.yml` lives. |

## Troubleshooting

**`mkdocs: command not found`** — your virtual environment isn't active. Look for the `(.venv)` prefix in your prompt and re-run the activate command.

**`The "glightbox" plugin is not installed`** — your venv is missing a dependency. Run `pip install -r requirements.txt` with the venv active.

**The preview doesn't reflect my edits** — check the `mkdocs serve` terminal for a build error. A YAML mistake in `mkdocs.yml` stops the rebuild and the browser keeps showing the last good version.

**My new page isn't in the sidebar** — you didn't add it to `nav:` in `mkdocs.yml`. See [Adding a New Page](#adding-a-new-page).

**Indentation error in `mkdocs.yml`** — YAML is whitespace-sensitive and rejects tabs. Use spaces only, and keep entries in a section at the same indent level as their siblings.
