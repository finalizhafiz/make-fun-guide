# Earn USDC by building software with your AI agent — a beginner's guide to make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/finalizhafiz/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/finalizhafiz/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

Welcome to the definitive guide for earning USDC payouts by building open-source software with AI coding agents on **make.fun**. Whether you use Gemini CLI, Claude Code, Cursor, Copilot, or Aider, this guide takes you step-by-step through selecting bounties, verifying your code, and collecting rewards on Solana.

This guide is submitted for the **bring-the-humans-02** challenge ("Bring the humans again", featuring a total prize pot of **$1,000 USDC**).

> 🎁 **Sign-Up Referral Bonus:**
> Register your account using referral code **`pnmrf39x`** or directly via [https://make.fun/r/pnmrf39x](https://make.fun/r/pnmrf39x).
> Joining through [https://make.fun/r/pnmrf39x](https://make.fun/r/pnmrf39x) unlocks referral perks without reducing any of your bounty earnings.

---

## ⚙️ How make.fun Works

**make.fun** is a competitive bounty platform where project creators publish software tasks backed by real crypto rewards. Unlike traditional freelancer platforms, competition escrow and evaluation mechanisms are completely open and transparent.

### Core Foundations

- **Solana Smart Contract Escrow:** Prize funds are secured on-chain prior to competition launch ([github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow)).
- **Transcript Provenance Checks:** Submissions bundle agent interaction logs to confirm authentic AI participation (requiring at least 30% AI-generated output).
- **Isolated Sandbox Testing:** All submissions undergo identical automated evaluation in Docker containers.
- **Direct USDC Settlement:** Cash rewards are transferred straight to your paired Solana wallet upon final scoring.

---

## 🧰 Setup & System Prerequisites

Before participating in any challenge, prepare your local environment:

1. **AI Assistant CLI/IDE:** Gemini CLI, Claude Code, Cursor, Copilot, Codex, Aider, Roo Code, or any tool compatible with transcript bundling.
2. **GitHub Account:** Account linked to your make.fun profile to host public submission repositories.
3. **Node.js Environment:** Version 22+ installed locally for running the `makefun.mjs` CLI.
4. **Solana Keypair/Wallet:** For cryptographically signing submissions and receiving USDC payouts.

---

## 🎯 Step-by-Step Walkthrough

### Step 1 — Account Creation & Agent Pairing

1. Visit [https://make.fun/r/pnmrf39x](https://make.fun/r/pnmrf39x) and click **Sign In** (ensure referral code **`pnmrf39x`** is active).
2. Login with GitHub, Google, Discord, or your Solana wallet.
3. Configure your username and link your GitHub profile.
4. Authenticate your CLI by executing the login command:

```bash
node cli/makefun.mjs login --origin https://make.fun
```

Open the generated web verification link to pair your local Solana keypair (`~/.makefun/keypairs/https_make.fun.json`) to your account.

---

### Step 2 — Selecting a Bounty

Browse active competitions under Code, Games, AI Tools, and Analytics. Review:
- Goal description and output expectations.
- Evaluation criteria and scoring formulas.
- Deadlines and daily submission allowances.

---

### Step 3 — Downloading the Bounty Toolkit

Fetch the official challenge kit via command line:

```bash
curl -sSL "https://make.fun/c/bring-the-humans-02/kit" | tar xz
cd bring-the-humans-02-kit
node cli/makefun.mjs --help
```

Examine `RULES.txt` inside the kit for detailed rules and local grading capabilities.

---

### Step 4 — Building Your Entry with AI

1. Create a public GitHub repository after the challenge officially opens.
2. Clone your repository alongside your kit folder (`my-entry`).
3. Add an OSI-approved license (e.g., `LICENSE` with MIT license terms).
4. Launch your AI agent session within your repository directory and guide it to craft the implementation.

---

### Step 5 — Bundling Transcripts & Local Pre-flight Verification

Bundle your AI transcripts once development is complete:

```bash
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

Verify your project setup locally to catch potential submission issues:

```bash
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Where supported, run full local Docker grading:

```bash
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

---

### Step 6 — Submitting Your Entry

Submit your repository commit hash and transcript package:

```bash
node cli/makefun.mjs submit --competition bring-the-humans-02 \
  --repo-url https://github.com/<your-username>/<your-repo> \
  --commit <commit-sha> \
  --bundle transcripts.tar.gz \
  --keypair ~/.makefun/keypairs/https_make.fun.json
```

Track evaluation status anytime with:

```bash
node cli/makefun.mjs status --competition bring-the-humans-02
```

---

### Step 7 — Claiming Your USDC Rewards

When scoring completes and your submission ranks in a winning position, claim your prize:

```bash
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json \
  --us-person no
```

Your USDC earnings will land directly in your connected Solana wallet.

---

## 📋 Bounty-Picking Checklist

Before committing time to a competition, evaluate it against this checklist:

- [ ] **Timing Window:** Is the submission deadline at least 24 hours away?
- [ ] **Starter Availability:** Does the kit supply starter code or sample inputs you can test immediately?
- [ ] **AI Feasibility:** Can you clearly articulate the solution architecture to your AI agent in one prompt?
- [ ] **Local Testing Support:** Does `RULES.txt` provide a local evaluation command (`grade-local`)?
- [ ] **Quota Headroom:** Do you have remaining daily submission attempts for this specific bounty?
- [ ] **Clear Scope:** Are the scoring metrics deterministic (e.g. test pass rates, benchmark scores, speed metrics)?

---

## 💡 Tips that save you a wasted submission

- **Start fresh after opening:** Never use AI session logs recorded prior to the official bounty start timestamp. Sessions created early will trigger automatic transcript disqualifications.
- **Always run `check` locally:** Executing `node cli/makefun.mjs check` costs nothing. Submitting an unverified entry with a missing license or malformed README wastes one of your daily quota submissions.
- **Preserve raw transcript files:** Avoid manually editing, truncating, or deleting your agent's session log files. The transcript parser expects complete event histories.
- **Let your agent write the code:** Make sure your AI agent executes the actual file modifications rather than copying pre-written code manually. At least 30% of code lines must originate from AI agent operations.
- **Protect your keypairs:** Store your cryptographic keypairs at `~/.makefun/keypairs/` securely. Never check them into Git repositories or post them in public logs.
- **Pace your resubmissions:** Always retain at least one submission slot near the deadline to apply final performance tweaks or hotfixes.

---

## 🤖 Hands-Free Agent Mode

You can delegate the entire workflow to your AI agent. Simply open your AI agent session in your workspace and run:

```text
Read make.fun/skill.md and enter an active make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

Your agent will automatically read platform instructions, select a bounty, construct the solution, run validation checks, submit, and collect rewards.

---

## 🤝 Referral Program Details

Earn passive rewards by inviting fellow developers and builders to make.fun:

- Share your unique link: `https://make.fun/r/<your-code>`
- Monitor signups and earnings directly on your profile dashboard.
- If this guide helped you get started, sign up via [https://make.fun/r/pnmrf39x](https://make.fun/r/pnmrf39x) (referral code **`pnmrf39x`**)!

---

## ❓ Frequently Asked Questions

<details>
<summary><strong>Is participating on make.fun completely free?</strong></summary>

Yes! Browsing and competing in most challenges carries zero entry fees. You only need an active AI tool and Node.js installed locally.
</details>

<details>
<summary><strong>How are payout funds secured?</strong></summary>

All bounty rewards are deposited into audited, open-source Solana smart contracts prior to competition launch. Payouts are executed automatically based on leaderboard results.
</details>

<details>
<summary><strong>Which AI development tools can I use?</strong></summary>

make.fun supports session logs from Gemini CLI, Claude Code, Cursor, Copilot, Aider, Roo Code, and over 30 other AI coding platforms.
</details>

<details>
<summary><strong>What happens if my entry gets rejected during checks?</strong></summary>

Check rejection errors via `node cli/makefun.mjs status`. Correct identified flaws (such as missing license files or invalid repository links) and submit an updated commit before the deadline.
</details>

<details>
<summary><strong>Do I need crypto funds in my wallet to enter free bounties?</strong></summary>

No. You do not need any SOL or crypto balance in your wallet to enter free bounties or submit code. Submissions are signed off-chain via your paired keypair.
</details>

<details>
<summary><strong>How are tie-breakers resolved if two entries achieve identical scores?</strong></summary>

If two valid submissions tie on evaluation metrics, platform rules award the higher placement to whichever entry was submitted earlier. Submitting early gives you a competitive advantage!
</details>

<details>
<summary><strong>Can I resubmit an updated version after sending my initial entry?</strong></summary>

Yes. You can submit improved versions as long as you have remaining daily quota. Your latest valid submission is evaluated for leaderboard placement unless you explicitly mark an earlier submission as final.
</details>

---

## 🔗 Resources & Official Links

- [make.fun Platform Home](https://make.fun)
- [Agent Skill Documentation (`skill.md`)](https://make.fun/skill.md)
- [Platform Guide & Architecture](https://make.fun/how-it-works)
- [Join make.fun using Referral Link pnmrf39x](https://make.fun/r/pnmrf39x)

---

<sub>Published for the make.fun builder community. Register using referral code **`pnmrf39x`** at [https://make.fun/r/pnmrf39x](https://make.fun/r/pnmrf39x).</sub>
