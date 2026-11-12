# Stratum

PR review and triage for open-source maintainers, on a model you run yourself.

Maintainers now get pull requests faster than they can read them, and many are generated. [**Stratum Open**](https://github.com/stratum-org/stratum-open) reads each PR first, flags what's risky and sorts the queue, so your review time goes to the PRs that deserve it. It runs on small open models (7–14B) on hardware you control. Nothing is sent to Stratum: there's no account, no telemetry and no license check.

## What it does on each PR

- **Runs checks that need no model.** These catch secrets; `eval`, shell commands and SQL built from strings; and workflow changes that hand out a write token. They also catch new, typo-squatted or nonexistent packages, edits to files that steer coding agents, and hidden Unicode.
- **Has the model review the PR.** You get a summary of what the PR does and whether it matches its description, plus inline comments with fixes you can commit. Each push reviews only what changed.
- **Applies one triage label:** `ready`, `needs work`, `low effort` or `needs a maintainer`, with the reasons spelled out. Labels are off until your policy turns them on.
- **Builds a triage queue.** One issue lists every open PR, with the cheapest to review and best supported first.

Your rules live in `.stratum/policy.yml` in your own repo.

## Try it

Copy [`examples/stratum.yml`](https://github.com/stratum-org/stratum-open/blob/main/examples/stratum.yml) to `.github/workflows/stratum.yml`. It runs `qwen2.5-coder:7b` with Ollama on GitHub's own runner, so you don't need a server.

You can also run Stratum Open as a GitHub App on your own server, or as a CLI that reviews your branch before you open a PR. See the [README](https://github.com/stratum-org/stratum-open#readme) for both.

## Contributing

Stratum Open is early, and it works end to end on GitHub. Issues and PRs are welcome; see [CONTRIBUTING.md](https://github.com/stratum-org/stratum-open/blob/main/CONTRIBUTING.md). Please report security issues as described in [SECURITY.md](https://github.com/stratum-org/stratum-open/blob/main/SECURITY.md). Stratum Open is licensed under [AGPL-3.0](https://github.com/stratum-org/stratum-open/blob/main/LICENSE).
