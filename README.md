# Claude Code Skills by OMX

Nine small, free Claude Code skills for the jobs that quietly go wrong between "it works on my machine" and "the client is happy". Each one is a `SKILL.md` for Claude plus a small command-line tool you can run on its own (eight in standard-library Python, one in Node.js with Playwright). No API keys, no paid services, and every bundled example is synthetic.

## The tools

| Tool | What it does |
|---|---|
| [readme-quickstart-tester](https://github.com/OmxKamesh/readme-quickstart-tester) | Replays a repo's documented quickstart from a clean snapshot, records the first failure, proposes a minimal fix and verifies it with a fresh replay. |
| [idempotency-tester](https://github.com/OmxKamesh/idempotency-tester) | Checks whether a webhook or queue event arriving twice, or out of order, causes duplicate, missing or stale side effects. |
| [excel-reconcile-tool](https://github.com/OmxKamesh/excel-reconcile-tool) | Reconciles opening stock or invoice balances, movements and closing balances in CSV (exported from Excel or Google Sheets), and points to the exact row where a unit went missing. |
| [marketing-claim-checker](https://github.com/OmxKamesh/marketing-claim-checker) | Turns launch or marketing claims into an evidence ledger: supported, contradicted or unknown. |
| [repo-handover-checklist](https://github.com/OmxKamesh/repo-handover-checklist) | Maps what a repository is missing before handover: setup, tests, ownership, recovery. Never runs project code. |
| [requirements-diff](https://github.com/OmxKamesh/requirements-diff) | Compares two versions of a client's requirements and shows exactly what was added, removed, reassigned or moved. |
| [playwright-e2e-tester](https://github.com/OmxKamesh/playwright-e2e-tester) | Replays a customer journey in a real browser on your local or staging app and checks the result was actually saved, not just that a "Saved!" message appeared. |
| [webhook-tester](https://github.com/OmxKamesh/webhook-tester) | Fires duplicate, reordered, concurrent and timeout-after-write webhooks at your local or staging receiver and checks the real side effects through a separate readback. |
| [supabase-rls-tester](https://github.com/OmxKamesh/supabase-rls-tester) | Uses two synthetic accounts and four read-only requests to check user A can't read user B's record in your authorized local or staging Supabase app. |

## Install a skill in Claude Code

1. Clone the tool's repository, for example:

   ```sh
   git clone https://github.com/OmxKamesh/requirements-diff
   ```

2. Copy the skill folder (the `SKILL.md` together with its `scripts/` and `references/` folders) into one of:
   - `~/.claude/skills/<skill-name>/` to use it in every project, or
   - `.claude/skills/<skill-name>/` inside a single project.

   For `readme-quickstart-tester`, the skill folder is `skills/first-run/`. For the others, it is the repository root. For `webhook-tester` and `supabase-rls-tester`, copy the whole repository, because the Python package sits next to `SKILL.md`. For `playwright-e2e-tester`, also run `npm install` and `npx playwright install chromium` inside the skill folder.

3. Start Claude Code and invoke it explicitly by its skill name, for example `/scope-diff before.json after.json`. Skill names: `first-run`, `retry-proof`, `sheet-reconcile`, `promise-check`, `handoff-pack`, `scope-diff`, `customer-path-proof`, `webhook-tester`, `supabase-rls-tester`. The skills are user-invoked only, so Claude will not run them on its own.

Each repository's README has the exact install steps, requirements (Python 3.9+ or 3.10+ for the Python tools, Git for readme-quickstart-tester and repo-handover-checklist, Node.js 20+ for playwright-e2e-tester) and limits.

## Use a skill in claude.ai

1. Turn on code execution in claude.ai settings (skills need it to run their scripts).
2. Zip the skill folder so `SKILL.md` sits at the top level of the zip, along with `scripts/` and `references/`.
3. In claude.ai, open Customize, then Skills, then upload the zip.

claude.ai limits a skill description to 200 characters. If an upload is rejected, shorten the `description:` line in that skill's `SKILL.md` before zipping.

## Run without Claude

Every tool also works without Claude. The eight Python tools need no pip installs; playwright-e2e-tester needs only its free npm dependency (Playwright). See the "try it" section in each repository's README.

## License

MIT, see [LICENSE](LICENSE). Each tool repository carries its own MIT license.

---

Built by Kamesh Jindal at [OMX Digital](https://omxdigital.ai). Need this set up for your business? [kamesh@omxdigital.ai](mailto:kamesh@omxdigital.ai)
