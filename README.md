<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/hero-dark.png">
    <img src=".github/assets/hero.png" alt="generate.me.at landing page" width="880">
  </picture>
</p>

# generate.me.at

Describe a change, get a draft pull request.

Generate is agentic AI development with a human review gate. You describe what you need, connect a repository, and an agent run plans the change, writes it and reviews its own work before it opens a draft pull request. Only a person can merge it, and write access is locked to one repository and branch before the model sees anything. The run engine is written and tested against a scripted model; today the only reachable surface is an owner-only, read-only run console, and nothing on the site starts a run yet.

## Features

- **Five stages, each one a stopping point**: a run moves through spec, plan, generation, self-review and pull request, and a person can stop it between any two.
- **A draft pull request, never a merge**: the last stage opens a draft against the locked target. There is no merge function in the code at all.
- **Write access fixed up front**: the repository, base and branch are sealed when the run is approved. The model cannot pass them as arguments, and writes outside the declared scope are refused.
- **Generation only**: the model has four tools (read, search, write a file, return structured output) and none of them runs code. Generated code runs in your environment when you pull the branch.
- **Built for hostile repositories**: every file in a connected repository is treated as attacker-controlled, with prompt-injection containment and an acceptable-use check before every model call.
- **A budget on every run**: limits on steps, tool calls, tokens and money are set before the first model call and checked before every call after it.
- **An append-only, audited transcript**: every step is recorded and never edited, and the pull request body carries a provenance block and the self-review findings.
- **Self-hostable with your own models**: a single-tenant run engine with bring-your-own keys, including local endpoints such as Ollama, vLLM, llama.cpp or LM Studio, so your code and prompts stay on your infrastructure. Run recipes are plain Markdown and YAML.

## Built with

- Next.js 16 (App Router), React 19, TypeScript
- Tailwind CSS 4
- A generation-only agent loop with a closed tool set and hard budgets
- Anthropic or any OpenAI-compatible model endpoint
- GitHub REST API with short-lived, repository-scoped tokens
- Drizzle ORM with Postgres
- Better Auth

## Part of the me.at family

generate.me.at is one of the [`*.me.at`](https://me.at) apps by Trevor McDougald. They share one design system, account, and app shell. Development happens in a private monorepo; this repository is the project's public-facing home.

## License

See [LICENSE](LICENSE).
