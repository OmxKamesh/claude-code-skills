# OMX Claude Skills Toolkit

Seven small, free Claude Code skills for the jobs that quietly go wrong between "it works on my machine" and "the client is happy". Each one is a `SKILL.md` for Claude plus a small command-line tool you can run on its own (six in standard-library Python, one in Node.js with Playwright). No API keys, no paid services, and every bundled example is synthetic.

## The tools

| Tool | What it does |
|---|---|
| [first-run-skill](https://github.com/OmxKamesh/first-run-skill) | Replays a repo's documented quickstart from a clean snapshot, records the first failure, proposes a minimal fix and verifies it with a fresh replay. |
| [retry-proof](https://github.com/OmxKamesh/retry-proof) | Checks whether a webhook or queue event arriving twice, or out of order, causes duplicate, missing or stale side effects. |
| [sheet-reconcile](https://github.com/OmxKamesh/sheet-reconcile) | Reconciles opening stock or invoice balances, movements and closing balances in CSV, and points to the exact row where a unit went missing. |
| [promise-check](https://github.com/OmxKamesh/promise-check) | Turns launch or marketing claims into an evidence ledger: supported, contradicted or unknown. |
| [handoff-pack](https://github.com/OmxKamesh/handoff-pack) | Maps what a repository is missing before handover: setup, tests, ownership, recovery. Never runs project code. |
| [scope-diff](https://github.com/OmxKamesh/scope-diff) | Compares two versions of a client's requirements and shows exactly what was added, removed, reassigned or moved. |
| [customer-path-proof](https://github.com/OmxKamesh/customer-path-proof) | Replays a customer journey in a real browser on your local or staging app and checks the result was actually saved, not just that a "Saved!" message appeared. |

## Install a skill in Claude Code

1. Clone the tool's repository, for example:

   ```sh
   git clone https://github.com/OmxKamesh/scope-diff
   ```

2. Copy the skill folder (the `SKILL.md` together with its `scripts/` and `references/` folders) into one of:
   - `~/.claude/skills/<skill-name>/` to use it in every project, or
   - `.claude/skills/<skill-name>/` inside a single project.

   For `first-run-skill`, the skill folder is `skills/first-run/`. For the others, it is the repository root. For `customer-path-proof`, also run `npm install` and `npx playwright install chromium` inside the skill folder.

3. Start Claude Code and invoke it explicitly, for example `/scope-diff before.json after.json`. The skills are user-invoked only, so Claude will not run them on its own.

Each repository's README has the exact install steps, requirements (Python 3.9+ or 3.10+ for the Python tools, Git for first-run and handoff-pack, Node.js 20+ for customer-path-proof) and limits.

## Use a skill in claude.ai

1. Turn on code execution in claude.ai settings (skills need it to run their scripts).
2. Zip the skill folder so `SKILL.md` sits at the top level of the zip, along with `scripts/` and `references/`.
3. In claude.ai, open Customize, then Skills, then upload the zip.

claude.ai limits a skill description to 200 characters. If an upload is rejected, shorten the `description:` line in that skill's `SKILL.md` before zipping.

## Run without Claude

Every tool also works without Claude. The six Python tools need no pip installs; customer-path-proof needs only its free npm dependency (Playwright). See the "try it" section in each repository's README.

## License

MIT, see [LICENSE](LICENSE). Each tool repository carries its own MIT license.

---

Built by Kamesh Jindal at [OMX Digital](https://omxdigital.ai). Need this set up for your business? [kamesh@omxdigital.ai](mailto:kamesh@omxdigital.ai)
