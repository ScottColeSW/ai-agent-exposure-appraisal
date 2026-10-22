# Corrections

Six places where early working notes drifted from the measurements, and what the data supports
instead. Kept on purpose, so the same mistakes do not come back.

| # | Early note said | What the data supports |
|---|---|---|
| 1 | Scoped credentials mean "dynamic, short-lived OAuth tokens restricted to the ticket." | The test used a credential scoped to the task and ticket in a simulation, and it cut planted-instruction success from 62 of 120 to 12 of 120. OAuth is one way to build that. It was not tested. |
| 2 | "Informed" attackers bypassed scoped keys 76 times. | The 76 of 675 came from attacks written by models **told nothing** about the defenses. Informed attackers got 30 of 54 and 36 of 54 past scoped credentials. Request binding let 0 through in every case. |
| 3 | Request binding is "cryptographic" and ties tool calls to a signed session. | It refuses outright a refund or export the operator never asked for, by comparing the request to the operator's own words. No signing is involved. |
| 4 | Fix indirect injection with "strict context delimitation and input isolation." | Telling the model the text was untrusted raised hijacks from 22 of 45 to 33 of 45. What held: a plan locked before untrusted text is read (0 of 36 for hijacks needing a new tool), a goal check by a separate reviewer (all 45 stopped), and request binding (0 of 120). The 62 of 120 figure belongs to the shared-token support desk, not to this row. |
| 5 | Over-blocking is fixed by showing reviewers the user prompt next to the proposed action (40% to 6%). | That result fixes a different problem, reviewers approving things they should not. The over-blocking finding is that the one control stopping every tampered tool also refused all 18 legitimate updates. The finding paired with it is that request binding with holds kept 61 of 63 valid tasks. |
| 6 | Preregistration is the same as hash-chaining the decision log, and the 75% vs 52% miss shows log tampering. | Two separate controls. Preregistration commits the prediction before the run. The hash-chained log makes the decision record tamper-evident. The 75% vs 52% is a missed prediction, reported openly. A hash chain detects tampering but does not prevent it, so "immutable" overclaims, and nothing here is a compliance claim. |

One row held up as written: a $50 refund budget stopped a duplicate of a requested $30 refund (0 of 54),
while an approval hold path approved it 32 of 32 times because it matched the operator's words. The
matching fix is a final budget denial, or request binding alone.

## Also corrected from a vendor source

A vendor checklist said LlamaFirewall reduced attacks "while preserving 42.7% utility." The paper's
baseline utility was 47.7%, so the combined setup cost 5 points. See [SOURCES.md](../SOURCES.md).
