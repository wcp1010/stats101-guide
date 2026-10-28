# STATS101 startup

> **Student:** make a folder called STATS101, put this file in it, open a new Claude conversation with access to that folder, drag this file in, and say "Follow startup.md."
>
> **Claude:** set up this student's workspace, then brief them. Assume they are not technical: one step at a time, plain language, no jargon, check in after each step. You do all the technical work. Never ask the student to type commands, and never ask for a password.

## 0. Make sure you can do this

You need to create files and run programs. If you can't, stop and tell the student, in one short message: open the Claude desktop app, switch to the mode that works on files on your computer (Cowork), give it the STATS101 folder, and drag this file in again. A paid plan is needed for that.

Find out where you are before installing anything:
- **Folder.** Work in the student's STATS101 folder: the folder they connected, or the one this file is in. If they connected no folder, create STATS101 wherever your workspace is.
- **Can the student see your files?** If your workspace is a sandbox or cloud copy they can't open, tell them so in one line. From then on, hand them every file they need (rendered HTML especially) as a download or attachment.
- **System.** macOS, Windows or Linux. Do you have admin rights? Is there a package manager (brew, apt, conda/micromamba)? Is the internet reachable?

## 1. Install

Needed: R, Quarto, and the R packages `tidyverse`, `knitr`, `kableExtra`, `broom`, `rmarkdown`, `modelsummary`.

Check what's already there (`R --version`, `quarto --version`, `requireNamespace()` for each package) and install only what's missing. Use the first route that works:

- **Quarto.** The official installer works if you have admin rights. Without them, download the tarball/zip for this OS and CPU from the Quarto GitHub releases page and unpack it into a folder you own. That works with no password. Call it by its full path, or put it on PATH.
- **R.** On macOS or Windows, if you can't install it silently, download the official installer (CRAN), put it in the STATS101 folder, and ask the student to double-click it. If the system asks for a password, they type it into that system window, never into the chat. On Linux or in a sandbox, use `apt-get install r-base` if you have root. Otherwise use micromamba/conda into a folder you own (`r-base` from conda-forge).
- **Packages.** Install them into a library you can write to (create `Sys.getenv("R_LIBS_USER")` if needed), from `https://cloud.r-project.org`. On Linux, use binary packages (conda-forge `r-tidyverse` etc., or Posit Package Manager's Linux binaries), because compiling tidyverse from source takes a very long time.
- **Downloads blocked?** Your internet access may be limited by the app's settings. Tell the student exactly which setting to change, and which sites need to be allowed: cloud.r-project.org, github.com, quarto.org, and conda.anaconda.org or packagemanager.posit.co if used. Then retry.

Write down what worked in CLAUDE.md under "Environment" (see the template): where R and Quarto live, and the exact commands to reinstall. Sandboxes can be reset between conversations, so later sessions may need to repeat the install.

## 2. Folders and files

Create the following. Each file's exact contents are at the end of this document, between the code fences. Never overwrite a file that already exists; ask first.

```
STATS101/
  CLAUDE.md        <- template below; fill in "Environment"
  method.md        <- file below
  theme_stats.R    <- file below; copy into each project folder when it starts
  sample/sample.qmd  <- file below
  lectures/
```

Project folders (hw1/, hw2/, hw3/, final/ ...) are made when each project's instructions arrive, named as the course names them, each with text/ inside.

## 3. Test

Copy `theme_stats.R` into `sample/` and run `quarto render sample.qmd` there. Fix any failure before moving on: a missing package means install it; "quarto not found" means use the full path. Then check that the HTML has no code, warnings or error messages in it.

Show the student the result: open it on their computer if you can, otherwise hand them the file. Tell them this is what their projects will look like, and that they can ask you to change the look any time. You edit `theme_stats.R`, and backgrounds stay light because graphs are shown on a projector.

## 4. Explain the loop, then wait

Every project runs on this loop. Explain it to the student in plain words, ask if anything is unclear, then stop.

1. **Drop files anywhere.** I file them into the right project.
2. **I make a plan:** every question, its points, what you write and what I make.
3. **I explain the variables.** No results yet.
4. **You write every Think for the section:** predictions as ranges with a reason and how confident you are. Tell me when they're done. Seeing results first ruins the prediction, and graders can tell.
5. **I make the Show:** graphs and tables with your prediction drawn on, plus a list of what came out against what you predicted.
6. **You write the Tells.** I point out mistakes but never write or reword your text; the professor grades down AI-written text.
7. **I put it together, render and check.** You read the final HTML and submit early.

Also tell them:
- **Every new conversation:** open it on the STATS101 folder. If Claude doesn't seem to know the plan, say "Read CLAUDE.md."
- **Keep a copy of your own writing** outside this folder too (notes app, email to yourself). It's the part of the work that is yours.

---

## Template: CLAUDE.md

```
# STATS101 - standing orders

For every project, follow method.md.

## Each conversation
- Read this file and method.md first.
- Check that R and Quarto still run (quarto --version; R loads tidyverse). If not, reinstall using "Environment" below, say so in one line, then continue.
- If the student can't open files in your workspace, hand them every file they need to see.

## Environment
(Filled in at setup: OS, where R and Quarto are, the exact reinstall commands, and whether the student can see this folder directly.)

## The loop
- Every project runs: 1 files in, 2 plan, 3 variable briefing, 4 my Thinks, 5 your Show, 6 my Tells, 7 assemble and check. Details in method.md.
- Start each reply about a project with where we are ("Step 4: your Thinks for 2a-2c"). End with exactly what I do next, naming the files to write.
- Show me the plan as a short checklist by question: what I write (named files), what you make, status. Update it as we go.

## Filing
The student will drop files anywhere: the folder root, the chat, nested in odd places. At the start of each session, and whenever new files appear, put them where they belong:
- Instructions, data and anything project-specific -> that project's folder (hw1/, hw2/, hw3/, final/ ...; create it, with text/ inside, when a new project's instructions arrive). Decide from the contents, not the filename.
- Lecture decks and readings -> lectures/.
- The student's own writing -> that project's text/, named by question label (1a-think.md). Text pasted into the chat is saved there first, word for word, then inserted.
- Never delete or overwrite: on a name clash, keep both with a suffix. Old versions go in that folder's old/.
- If you can't tell where something goes, ask. Say in one line what you moved.

## Deliverable
- Quarto .qmd rendered to HTML, in the project's folder. ggplot() for graphs, kable() for tables, unless the project requires something else (e.g. modelsummary() for regression tables): the project's requirements win.
- Setup chunk (include: false): tidyverse, knitr, kableExtra; source("theme_stats.R"); use_theme(). Next chunk, `#| output: asis`: cat(theme_css()).
- No code, warnings or messages in the HTML unless a question asks for code. Check the rendered HTML for them every time.
- Every question label (1a, 1b, 2a...) appears as a heading, exactly as written, in order.
- p-values as "< 0.001", never 0.

## My writing
- Never write or reword description or interpretation for me, not even a draft.
- My text is in the project's text/ folder (1a-think.md etc.). Insert it under the right heading, word for word.
- You may flag errors (wrong number, wrong term, unsupported claim, unnamed condition): quote the line, say what's wrong.

## Predictions
- Show me no results for a question until I say its Think is written. Before that, only what variables mean, their type, and suitable displays.
- Exception: tell me about broken data (missing, impossible, duplicated) without describing results.

## Numbers
- Every number comes from code you ran. Recompute headline numbers a second way.
- If the instructions are ambiguous, ask.

## Graphs
- Data in ink; my prediction in the accent colour, dashed, drawn on the graph. Nothing else uses dashed accent: other reference lines (means, medians) are ink2, dotted.
- Title states the finding; axes have plain names and units; more than four colours means facet_wrap().
- When I ask for a graph, offer two or three options.
- Look changes go in theme_stats.R so every graph follows. Keep backgrounds light.

## Graph contest (projected in class)
- Light background, 16:9, large type, one finding readable in three seconds.
- Check at thumbnail size and with contrast lowered.
```

---

## File: method.md

````markdown
# method.md: how to run a STATS101 project

For Claude. Read alongside CLAUDE.md; steps match the loop there. Your job: build every graph, table and check a full-marks project needs, while the student writes every word of text. Grading rewards interpretation over correct numbers, so your work exists to give the student's Thinks and Tells something sharp to work with.

## Step 2: Plan (touch no results)

- Read the instructions in full. Write `plan.md` in the project folder: one row per question with its exact label, points, the verbatim prompt, what the student writes (named files: `1a-think.md`, `1a-tell.md`), what you make (graph / table / code shown), and status. Show it to the student as a short checklist and update it as each step finishes.
- List the technical requirements separately, verbatim. They differ by project (e.g. HW2 required `modelsummary()` for regression tables). Note word, graph and table limits and the progress-check date.
- Audit the data, reporting only facts that affect method: rows, types, missing or impossible values, duplicates, odd encodings (many exact zeros, codes, units), and where the data comes from. Never describe distributions or relationships.

## Steps 3-4: Brief, then wait for the Thinks

For each question in the section: what each variable means (check the source's documentation), units, how it was measured, its type, which display the type calls for, and which lecture method applies. No numbers from the data.

Ask the student to predict every quantity the Show will report (shape, centre, spread, r, slope, R², group differences) as a range with a reason and a confidence level. Ask for all Thinks in the section before any Show, because one result poisons the next prediction. Wait until they say the Thinks are written.

## Step 5: Show

- Copy the predictions from the student's Think files into one `tribble` in the setup chunk. Graphs and any later scoreboard read from it, so a prediction is never quoted two different ways.
- Make exactly the display the prompt asks for. Draw the prediction on it. Caption and label every figure and table.
- Then give the student, in chat, a short fact list for their Tell: each observed value next to its prediction, in or out of range (exact, no rounding a miss into a hit), and anything unusual (outliers, gaps, a second mode). Facts only, no explanations.

**Course methods by topic**

- *One distribution:* histogram (plus boxplot if useful); shape, centre, spread, outliers; median/IQR when skewed, mean/SD when symmetric.
- *Groups:* side-by-side boxplots and a summary table by group.
- *Two categorical:* contingency table with counts and the row or column percentages that answer the question.
- *z-scores:* (group value − overall mean) / overall SD; show code when the prompt says so.
- *Correlation and regression:* scatterplot first. Check every condition by name with a plot or number each: Quantitative Variables, Straight Enough, Outlier, Does the Plot Thicken? Residual plot, R², s_e against the SD of y.
- *Re-expression:* when skew or fanning appears, fit untransformed, log-y and log-log side by side in one table with the same diagnostics. Help the student decide once, then hold that choice for later questions. Log coefficients become percent changes.
- *Multiple regression:* each coefficient "holding the others fixed", in units; per-SD effects to compare sizes; indicators against a named baseline. Watch for a confounder (season, time, group) driving a pairwise result: show the coefficient with and without it.
- *Inference (final project):* coefficient CIs and p-values, every diagnostic, one-unit and Q1→Q3 effects. With large n everything is significant, so effect sizes carry the argument.

## Step 6: Check the Tells

Read each Tell against the output. Quote and flag: wrong numbers or terms, causal claims from association, unnamed conditions, a miss called a hit, a Tell that only restates the graph, a Tell that doesn't say whether the prediction held. Pointers are fine ("2b never says why the miss happened"). Wording is not: never suggest phrasing.

For synthesis questions ("In summary"): give the student their results grouped by theme and point out any mechanism that recurs across questions. They write the conclusion; it must not be a recap.

## Step 7: Assemble and check

- Every label from the instructions is a heading, in order, even if the student restructures.
- Extras go after the required parts, clearly labelled optional, and each one answers a question the required work raised. The required answer always comes first.
- Every technical requirement met; no code, warnings or messages in the HTML; p-values formatted.
- Every number in the student's text matches the output; recompute headline numbers a second way.
- Count words, graphs and tables against the limits.
- Render, get the HTML in front of the student (open it, or hand them the file), and walk through `plan.md` row by row with the student.
````

---

## File: theme_stats.R

```r
# theme_stats.R - one look for every graph and the report around it.
#
# In a .qmd setup chunk:   source("theme_stats.R"); use_theme()
# Then a chunk with `#| output: asis` containing:   cat(theme_css())
#
# ink = what the data shows. accent, dashed = what you predicted.
# To change the look, edit the colours below (keep the background light).

stats_theme <- list(
  ground = "#F3F6F9", card = "#FFFFFF", ink = "#0F1B2D", ink2 = "#475569",
  rule = "#D7DEE7", accent = "#0E9AA7", accentInk = "#0B6F78",
  second = "#C2410C", stone = "#94A3B8",
  font = '-apple-system, "Segoe UI", "Helvetica Neue", Arial, sans-serif'
)

theme_stats <- function(t = stats_theme, base_size = 13) {
  ggplot2::theme_minimal(base_size = base_size) +
    ggplot2::theme(
      plot.background  = ggplot2::element_rect(fill = t$ground, colour = NA),
      panel.background = ggplot2::element_rect(fill = t$ground, colour = NA),
      panel.grid.major = ggplot2::element_line(colour = t$rule, linewidth = 0.3),
      panel.grid.minor = ggplot2::element_blank(),
      axis.title       = ggplot2::element_text(colour = t$ink, face = "bold"),
      axis.text        = ggplot2::element_text(colour = t$ink2),
      plot.title       = ggplot2::element_text(colour = t$ink, face = "bold", size = base_size + 1.5),
      plot.subtitle    = ggplot2::element_text(colour = t$ink2, size = base_size - 1.5),
      plot.caption     = ggplot2::element_text(colour = t$ink2, size = base_size - 3.5, hjust = 0),
      plot.title.position = "plot", plot.caption.position = "plot",
      strip.text       = ggplot2::element_text(colour = t$ink, face = "bold"),
      legend.position  = "top", legend.title = ggplot2::element_blank(),
      legend.text      = ggplot2::element_text(colour = t$ink2),
      plot.margin      = ggplot2::margin(14, 16, 10, 14)
    )
}

use_theme <- function(t = stats_theme, base_size = 13) {
  # colour names usable in any plot: ink, ink2, accent, accentInk, second, stone, ...
  list2env(t[setdiff(names(t), "font")], envir = globalenv())
  assign("pal_stats", c(t$ink, t$accent, t$stone, t$second), envir = globalenv())
  ggplot2::theme_set(theme_stats(t, base_size))
  for (g in c("point", "line", "path", "segment", "text"))
    ggplot2::update_geom_defaults(g, list(colour = t$ink))
  for (g in c("bar", "col", "area", "density"))
    ggplot2::update_geom_defaults(g, list(fill = t$ink, colour = NA))
  ggplot2::update_geom_defaults("boxplot", list(fill = t$card, colour = t$ink))
  ggplot2::update_geom_defaults("smooth", list(colour = t$ink2, fill = t$rule))
  options(ggplot2.discrete.colour = pal_stats, ggplot2.discrete.fill = pal_stats)
  knitr::opts_chunk$set(dev.args = list(bg = t$ground), fig.width = 7, fig.height = 4.4,
                        echo = FALSE, warning = FALSE, message = FALSE)
  invisible(t)
}

# The report's look, matched to the graphs.
theme_css <- function(t = stats_theme) {
  sprintf('<style>
body{background:%1$s;color:%3$s;font-family:%10$s;line-height:1.65;}
main,.quarto-title-block{max-width:46rem;}
h1,h2,h3,h4{color:%3$s;font-family:%10$s;font-weight:700;letter-spacing:-0.01em;}
h1.title{border-bottom:3px solid %6$s;padding-bottom:.3em;}
h2{margin-top:2.2em;border-bottom:1px solid %5$s;padding-bottom:.2em;}
h3{color:%4$s;}
a{color:%7$s;text-underline-offset:2px;} a:hover{color:%6$s;}
code:not(pre code){color:%7$s;background:%2$s;padding:.1em .3em;border-radius:3px;}
blockquote{border-left:3px solid %6$s;color:%4$s;padding:.2em 0 .2em 1em;margin-left:0;}
.table,table{background:%2$s;color:%3$s;border-collapse:collapse;--bs-table-bg:%2$s;--bs-table-color:%3$s;}
table th{background:%3$s !important;color:%1$s !important;font-weight:600;text-align:left;}
table td,table th{border:1px solid %5$s;padding:.4em .6em;}
caption,.figure-caption,figcaption{color:%4$s;text-align:left;font-size:.92em;}
hr{border:0;border-top:1px solid %5$s;margin:2.5em 0;}
#TOC a.nav-link,.sidebar nav a{color:%4$s !important;} #TOC a.nav-link.active{color:%7$s !important;border-left-color:%6$s !important;}
</style>', t$ground, t$card, t$ink, t$ink2, t$rule, t$accent, t$accentInk, t$second, t$stone, t$font)
}
```

---

## File: sample/sample.qmd

````markdown
---
title: "Sample report"
subtitle: "STATS101 sample: lorem ipsum text, random data"
author: "Your Name"
date: today
date-format: "MMMM D, YYYY"
format:
  html:
    embed-resources: true
    toc: true
    toc-location: left
---

```{r}
#| label: setup
#| include: false
library(tidyverse)
library(knitr)
library(kableExtra)
source("theme_stats.R")
use_theme()
set.seed(101)
```

```{r}
#| output: asis
cat(theme_css())
```

*Every number and graph on this page is random data. Every word is filler. It shows what a finished project looks like.*

# Introduction

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident.

# Question 1: Describing a distribution

## 1a. Investigating `runtime`

> Think

Lorem ipsum dolor sit amet, consectetur adipiscing elit: **most values between 90 and 120, centred near 105**, skewed right; about 70% confident. Integer posuere erat a ante venenatis dapibus posuere velit aliquet.

> Show

```{r}
#| label: fig-1a
#| fig-cap: "Lorem ipsum: the shaded band and dashed line are the prediction from the Think."
runtime <- tibble(minutes = c(rnorm(380, 108, 14), rexp(60, 1 / 30) + 125))
ggplot(runtime, aes(minutes)) +
  annotate("rect", xmin = 90, xmax = 120, ymin = -Inf, ymax = Inf, fill = accent, alpha = 0.12) +
  geom_histogram(binwidth = 5, colour = ground) +
  geom_vline(xintercept = 105, colour = accent, linetype = "dashed", linewidth = 0.9) +
  annotate("text", x = 121, y = Inf, vjust = 1.6, hjust = 0, colour = accentInk, size = 3.8,
           label = "My prediction: 90–120, centred on 105") +
  labs(title = "Lorem ipsum: the tail runs much longer than predicted",
       subtitle = "Runtime of 440 random films", x = "Runtime (minutes)", y = "Number of films")
```

> Tell

Donec ullamcorper nulla non metus auctor fringilla. Vestibulum id ligula porta felis euismod semper. Cras justo odio, dapibus ac facilisis in, egestas eget quam.

## 1b. Comparing groups

> Show

```{r}
#| label: fig-1b
#| fig-cap: "Lorem ipsum: boxplots by group, with the overall median dashed."
groups <- tibble(genre = rep(c("Action", "Comedy", "Drama"), times = c(150, 170, 180)),
                 minutes = c(rnorm(150, 116, 16), rnorm(170, 99, 11), rnorm(180, 112, 20)))
ggplot(groups, aes(genre, minutes)) +
  geom_hline(yintercept = median(groups$minutes), colour = ink2, linetype = "dotted") +
  geom_boxplot(width = 0.5, outlier.colour = stone) +
  labs(title = "Lorem ipsum: comedies run shortest and vary least",
       subtitle = "Runtime by genre, 500 random films", x = NULL, y = "Runtime (minutes)")
```

```{r}
#| label: tbl-1b
#| tbl-cap: "Lorem ipsum: summary statistics by group."
groups |>
  group_by(Genre = genre) |>
  summarise(n = n(), Mean = mean(minutes), SD = sd(minutes), Median = median(minutes)) |>
  kable(digits = 1) |>
  kable_styling(full_width = FALSE)
```

> Tell

Aenean lacinia bibendum nulla sed consectetur. Maecenas sed diam eget risus varius blandit sit amet non magna.

# Question 2: Regression

## 2a. The relationship

```{r}
#| label: fig-2a
#| fig-cap: "Lorem ipsum: least-squares line, with the predicted slope dashed."
reg <- tibble(x = runif(200, 0, 10), y = 12 + 2.4 * x + rnorm(200, 0, 4))
fit <- lm(y ~ x, data = reg)
ggplot(reg, aes(x, y)) +
  geom_point(alpha = 0.55) +
  geom_smooth(method = "lm", formula = y ~ x, se = TRUE, colour = ink, linewidth = 1) +
  geom_abline(intercept = 15, slope = 1.8, colour = accent, linetype = "dashed", linewidth = 0.9) +
  annotate("text", x = 0, y = 42, hjust = 0, colour = ink, size = 3.8, fontface = "bold",
           label = sprintf("Fitted slope: %.2f", coef(fit)[2])) +
  annotate("text", x = 0, y = 38.5, hjust = 0, colour = accentInk, size = 3.8,
           label = "Predicted slope: 1.8 (dashed)") +
  labs(title = "Lorem ipsum: the slope is steeper than predicted",
       subtitle = "200 random observations", x = "Wind speed (km/h)", y = "Something (units)")
```

```{r}
#| label: tbl-2a
#| tbl-cap: "Lorem ipsum: regression coefficients."
broom::tidy(fit) |>
  mutate(term = c("Intercept", "Wind speed (km/h)"),
         p.value = format.pval(p.value, eps = 0.001)) |>
  kable(digits = 3, col.names = c("Term", "Estimate", "Std. error", "t", "p-value")) |>
  kable_styling(full_width = FALSE)
```

## 2b. Conditions

```{r}
#| label: fig-2b
#| fig-cap: "Lorem ipsum: residuals against fitted values."
ggplot(broom::augment(fit), aes(.fitted, .resid)) +
  geom_hline(yintercept = 0, colour = ink2) +
  geom_point(alpha = 0.55) +
  labs(title = "Lorem ipsum: no pattern, no thickening",
       subtitle = "Residuals of the model in 2a", x = "Fitted value (units)", y = "Residual (units)")
```

Sed posuere consectetur est at lobortis. **Quantitative Variables Condition:** lorem ipsum. **Straight Enough Condition:** dolor sit amet. **Does the Plot Thicken?** Consectetur adipiscing elit.

# Question 3: Several groups at once

```{r}
#| label: fig-3
#| fig-cap: "Lorem ipsum: small multiples instead of a fifth colour."
seasons <- expand_grid(season = factor(c("Winter", "Spring", "Summer", "Autumn"),
                                       levels = c("Winter", "Spring", "Summer", "Autumn")),
                       day = 1:90) |>
  mutate(value = 40 + 25 * (season == "Winter") - 10 * (season == "Summer") +
           8 * sin(day / 9) + rnorm(n(), 0, 6))
ggplot(seasons, aes(day, value)) +
  geom_line(linewidth = 0.4) +
  geom_hline(data = summarise(seasons, m = mean(value), .by = season),
             aes(yintercept = m), colour = ink2, linetype = "dotted") +
  facet_wrap(~season, nrow = 1) +
  labs(title = "Lorem ipsum: winter sits well above the rest",
       subtitle = "Daily value by season, random data; dotted line = seasonal mean",
       x = "Day of season", y = "PM2.5 (µg/m³)")
```

```{r}
#| label: fig-3b
#| fig-cap: "Lorem ipsum: the theme's series colours, in order."
tibble(group = factor(rep(c("First", "Second", "Third", "Fourth"), each = 5), levels = c("First", "Second", "Third", "Fourth")),
       x = rep(2021:2025, 4), y = c(cumsum(runif(5, 1, 3)), cumsum(runif(5, 0.5, 2.5)),
                                    cumsum(runif(5, 0, 2)), cumsum(runif(5, 0, 1.5)))) |>
  ggplot(aes(x, y, colour = group)) +
  geom_line(linewidth = 1.1) + geom_point(size = 2.2) +
  labs(title = "Lorem ipsum: four series is the most one graph should carry",
       subtitle = "Random values, 2021–2025", x = "Year", y = "Value (units)")
```

# Question 4: In summary

Curabitur blandit tempus porttitor. Nullam quis risus eget urna mollis ornare vel eu leo. Etiam porta sem malesuada magna mollis euismod. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
````
