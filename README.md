<p align="center"><img src="docs/banner.svg" width="100%" alt="A report travelling back to its maker, drawn as a feedback loop in pixel icons, pale green on the left meeting deep indigo on the right at one diagonal seam. A tester's machine shows an alert. Its full story stays home in the machine's own inbox, while an agent passes only counts, ids, timings and blacked-out bars through a redacting gate. The resulting issue card crosses the seam, meets what was expected at a summing junction, and is filed at the head of a list of issues. The maker looks, fixes and checks, and the fix rides a release back along the bottom wire to the machine, where a pixel cat stands waiting."></p>

# pip-issues

**A repo for alpha testers.** It is for those who know. If you are running PIP, you already know what it is and how
you came to have it. This is where you tell its maker when it goes wrong. If you are not running PIP, there is nothing
here to install and nothing to follow.

PIP's code is not here, and it is not public. This repo holds reports and nothing else, so a machine that runs PIP but
holds none of its code can still send word back.

## What to report

A problem with a running PIP: something it did that it should not have, or did not do that it should. A route that
errors, a job that stops, a screen that breaks, a record that looks wrong after an action.

- **One issue per problem.** Two symptoms that may share a cause are still two issues until someone shows otherwise.
- **Already reported?** Add your evidence to the open issue rather than opening another. Another machine, version or
  frequency is useful evidence.
- **Report what you observed.** Do not guess at a cause or suggest a fix. Neither is visible from outside the code, and
  the observation is what can be reproduced.

## How to report

**With the PIP reporting skill**, which is the usual way. Tell your Claude session that something is wrong with PIP. The
skill:

1. gathers the evidence;
2. redacts it;
3. records the problem in your own PIP Inbox, where your own words may stay;
4. drafts the issue;
5. shows you the draft, and files it only when you say so.

Your Inbox item and the issue link to each other, so your machine keeps the full story and this repo gets only the
evidence.

**By hand.** Open a [new issue](https://github.com/Primatif/pip-issues/issues/new?template=problem.md) with the
*Problem with a running PIP* template and fill in its four sections: What happened, Version, Evidence and Left out.
Read the two lists below first.

## What an issue may contain: safe forensic evidence

Enough for the maker to reproduce and debug, and nothing that identifies anyone or anything in your instance's own
data:

- what was done, what was expected, what happened, how often, since when. Describe the action in general terms ("resolved
  an inbox item from the board");
- PIP's version: the commit or bundle build and `stale` from `/api/health`, the schema version, the Node version, the
  macOS version;
- `/api/health` output, and the failing call as method, route **pattern**, HTTP status and response time:
  `POST /api/inbox/:id/resolve`, never a real URL carrying other values;
- error messages and stack traces, with every data value replaced by `<redacted:kind>`;
- PIP's own ids (task numbers, note numbers, entity ids), counts, sizes, timings and timestamps. These mean nothing
  outside your instance;
- the names of launchd jobs, log files and settings keys involved, never their contents or values. Write paths as
  `~/pip/logs/<file>`, never as an absolute path that contains a user or client name.

## What an issue must never contain

- titles, bodies or any other text from inbox items, tasks, notes, journal entries or projects;
- names of people, clients, companies, accounts, boards or channels, and email addresses;
- ids or URLs from outside systems (monday, Azure DevOps, Gmail, Slack, Calendar);
- credentials, tokens, `.env` values or `instance.json` values;
- screenshots of the app showing real records.

## Redacting

Replace each value with `<redacted:kind>`, where kind says what it was: `title`, `body`, `person`, `client`, `email`,
`account`, `board-id`, `ticket-id`, `channel`, `url`, `path-under-home` or `token`.

When in doubt, leave it out, and say under **Left out** what you left out, by kind ("one task title, two person
names"). A report that says what it withheld is more useful than one that quietly says less.
