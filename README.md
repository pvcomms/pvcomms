Fourteen of the forty-four items in my own benchmark carried no information at all. Every model passed thirteen of them and every model failed one. I had already published the leaderboard.

I found that out by writing a tool to check, which is roughly the whole method here: build the instrument, point it at yourself, publish what it says.

---

I'm Param. I run the experiments on myself and file the reports — small systems, and essays about what constant machine mediation does to a mind. Bangalore, for now.

## What's here

**[error-bars](https://github.com/paramvaswani/error-bars)** — Wilson intervals, exact McNemar, item-information analysis, and a rank-stability bootstrap for benchmarks too small to support the rankings printed on them. Standard library, no dependencies. Bean et al. reviewed 445 AI benchmarks for NeurIPS 2025 and found 16% ran a statistical test of any kind; I was in the other 84% until I wrote this.

**[tool-selection-under-load](https://github.com/paramvaswani/tool-selection-under-load)** — What happens to an agent's tool choice as the menu grows. 7 models, 665 trials, 34 tools across three tiers, $5.07, zero API errors. The result that survives correction is GPT-5 Mini beating GPT-5 at every tier (p=0.0018) and GPT-5 being the only model that degrades as tools are added, by declining to call one. The rank order does not survive, and the README says so above the leaderboard.

**[bonp](https://github.com/paramvaswani/bonp)** — A signed-envelope protocol for biometric claims. I audited it against its own specification and found that every v1.0 signature was universally forgeable: the prescribed canonicalization used `JSON.stringify`'s replacer argument as if it were a key sort, which erased every nested object, so all envelopes hashed identically and one harvested signature validated any claim. v1.1 is RFC 8785 plus real Ed25519. The broken canonicalizer lives in the test suite so the defect stays pinned.

**[doordrop](https://github.com/paramvaswani/doordrop)** — A screen by the front door showing the delivery code, so the phone stays in the other room. ESP32 and an SSD1306, fed from the macOS Messages store. Rebuilding it revealed that the original sender filter was empty, which meant the device would have displayed bank OTPs and login codes to whoever was standing at the door. The firmware has never been flashed and the README says that in the third paragraph.

## The through-line

The work I'd actually defend is the negative results.

A tool-selection leaderboard whose top four are statistically indistinguishable — zero discordant pairs between first and second, meaning they gave identical answers on all 44 items. A settlement oracle where a prompt revision that reduced over-caution drove dangerous errors from one to five. A fleet of 26 scheduled agents that ran 557 times unattended between April and June and whose success rate fell from 50% to 27% to 19% as the connectors it depended on rotted underneath it. A protocol I designed, specified, implemented, and then broke.

None of that is a portfolio in the usual sense. It's the part I trust, because it's the part that cost something to find out.

I build instruments and then turn them on the thing that built them. Evals for the models. Statistics for the evals. An archive for the story I tell about the work. Each one exists because the layer under it turned out to be less trustworthy than it looked, including when the layer was me.

## The correction

For a stretch I routed everything through the machine. Every hour planned, every note processed, every decision handed over — including a proxy that read my overnight recovery score and rewrote the sampling temperature and thinking budget of the model I worked with the next day. Biology in, inference parameters out.

In April 2026 I stopped, hard. Months later I could say what had happened, and what I wrote down was: _both were positions the pendulum picked, not me._

That's the honest version. Not a realisation that arrived on schedule — a behaviour that changed first and a sentence that caught up four months afterwards. I'd rather describe it that way than claim I saw it coming, because I didn't.

The useful residue is a rule I can apply: automate the work, never the choice of which work is worth doing. Delegate cognition's logistics — scatter, triage, scaffolding. Don't delegate its judgment.

## How I work

- **Dissect the package.** What's said, how it's sold, and what actually arrives are three different things.
- **Keep the exit.** Any system you can't leave owns you.
- **Question the frameworks you question with.** Every instrument has assumptions baked in, especially the ones that feel like plain glass.
- **Credences, not vibes.** Numbers keep me honest about what I actually believe.

Standing contradictions I hold open on purpose: builds with AI and suspicious of AI; loves systems and distrusts platforms; craves order and trains for uncertainty.

## Also, mostly unpublished

Nine MCP servers I wrote and use daily — about 90 tools across Whoop, Vercel, Spaceship, and the Claude Code hook surface. They independently converged on the same three patterns, which is the part I find interesting: single-flight credential refresh, dry-run-by-default on anything irreversible, and one composite audit tool per server that fans out in parallel and returns a ranked action list naming the tool that fixes each finding.

A retrieval stack over my own reading. A daily dashboard that replaced five newsletters. A statistics course I wrote to teach myself enough to audit my own work, which is how the first paragraph of this page happened.

Most of that stays local. Not everything wants to be a repository.

---

_Writing at [paramv.com](https://paramv.com). Numbers above are current as of September 2026 and link to the data that produced them._
