# Sources

Every outside number used in this repository, with where it came from and how far it was checked.
Last verified 2026-10-22.

**Status key.** *Primary* means the figure was read in the original paper or agency document.
*Secondary* means it was read in a summary and still needs a check against the primary text.

## Research papers

### LlamaFirewall (Meta) | Primary

Chennabasappa et al., *LlamaFirewall: An open source guardrail system for building secure AI agents*,
arXiv:2505.03574, submitted 6 May 2025. <https://arxiv.org/abs/2505.03574>

AgentDojo evaluation (Section 4.3): ten agent models, static replays, one attack type
(`important_instructions`, an instruction planted in tool output).

| Configuration | Attack success rate | Task utility |
|---|---|---|
| No guardrail (baseline) | 17.6% | 47.7% |
| PromptGuard 2 86M alone | 7.5% | 47.0% |
| AlignmentCheck (Llama 4 Maverick) alone | 2.89% | 43.1% |
| Combined | 1.75% | 42.7% |

Read it this way: the combined setup cut attacks by more than 90% and **lowered utility by 5 points**
(47.7% to 42.7%). Summaries that say it "preserved 42.7% utility" leave out the baseline. The paper
itself notes the benchmark covers a narrow class of attacks. The introduction rounds the AlignmentCheck
reduction to 83% and Section 4.3 to 84%.

### Spotlighting (Microsoft) | Primary

Hines, Lopez, Hall, Zarfati, Zunger, Kiciman, *Defending Against Indirect Prompt Injection Attacks With
Spotlighting*, arXiv:2403.14720, submitted 20 March 2024. <https://arxiv.org/abs/2403.14720>

- Abstract: attack success falls "from greater than 50% to below 2%" with minimal impact on task
  efficacy. The figure under 2% belongs to the best technique (encoding), not to datamarking.
- Models tested: **GPT-family only** (GPT-3.5-Turbo, GPT-4, GPT-3 Text-003). No small open-weight models.
- Delimiting: defensive instructions alone had negligible effect on GPT-3.5-Turbo. Adding special
  delimiters cut attack success by about half.
- Datamarking, summarization task: GPT-3.5-Turbo about 50% down to 3.10%; Text-003 40% down to 0.00%.
- Datamarking, document Q&A task: GPT-3.5-Turbo 8.0%, GPT-4 1.0%, Text-003 0.00%.
- Encoding: ASR 0.0% or close to it across summarization and Q&A.
- The authors report negligible harm to underlying NLP task performance from datamarking and encoding.
  Not independently checked here.

## Government guidance

### Careful Adoption of Agentic AI Services | Primary (agency pages), full text not yet read in this repo

Joint guidance from agencies in six countries: CISA, NSA, Australian Signals Directorate's ACSC,
Canadian Centre for Cyber Security, New Zealand NCSC, UK NCSC. NSA released it 30 April 2026 and CISA
1 May 2026. The five risk categories named by NSA are privilege, design and configuration, behavior,
structural, and accountability.

- CISA: <https://www.cisa.gov/news-events/news/cisa-us-and-international-partners-release-guide-secure-adoption-agentic-ai>
- NSA: <https://www.nsa.gov/Press-Room/Press-Releases-Statements/Press-Release-View/Article/4475134/nsa-joins-the-asds-acsc-and-others-to-release-guidance-on-agentic-artificial-in/>
- Full text (ASD): <https://www.cyber.gov.au/sites/default/files/2026-05/careful_adoption_of_agentic_ai_services.pdf>

CISA's resource page labels the document "agentic SI services", which looks like a typo. Cite the ASD PDF.

## Regulation

### EU AI Act amendments (Digital Omnibus on AI) | Secondary, confirm on EUR-Lex

Reported as Regulation (EU) 2026/1744, published in the Official Journal on 24 July 2026 and in force
27 July 2026. Stand-alone high-risk systems (Annex III) move from 2 August 2026 to **2 December 2027**.
Systems embedded in regulated products (Annex I) move to **2 August 2028**.

- Garrigues summary: <https://www.garrigues.com/en_GB/garrigues-digital/ai-digital-omnibus-regulation-has-been-published-redefining-deadlines-and>

Sources disagreed on whether the final text uses fixed dates or a standards-based trigger with a
long-stop date. Read the regulation text before citing a date as binding.

## Context and taxonomy

### Iternal Technologies checklist page | Secondary, a map to primary sources only

Iternal Technologies, *AI Agent Security: Risks, Controls & the CISO Agentic AI Security Checklist*
(2026), accessed 2026-10-22. <https://iternal.ai/ai-agent-security-checklist>

A vendor page that also sells related products. It is cited here only for how it organizes the OWASP,
NIST, CISA and EU AI Act material. No figure in this repository rests on it. Two of its figures were
traced to the papers above, and one was found misleading (the LlamaFirewall utility figure).

Other numbers on that page were **not** checked and are not used here: Gartner adoption forecasts,
vendor survey percentages, and the incident statistics.

## Measurements from this author

All "what we measured" figures in the README come from the sibling project
[Agent Defense Theater](https://github.com/ScottColeSW/Agent-Defense-Theater), mainly its
`docs/ROLE-QUESTIONS.md` and `docs/CHECKLIST.md`, and from
[Aegis Vector](https://github.com/ScottColeSW/Project-Aegis-Vector). They use simulated targets, local
models of 8B parameters or smaller, and attacks written by the author or by two Google models.
