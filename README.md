# ai-agent-exposure-appraisal

**Risk vs. confidence for AI agents, by the executive who owns the answer.**

Most AI security claims show a defense blocking an attack. Few show what the defense cost in work that
no longer got done, whether the prediction came before the result, or whether anyone but the author
attacked it. This appraisal puts those three things next to each question a CISO, CTO, CFO or board
member would ask. It pairs **attacks stopped** with **legitimate work kept**, and it states the caveat
beside every number.

What is your exposure?

## Scope, stated once

- Evidence, not an audit, and not a compliance claim.
- Every "measured" figure comes from simulated targets, local open-weight models of 8B parameters or
  smaller, and attacks written by the author or by two Google models.
- The measurements are from [Agent Defense Theater](https://github.com/ScottColeSW/Agent-Defense-Theater)
  and [Aegis Vector](https://github.com/ScottColeSW/Project-Aegis-Vector). Outside figures are in
  [SOURCES.md](SOURCES.md), with how far each was checked.
- Status: early draft. Corrections to earlier notes are in [docs/CORRECTIONS.md](docs/CORRECTIONS.md).

Ask each question of your own environment first. The answers below are what was seen in ours.

## CISO

| Question | What we measured | What held | What it cost | Caveat |
|---|---|---|---|---|
| Which agents still carry one key that opens every door? | A shared admin token let 62 of 120 planted instructions run. | A credential scoped to the task and ticket: 12 of 120. | Not isolated in this figure. | One simulated desk, one agent step. |
| If an attacker knows your controls, which one still holds? | Models told nothing about the defenses wrote 45 attacks. Scoped credentials let 76 of 675 through, all from the 6 attacks that fit one gap. | Request binding: 0 of 675. Against an informed hosted attacker: 0 of 54 on each task, where scoped credentials let 30 and 36 of 54 through. | No loss of valid work in either run. | Two Google models wrote the attacks. The informed attacker finished 1 round of 4. |

## CEO and COO

| Question | What we measured | What held | What it cost | Caveat |
|---|---|---|---|---|
| What does your agent read that someone else wrote, and what may it do about it? | With no control, planted text became actions in 62 of 120 cases. | Request binding with approval holds: 0 of 120. | 61 of 63 valid tasks completed. | The valid tasks are the author's and tidier than real work. |
| Where is a person in the loop, and what do they see? | A reviewer shown the agent's own reason let 40% of non-matching requests through. | The system's comparison with the operator's words shown first: 6%. | Not measured. | Small-model reviewers. A study with people is built and waiting for participants. |

## CTO

| Question | What we measured | What held | What it cost | Caveat |
|---|---|---|---|---|
| Where does an approval path reopen something a hard limit refused? | A $50 refund budget stopped a duplicate of a requested $30 refund (0 of 54). With a hold path, the reviewer approved 32 of 32 holds. | The final budget denial, or request binding alone. | Not measured. | Six author-written texts, one mechanism, one reviewer model. Reproduced exactly on a rerun. |
| Which defenses did you adopt because they sound right? | Telling the model the text was untrusted raised hijacks from 22 of 45 to 33 of 45. | A locked plan stopped every hijack needing a new tool (0 of 36). A goal check by a separate reviewer stopped all 45. | Not measured. | Five attacks, three models. |

## Head of AppSec

| Question | What we measured | What held | What it cost | Caveat |
|---|---|---|---|---|
| Who has tried to break your control without having written it? | Blind attack writers found the leaking gap in 2 of 39 on their own. Shown the rules, a hosted model aimed 4 of its first 6 at it. Across four draws of a local 8B attacker, scoped-credential success ranged from 0% to 18.7%. | Request binding: 0 of 720 across the four draws. | None observed. | One vendor for hosted writers, one small local model. None of this replaces an outside red team. |
| Who checks the checker? | On the same card, reviewer models differed by 27 points. One alone approved 12 refunds nobody asked for. In a three-agent crew a reviewer agreed with 78% of bad reports and 67% of honest ones. | An independent recomputation stopped all 45 bad figures. | Nothing measurable. | A handful of small models. |

## CFO

| Question | What we measured | What held | What it cost | Caveat |
|---|---|---|---|---|
| What does a control cost in work that no longer gets done? | The one control that stopped every tampered tool also refused all 18 legitimate updates. | Request binding with approval holds. | 61 of 63 valid tasks kept. | Two simulated settings. |
| What does it cost to test this? | All attack generation so far, hosted models included, cost $0.27 (the author's figure from the provider's billing page). | Hard caps on calls and tokens. | $0.27 in total. | Small models and samples. Larger models cost more and may behave differently. |

## Compliance and Audit

| Question | What we measured | What held | What it cost | Caveat |
|---|---|---|---|---|
| Can you show a prediction came before the result, and the log was not edited? | Each preregistered live run refuses to start unless its prediction is committed and unedited. The no-defense rate in the blind round came in at 75% against a predicted 52%, and the miss is reported. | A hash-chained decision log that can be verified after the fact. | Not measured. | A hash chain detects tampering. It does not prevent it. Method, not a guarantee. |
| What could not be tested? | Independent red teams, larger models, real tool catalogs, production telemetry, people reviewing approvals. | | | The list is the author's own. |

## Board

| Question | What we measured | What held | What it cost | Caveat |
|---|---|---|---|---|
| If attackers are not refused and know our controls, what is our worst case? | The approval path approved a duplicate refund 32 of 32 times. The control that looked strongest, request binding with holds, had a hole that a simpler final budget denial did not. | A final hard limit in code. | Not measured. | One simulated setting. It shows a kind of failure to look for, not how often it happens elsewhere. |

## Outside evidence, read carefully

Meta's LlamaFirewall cut attacks on one benchmark from 17.6% to 1.75% and **lowered task utility from
47.7% to 42.7%**. Microsoft's spotlighting work cut attacks from about 50% to under 3% on GPT-family
models, which are not the small open-weight models tested here. Details and links are in
[SOURCES.md](SOURCES.md).

## Books for the people who sign off

This appraisal covers measured agent risk. The books cover the leadership, governance and decision
side, written for executives who need to make good AI calls without becoming technical:

- [**The Six-Question AI Evaluation Framework**: Turn Vendor Meetings Into Clear Go/No-Go Decisions in 60 Minutes](https://www.amazon.com/dp/B0GPRJRYZW?&linkCode=ll2&tag=ifio42-20&linkId=b67e3c17a4eb0539b2ec9ec37ef410e4&language=en_US&ref_=as_li_ss_tl)
- [**Navigating AI Landscapes**: Responsible Executive Blueprints](https://www.amazon.com/dp/B0G1QLZ5BL?&linkCode=ll2&tag=ifio42-20&linkId=b67e3c17a4eb0539b2ec9ec37ef410e4&language=en_US&ref_=as_li_ss_tl) ([Paperback](https://www.amazon.com/dp/B0G1SL9SRD?&linkCode=ll2&tag=ifio42-20&linkId=b67e3c17a4eb0539b2ec9ec37ef410e4&language=en_US&ref_=as_li_ss_tl))
- [**The GenAI Prompt Playbook**: Risk & Compliance](https://www.amazon.com/dp/B0F28B7NYM?&linkCode=ll2&tag=ifio42-20&linkId=b67e3c17a4eb0539b2ec9ec37ef410e4&language=en_US&ref_=as_li_ss_tl) ([Paperback](https://www.amazon.com/dp/B0F5QCH3M6?&linkCode=ll2&tag=ifio42-20&linkId=b67e3c17a4eb0539b2ec9ec37ef410e4&language=en_US&ref_=as_li_ss_tl) · [Audiobook](https://www.amazon.com/dp/B0F8D8SNKM?&linkCode=ll2&tag=ifio42-20&linkId=b67e3c17a4eb0539b2ec9ec37ef410e4&language=en_US&ref_=as_li_ss_tl))
- [**AI to ROI** (2nd Edition): Agentic Frameworks, Patterns, and Engrams](https://www.amazon.com/dp/B0G99W1QTW?&linkCode=ll2&tag=ifio42-20&linkId=b67e3c17a4eb0539b2ec9ec37ef410e4&language=en_US&ref_=as_li_ss_tl) ([Paperback](https://www.amazon.com/dp/B0GC6NS3MK?&linkCode=ll2&tag=ifio42-20&linkId=b67e3c17a4eb0539b2ec9ec37ef410e4&language=en_US&ref_=as_li_ss_tl))

Author of 30+ books. The full list is on the [profile page](https://github.com/ScottColeSW).

<sub>As an Amazon Associate I earn from qualifying purchases.</sub>

## Work with me

Want an appraisal of your own agents? Start with the question at the top: **what is your exposure?**
Reach me on [LinkedIn](https://linkedin.com/in/scottcole).

## Author

Scott Cole, AI security and governance. [Profile](https://github.com/ScottColeSW)

## License

MIT
