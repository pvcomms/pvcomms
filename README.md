Fourteen of the forty-four items in my own benchmark carried no information at all. Every model passed thirteen of them and every model failed one. I had already published the leaderboard.

I found that out by writing a tool to check, which is roughly the whole method here: build the instrument, point it at yourself, publish what it says.

---

I'm Param. I run the experiments on myself and file the reports — small systems, and essays about what constant machine mediation does to a mind. Bangalore, for now.

## Measurement

**[error-bars](https://github.com/pvcomms/error-bars)** — Wilson intervals, exact McNemar, item-information analysis and a rank-stability bootstrap, for benchmarks too small to support the rankings printed on them. Standard library, no dependencies. Bean et al. reviewed 445 AI benchmarks for NeurIPS 2025 and found 16% ran a statistical test of any kind; I was in the other 84% until I wrote this.

**[auditing-my-own-evals](https://github.com/pvcomms/auditing-my-own-evals)** — the statistics I taught myself, and what happened when I applied them to my own published results.

**[tool-selection-under-load](https://github.com/pvcomms/tool-selection-under-load)** — what happens to an agent's tool choice as the menu grows. 7 models, 665 trials, 34 tools, $5.07, zero API errors. The finding that survives correction is GPT-5 Mini beating GPT-5 at every tier (p=0.0018), and GPT-5 being the only model that degrades as tools are added — by declining to call one. The rank order does not survive, and the README says so above the leaderboard.

**[biometric-json-eval](https://github.com/pvcomms/biometric-json-eval)** — 29 hand-built cases asking whether a model can read biometric JSON well enough to settle a real-money contract. The KPI is dangerous errors, not accuracy. A prompt revision written to reduce over-caution raised accuracy _and_ drove dangerous errors from zero to five.

**[yt-tldr-eval](https://github.com/pvcomms/yt-tldr-eval)** — four models summarising forty videos. The previous README said ninety-seven videos and credited the grading to Opus. Both were false, and the repo contained the correct numbers the whole time, one file over.

## Protocols and agent infrastructure

**[mcp-fleet](https://github.com/pvcomms/mcp-fleet)** — four MCP servers I use daily, 47 tools. Written in a week for unrelated services, sharing no code, they converged on the same three patterns: single-flight credential refresh, dry-run-by-default on anything irreversible, and one composite audit tool per server that fans out in parallel and returns findings that each name the tool that fixes them.

**[bonp](https://github.com/pvcomms/bonp)** — a signed-envelope protocol for biometric claims. Auditing it against its own specification turned up universally forgeable signatures: the prescribed canonicalization used `JSON.stringify`'s replacer argument as if it were a key sort, which erased every nested object, so all envelopes hashed identically and one harvested signature validated any claim. v1.1 is RFC 8785 plus real Ed25519.

**[cmchp](https://github.com/pvcomms/cmchp)** — a wire format for handing agent state between models, and the retraction of the paper I wrote about it. The benchmark scored whether text rendered _from_ a packet contained that packet's own fields, which is the renderer's job, so it returned 100% for any input including nonsense. Every number I published came from that.

**[mcp-red-team](https://github.com/pvcomms/mcp-red-team)** — an adversarial scanner for MCP servers, ten attack categories. Against its own test target it now returns thirty findings where it used to return twenty-four; the six it was missing were its bugs, not the target's.

**[claude-code-playbook](https://github.com/pvcomms/claude-code-playbook)** — skills, hooks and evals for driving an agentic coding system. Every install command in it was broken, pointing at package names that do not exist.

## Things that solved a problem I had

**[doordrop](https://github.com/pvcomms/doordrop)** — a screen by the front door showing the delivery code, so the phone stays in the other room. ESP32 and an SSD1306 fed from the macOS Messages store. With an empty sender filter it would have shown bank OTPs to whoever was standing at the door.

**[subcortex](https://github.com/pvcomms/subcortex)** — retrieval over my own reading. Feeds in, chunked, TF-IDF, diversified, answered with citations.

**[maj-companion](https://github.com/pvcomms/maj-companion)** — a mah jongg companion built around a constraint: the official card is copyrighted, so the software must never contain it. Hand templates as a DSL, exact joker fill, a seeded scheduler for thirty-two players.

**[wasm-labs](https://github.com/pvcomms/wasm-labs)** — hand-written C compiled to WebAssembly. A 2→16→8→1 network with backprop in 69 lines, 16,124 bytes on the wire. The frame time I had been quoting was off by a factor of two.

**[bayesian-trainer](https://github.com/pvcomms/bayesian-trainer)** — drilling my own posterior updates against business cases. The Bayes engine is correct to floating-point noise. The input parser was not: one field used `parseFloat` where every other used the project's own helper, so typing `85/12` silently became `85`, and a tool for fixing miscalibration returned an answer 31.6 points wrong.

**[arxiv-digest](https://github.com/pvcomms/arxiv-digest)** — a paper URL in, a digest tuned to what I work on out.

## The through-line

The work I would actually defend is the negative results.

A leaderboard whose top four are statistically indistinguishable, where first and second returned identical answers on all forty-four items. A paper of mine, retracted, because its benchmark could not fail. A calibration trainer that miscalibrated. A protocol I specified, implemented, and then broke. A security scanner whose worst misses were its own. A fleet of 26 scheduled agents that ran 557 times unattended and whose success rate fell from 50% to 27% to 19% as the connectors underneath it rotted.

None of that is a portfolio in the usual sense. It is the part I trust, because it is the part that cost something to find out.

I build instruments and then turn them on the thing that built them. Evals for the models, statistics for the evals, an archive for the story I tell about the work. Each exists because the layer under it turned out to be less trustworthy than it looked, including when the layer was me.

## The correction

For a stretch I routed everything through the machine. Every hour planned, every note processed, every decision handed over — including a proxy that read my overnight recovery score and rewrote the sampling temperature and thinking budget of the model I worked with the next day. Biology in, inference parameters out.

In April 2026 I stopped, hard. Months later I could say what had happened, and what I wrote down was: _both were positions the pendulum picked, not me._

That is the honest version. Not a realisation that arrived on schedule — a behaviour that changed first and a sentence that caught up four months afterwards. I would rather describe it that way than claim I saw it coming, because I didn't.

The useful residue is a rule I can apply: automate the work, never the choice of which work is worth doing. Delegate cognition's logistics — scatter, triage, scaffolding. Don't delegate its judgment.

## How I work

- **Dissect the package.** What's said, how it's sold, and what actually arrives are three different things.
- **Keep the exit.** Any system you can't leave owns you.
- **Question the frameworks you question with.** Every instrument has assumptions baked in, especially the ones that feel like plain glass.
- **Credences, not vibes.** Numbers keep me honest about what I actually believe.

Standing contradictions I hold open on purpose: builds with AI and suspicious of AI; loves systems and distrusts platforms; craves order and trains for uncertainty.

---

_Writing at [paramv.com](https://paramv.com). Every number above is computed from data committed in the repository it links to._
