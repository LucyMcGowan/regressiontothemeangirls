# Contributing a post

Thanks for coming on the show! Here's how to add your write-up to the site.
Here are the steps to contribute:

1. open a Codespace  
2. copy the template 
3. write your post  
4. render it  
5. open a pull request 


## 1. Open a Codespace

Click this button (you'll need a free GitHub account):

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/LucyMcGowan/regressiontothemeangirls?quickstart=1)

This will open VS Code in your browser with Quarto, R, Python, and all the packages the site currently uses installed. The first launch may take a few minutes while it builds.

Create a new branch for your work (name it anything, e.g.
`sarah-post`). When you later push, GitHub will offer to make a fork under your
account.

> Prefer to work locally? Install [Quarto](https://quarto.org/docs/get-started/),
> clone your fork, and run the same commands below in your own terminal. The


## 2. Copy the template

In the Codespace terminal, run:

```bash
cp -r posts/_template posts/{NN-your-slug}
```

Where `NN` is a number, like `03`. Use the next free number (look in `posts/`) and a short hyphenated slug of your own. Then open `posts/NN-your-slug/index.qmd`.

## 3. Fill in yaml

The block between the `---` lines at the top. 

| Field | What goes in it |
|-------|-----------------|
| `title` | Post title. |
| `author` | Your name, as you want it credited. |
| `date` | Publish date, `YYYY-MM-DD`. |
| `image` | `featured.png` — the thumbnail (see step 5). |
| `categories` | Lower-case tags in `[brackets]`. Reuse existing tags where you can. |
| `draft` | Leave it as `true`. It keeps your post off the home page while you work; we will remove it to publish. |

## 4. Write the post

Write in Markdown, with R or Python in fenced chunks:

````markdown
```{r}
library(ggplot2)
mtcars |> ggplot(aes(wt, mpg)) + geom_point()
```
````

The template has working examples of a code chunk, an inline computed value,
and a captioned figure. The following are the chunk defaults: warnings and
messages are hidden, code is shown but collapsible, figures render at 8x5 in /
300 dpi, centered. You can override the defaults in each chunk with `#|` options, e.g. `#| fig-width: 10`.

**If you need a package that isn't installed** you can add R packages to the `packages` list in `.devcontainer/devcontainer.json` and Python packages to
`.devcontainer/requirements.txt`, then run **Codespaces: Rebuild Container**
from the command palette (F1). Commit those changes with your post.

To see your post as you write, click the **Preview** button in the top right of
the editor (from the Quarto extension), or run `quarto preview` in the terminal.

## 5. Add a featured image

Put one image named **`featured.png`** in your post folder. It will be the thumbnail on the home page. Any other images you reference can also go in the same folder.

## 6. Render, then commit everything

The site is published **without** re-running any code (it reuses the output
Quarto saves under `_freeze/`), so you need to render before committing:

```bash
quarto render
```

Then commit your source **and** the generated freeze files:

```bash
git add posts/NN-your-slug/ _freeze/ .devcontainer/
git commit -m "Add post: your title"
git push
```

If you change code later, run `quarto render` again and commit the updated
`_freeze/` files.

## 7. Open the pull request

Push your branch and open a PR (GitHub will show a "Compare &
pull request" button). 

If the PR's render check fails, it may be because `_freeze/` wasn't
committed (run `quarto render` again and commit the `_freeze/` changes).
