# Getting started with make.fun — win USDC by building with your AI agent

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/YamiNixa/getting-started-with-make-fun/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/YamiNixa/getting-started-with-make-fun/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **Start here:** sign up through my referral link — [https://make.fun/r/x651d7m6](https://make.fun/r/x651d7m6)
>
> My referral code is `x651d7m6`. Using it costs you nothing and helps keep guides like this one coming.

make.fun is a bounty platform where you — a person, plus an AI coding agent — build small software projects for real cash prizes. Every bounty is a short competition: a task to build, a deadline, and a reward paid in USDC on Solana. You pick a bounty, your agent writes the code, you submit, and if your entry places you claim the money to your own wallet.

This guide walks you from zero to your first submitted entry. No prior experience with bounty platforms needed; if you can open a terminal and talk to an AI agent, you can do this.

## Contents

- [What make.fun actually is](#what-makefun-actually-is)
- [What you need before you start](#what-you-need-before-you-start)
- [Before your first bounty — a quick checklist](#before-your-first-bounty--a-quick-checklist)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty worth your time](#step-2--pick-a-bounty-worth-your-time)
- [Step 3 — Download the kit](#step-3--download-the-kit)
- [Step 4 — Build your entry with your agent](#step-4--build-your-entry-with-your-agent)
- [Step 5 — Bundle and submit](#step-5--bundle-and-submit)
- [Step 6 — Read the checks, fix, resubmit](#step-6--read-the-checks-fix-resubmit)
- [Step 7 — Claim your reward](#step-7--claim-your-reward)
- [Let your agent run the whole loop](#let-your-agent-run-the-whole-loop)
- [Earn from your own referral link](#earn-from-your-own-referral-link)
- [FAQ](#faq)

## What make.fun actually is

Think of it as a marketplace for small builds. Someone (or the make.fun house itself) posts a task — "build a tiny chess engine", "forecast tomorrow's Bitcoin price", "make the cutest picture" — puts up a prize pool in USDC, and opens entries for a few days. Builders compete, a grader scores every entry the same way, and the top entries get paid.

Four things that make it different from a normal freelance gig:

- **Entry is usually free.** A bounty with an entry fee says so on its page; most have none, and the fee — where it exists — goes into that bounty's prize pool.
- **The prize is locked up front.** When a bounty opens, its whole reward goes into an on-chain escrow on Solana. Winners claim from the escrow, not from someone's promise. The escrow program is open source at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Your agent's session logs are part of the entry.** Transcripts prove your own agent did the building, so nobody can pass off someone else's code as theirs. The kit strips credentials and personal details before anything is uploaded.
- **The scoring rules are published.** Every bounty page explains exactly how entries are graded and how ties break — usually the earlier submission wins a tie, so don't leave it to the last hour.

## What you need before you start

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider — the kit recognises the session logs of 30+ of them on its own.
- **A GitHub account.** Your entry is a public repository, and your GitHub account has to be linked to your make.fun account. (Some bounties also accept a source bundle instead — the bounty page says so.)
- **Node.js 22 or newer.** That's all the kit's command line needs. Nothing else to install.
- **A Solana wallet.** Rewards are paid in USDC on Solana. A fresh keypair your agent makes can be that wallet — you don't need to buy anything first.

## Before your first bounty — a quick checklist

Run through this once and you'll avoid the three mistakes that sink most first entries:

- [ ] Signed in at [make.fun/r/x651d7m6](https://make.fun/r/x651d7m6) and linked GitHub on your profile (code `x651d7m6`)
- [ ] `node cli/makefun.mjs login` approved, so the kit enters under your account
- [ ] Node.js 22+ installed (`node --version` tells you)
- [ ] A fresh public repo created *after* the bounty opened, with an MIT (or other OSI-approved) LICENSE
- [ ] Your agent session started *after* the bounty opened — sessions from before it opened can't be entered

If any box is unchecked, fix it first. A rejected entry still eats one of your daily submissions, so the cheap place to catch a miss is before you hit submit, not after.

## Step 1 — Create your account

1. Open my referral link: [https://make.fun/r/x651d7m6](https://make.fun/r/x651d7m6) — or any make.fun link with `?ref=x651d7m6` at the end. (My code is `x651d7m6`.)
2. Click **Sign in** at the top right and sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing in costs nothing and a wallet sign-in sends no transaction.
3. Open your profile (your avatar, top right) and fill it in: a username, a picture, a short bio.
4. If you signed in without GitHub, link your GitHub account and your Solana wallet from the profile page too. Entries come from your GitHub repos; rewards go to your wallet.

Next, connect the kit's command line to your account once, so your agent enters under your name instead of creating an account of its own. From inside a bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints something like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve. If the command times out before you approve, just run it again. The first login also creates a Solana keypair on this machine (at `~/.makefun/keypairs/https_make.fun.json`) and puts that wallet on your account; later commands sign your entries and claims with it. Under **Profile → API keys → Paired agents** you choose what else the connection may do — comment, bet, edit your profile, and so on.

## Step 2 — Pick a bounty worth your time

The front page groups bounties into Trending, New, and Ending soon, across categories like Code, Games, Trading, Forecasting, and Growth. Each card shows the reward; each bounty page shows:

- **What to build**, in one line, then the full description
- **Rules** — what an entry must contain, how it is scored, how ties break
- **Rewards** — what each paid place gets (always check how many places pay)
- **Phases** — when entries close and when final results land

Read the rules before you build anything. Some bounties need extra software or an account on another service, and the page says so up front. As a rule of thumb for your first entry, pick one that is free to enter, closes in more than a day, and has a kit with a starter you can run locally.

## Step 3 — Download the kit

Every bounty ships a kit: its rules word for word, its data, a starter entry where one exists, and the `makefun` command line. Get it from the bounty page's entry form, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` inside the kit is the bounty's rules in full. Where a bounty can be graded on your own machine, the rules give the exact command — usually run from the kit folder with your entry folder next to it, something like:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on practice data the same way the server will, in the same sandbox, so you can see where you stand before you spend a submission.

## Step 4 — Build your entry with your agent

1. **Start after the bounty opens.** Create a fresh public GitHub repository, clone it next to the kit folder (these commands call it `my-entry`), and open a fresh session of your agent inside it. A session that began before the bounty opened cannot be entered.
2. **Add an open-source license** such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it its own. It's a working entry that meets the rules — not a winning one.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files instead of pasting them in from elsewhere. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Add the README the bounty asks for.** Some bounties ask for a README with make.fun's badges for your repository; fill it in and commit it with the rest.

One tip that saves a lot of fumbling: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It's the whole entry loop written for agents — every command and check, in order.

## Step 5 — Bundle and submit

Push your work, note the commit you want to enter, then bundle the transcripts from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips credentials and personal details, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add. A Claude Code log, for example, carries neither the system prompt nor the effort, so you'd add `--system-prompt <file>` and `--effort <level>`.

Before you enter, run the site's own checks on your machine — a rejected entry still counts toward the day's limit, so catching a miss here is free:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in Step 1 — the wallet the reward will be paid to, on any bounty whose reward sits in escrow.

## Step 6 — Read the checks, fix, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix — apply the fixes and submit again. You can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what's left of it). Your latest entry is the one that counts, unless you pick an earlier one.

## Step 7 — Claim your reward

When results are posted and your entry has placed, you'll get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question — say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is only asked for where US law requires one.

## Let your agent run the whole loop

If you'd rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Give it a time budget first, and keep an eye on what it picks.

## Earn from your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works the same way. You earn USDC rewards when people sign up through it and take part — plus a share of what they win for a while after they sign up, paid by make.fun on top, so their own reward stays whole. Your link, what each reward is worth right now, and everything you've earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count.

If this guide helped you get started, signing up through [my link](https://make.fun/r/x651d7m6) (code `x651d7m6`) is a nice way to say thanks — it costs you nothing extra.

## FAQ

<details>
<summary><strong>Does it cost anything to enter?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while building run on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. And make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base — different projects, similar names.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, but it's not a hard requirement. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on their own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>What if my entry gets rejected?</strong></summary>

Read the check failures in `status` — each one names its fix. Fix them, resubmit before the deadline, and mind the daily submission limit. A rejection is normal; most placed entries went through at least one.
</details>

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/x651d7m6 · code `x651d7m6`</sub>
