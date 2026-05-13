# BskyR Tutorial

This repository contains a beginner-friendly R Markdown tutorial for using the [`bskyr`](https://cran.r-project.org/package=bskyr) package to work with Bluesky data from R.

The main tutorial file is:

```text
BskyR_extended_tutorial_no_pipes.Rmd
```

The tutorial is written for new R users. It avoids pipeline-style code and shows each step separately so that the purpose of every line is easier to understand.

## What this tutorial covers

The tutorial introduces practical `bskyr` workflows, including:

- installing and loading `bskyr`
- authenticating with a Bluesky handle and app password
- retrieving account profile details
- searching public Bluesky posts
- extracting post text from search results
- collecting posts from a specific account
- paginating account posts
- retrieving followers and follows
- comparing followers and following accounts
- searching for Bluesky accounts
- retrieving suggested accounts
- reading the authenticated user's timeline
- retrieving liked posts
- checking likes, reposts, quotes, and threads for a post
- retrieving notifications and account preferences
- exporting collected data to CSV and RDS files
- performing simple text analysis
- creating a basic engagement plot
- posting, liking, reposting, following, and blocking safely
- creating a reusable account report workflow

## Why this tutorial is useful

`bskyr` connects R to Bluesky's AT Protocol API. It returns many results as tidy tables, which makes it useful for:

- social media analysis
- public discussion tracking
- hashtag or keyword monitoring
- account-level analysis
- follower and following comparison
- basic engagement analysis
- teaching API-based data collection in R

## Requirements

You need R and the following R packages:

```r
install.packages("bskyr")
install.packages("dplyr")
install.packages("tidyr")
install.packages("purrr")
install.packages("stringr")
install.packages("readr")
install.packages("ggplot2")
```

The tutorial loads the main packages at the start of the R Markdown file. `ggplot2` is loaded later in the plotting section.

## Authentication

To use authenticated `bskyr` functions, you need:

1. your Bluesky handle, without the `@` symbol
2. a Bluesky app password

Use an app password instead of your normal Bluesky account password. App passwords can be created and revoked from Bluesky settings.

Example:

```r
set_bluesky_user("yourhandle.bsky.social")
set_bluesky_pass("your-app-password")

active_session <- bs_auth(
  user = bs_get_user(),
  pass = bs_get_pass()
)
```

Do not commit your real app password to GitHub.

## How to use the tutorial

Open the R Markdown file in RStudio:

```text
BskyR_extended_tutorial_no_pipes.Rmd
```

Then run the chunks one by one.

Many chunks use:

```r
eval = FALSE
```

This means the code is shown but not executed automatically when the file is knitted. This is intentional, especially for chunks that could modify your Bluesky account.

## Safety notes

Some `bskyr` functions only read data. Others change your account state.

Read-only examples include:

- `bs_get_profile()`
- `bs_search_posts()`
- `bs_get_author_feed()`
- `bs_get_followers()`
- `bs_get_follows()`
- `bs_get_timeline()`
- `bs_get_post_thread()`

Account-changing examples include:

- `bs_post()`
- `bs_like()`
- `bs_repost()`
- `bs_follow()`
- `bs_block()`
- `bs_unlike()`
- `bs_unfollow()`
- `bs_unblock()`

Keep account-changing chunks as `eval=FALSE` unless you intentionally want to run them.
