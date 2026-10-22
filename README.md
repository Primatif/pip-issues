# pip-issues

Where problems with a running PIP are reported. One issue per problem.

PIP's code lives in `Primatif/pip-fullstack-app` (private). This repo holds only reports, so a machine that runs PIP
but holds none of its code can still tell the developer what went wrong.

## What an issue may contain: safe forensic evidence

Enough for the developer to reproduce and debug, and nothing that identifies anyone or anything from the instance's
own data:

- what was done, what was expected, what happened, how often, since when;
- PIP's version: the commit or bundle build from `/api/health`, the schema version, the Node version, macOS version;
- `/api/health` output and the failing route, method and HTTP status;
- error messages and stack traces, with any data value replaced by `<redacted:kind>`;
- PIP's own ids (task numbers, note numbers, entity ids), counts, sizes, timings and timestamps;
- the names of launchd jobs, log files and settings keys involved, never their values.

## What an issue must never contain

- titles, bodies, notes or any text from inbox items, tasks, notes, journal entries or projects;
- names of people, clients, companies, accounts, boards, channels or email addresses;
- ids from outside systems (monday, ADO, Gmail, Slack, Calendar);
- credentials, tokens, `.env` or `instance.json` values;
- screenshots of the app showing real records.

When in doubt, leave it out and say what was left out ("one task title redacted").

Reports are written by the `report-pip-issue` skill (in `Primatif/key-pip-claude`, published to the global Claude
config), which also records the problem in the instance's own PIP inbox.
