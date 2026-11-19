# github-achievements-lab

Sandbox repo for earning GitHub profile achievements and keeping the contribution graph active.
Owner account: **Anotida28**.

## Achievements

| Badge | Status | How |
|---|---|---|
| YOLO | Earned | PR #2 merged without a review |
| Quickdraw | Earned | Closed an issue/PR within 5 minutes of opening it |
| Pull Shark | Pending (1st tier: 2 merged PRs) | PRs #2–#7 merged. Next tier needs 16 |
| Pair Extraordinaire | Pending | PR #3 has a commit with a `Co-Authored-By: Claude` trailer. Backup plan: co-author with the second GitHub account's noreply email |
| Galaxy Brain | Not started | Needs 2 accepted answers in Discussions. Plan: enable Discussions, ask from the second account, answer from Anotida28, mark as answer from the second account |
| Starstruck | Not possible solo | Needs 16 stars from other people |

## Automatic daily commits

A GitHub Actions workflow commits to this repo automatically so the contribution graph stays green.

- **Workflow:** [`.github/workflows/daily-commit.yml`](.github/workflows/daily-commit.yml)
- **Log file:** [`activity.md`](activity.md). Each commit adds one timestamped line.
- **Schedule:** 6 runs a day at 02:23, 06:23, 10:23, 14:23, 18:23 and 22:23 UTC (add 2 hours for Harare).
- **Randomness:** each run has a 50% chance of making 1–3 commits, otherwise it does nothing. About 6 commits a day on average.
- **No empty days:** if nothing has been committed by the 22:23 UTC run, that run always commits.
- **Manual run:** Actions tab → Daily commit → Run workflow. Manual runs always make 1–3 commits.
- **Author:** `Anotida28 <162551120+Anotida28@users.noreply.github.com>`, so the commits count on the profile graph.

### Things to know

- The bot pushes to `main` every day. Run `git pull` before working here locally, or your push will be rejected.
- GitHub may turn off scheduled workflows in public repos after 60 days with no activity. If it stops, go to the Actions tab and click **Enable workflow**.
- Make changes through PRs that you merge yourself. Each merged PR counts toward the next Pull Shark tier.

## `ach` terminal command

[`bin/ach`](bin/ach) manages this repo from any directory. It's linked into the PATH with:

```bash
ln -sf ~/Projects/archive/github-achievements-lab/bin/ach ~/.local/bin/ach
```

| Command | What it does |
|---|---|
| `ach status` | Workflow state, last 5 runs, bot commits today, merged PR count |
| `ach run` | Trigger the commit workflow now, wait for it, then pull |
| `ach pr "message"` | Add a line to `notes.md`, open a PR and merge it (counts toward Pull Shark) |
| `ach pull` | Pull the latest `main` |
| `ach on` / `ach off` | Enable or disable the daily workflow |
| `ach open` | Open the repo on GitHub |
