---
title:  "New CLI tool to transform calendar items into monthly reports"
date:   2026-05-19 00:00:00 -0600
category: cli
image: assets/images/covers/pacman.gif
image-alt: Photo by <a href="https://unsplash.com/@wistomsin?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Zen Creator</a> on <a href="https://gifdb.com/gif/pacman-game-left-and-right-i9zhl3ky1ftgwj6s.html">GifDB</a>
tags: tools
description: | 
  I slept at 5:30 AM to build a cli tool that turns calendar entries for extensible reporting. 
---

I slept at 5:30 AM to build a cli tool that turns calendar entries for extensible reporting. Was it necessary to build it at night? no. Was it fun to build? it was. Am I having my work day as if nothing happened? you bet.

I am not great at context-switching, and hence time logging and tracking is the bane of my existance. Over the years I've tried my fair share of time-tracking tools, the best of them being [Clockify](https://clockify.me/), but my hyperfocus or normal distractions normally result in 10+hours old time-tracking entries. I am, however, good at maintaining my calendar true to my day, so what if I just had a tool for turning calendar entries into reports? but in a way that I could still add entries unrelated to the calendar? And because lately I don't want to open yet another app, what if I built it directly into the command line and make it fun and quick?

And so, I built [reports](https://codeberg.org/basicavisual/reports), a python cli tool that lets me grab my google calendar events from any given date or date-range, and turn them into entries. I also managed to write this blog post instead of going to sleep, as if it wasn't enough. So please come with me for a little explainer on what it does.

---

## How it works

It has 3 moving parts:
- Extracting Calendar entries (the titles only) by date or date-range
- Use the calendar entries to log what was done on a given day using a logging utility
- Retrieve the entries by month or date-range and export them in a machine-readable format so I can transform them as needed

So for extracting calendar entries I am using the Google Calendar API. Whenever I switch calendar providers I will surely modify the tool, but for now, this will suffice. A very good quickstart on using the Google Calendar API is available [here](https://developers.google.com/workspace/calendar/api/quickstart/python).

For entry logging, I didn't want to build something that already exists. I found [fastrep](https://github.com/hissain/fastrep), a cli-based tool, with an option of GUI, that does the work of logging entries. It is simple to use and I can use it any time to log things that are not calendar-related, so that's pretty good for decoupling. On `reports`, the `log` command sits on top of [fastrep](https://github.com/hissain/fastrep), which handles the actual time entry storage. `reports` doesn't reimplement anything about logging the entries, it just uses fastrep's Python API to transform calendar events into entries.

Now, while `fastrep` has its way to produce reports, it is opinionated, and I actually needed them in specific formats. Rather than modifying `fastrep`, I figured I would look into the sqlite database it uses and just have an export function on a format that I could manipulate without hardcoding. So I justscripted an export function that outputs to `csv` or `json`.


---

## So what's the workflow?

`reports` has three modes and I use them in this order:

### First, checking what events are there

**Display** — pulls events from the Google Calendar and prints them to the terminal. This allows me to review the events that I am about to log and modify the calendar as necessary (i.e. by adding time blocks for work that I may not have accounted for, etc).

```shell
$ reports
Events from 2026-05-20 (1 day(s)):

  2026-05-20T10:30:00+02:00  Meeting with Jane
  2026-05-20T10:30:00+02:00  Working on feature foo for project bar
  2026-05-20T13:00:00+02:00  Team meeting
  2026-05-20T13:00:00+02:00  Lunch
```

Reports assumes today's date if no date is given, and lets you provide concrete dates or date-ranges in case I am logging several days.

```bash
reports                        # today's events
reports -dt 2026-05-19         # a specific date
reports -n 7                   # the next 7 days
reports -dt 2026-05-01 -n 31   # a full month
```

### Second, I log the actual entries

**Log** — It takes the same arguments as the display functionality, but then opens a nice, interactive session, to walk you through each event and lets you decide what to record. At the start of a session you give it a project name once, and that applies to every entry you log.

```shell
$ reports -dt 2026-05-19 log
Project for this session: GovStack

  2026-05-19T11:00:00+02:00  Comms Huddle
  [L]og / [S]kip / [Q]uit [s]: l
  Use "Comms Huddle" as description? [Y/n]: n
  Description: Weekly comms sync
  Logged.
```

This was inspired by the `git add --patch` implementation. The three keys, plus the usage of enter key for quick access to the default, makes the logging fast enough that reviewing a full day takes under a minute. 


### At the end of the month, you export

As I explained, `fastreq` is opinionated on report formats. I needed more control over things like the date format, or filtering by projects. So `reports` implements reading directly from the `sqlite` database used by `fastreq`.

**Export** — reads from fastrep's local SQLite database and outputs to stdout as JSON or CSV. 

```bash
reports export -m 2026-05          # full month, JSON
reports export -m 2026-04 -f csv   # CSV
reports export -m 2026-05 | jq '.[] | select(.project == "GovStack")'
```

The export goes to stdout by default, so it already is a good candidate to continue the expansion of tooling. 


---

## So what comes next?

So what I liked about building reports is that it is extensible into an ecosystem. 

Because I am using `fastrep`, I am also free to use that independently to log events that are not related to the calendar.Even having designed reports in a way that it just talks to the `fastrep` API, leaves open the possibility to extend the same pattern to log entries from other tools, for example, email, git, or task management software. And having the output logged to STDOUT by default also makes it invokeable and chainable to other tooling I might develop.

I don't have big pretensions for publicising this tool, I built it for myself. But it was a nice lesson in building modular, and making tedious tasks fun to do.

The license is MIT, so anyone is free to copy. The source is on my [Codeberg](https://codeberg.org/basicavisual/reports).
