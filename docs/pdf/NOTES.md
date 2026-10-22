# PQC migration guide: working notes

Carried over from the planning session on 2026-10-22. These are decisions and facts for the PDF guide,
not the guide itself.

## The plan

- A "post-quantum cryptography (PQC) migration" guide: a free PDF checklist first, a Kindle edition later.
- **Title says PQC, not "QSP".** QSP is not a standard term, so people will not find it by searching.
- Audience: leaders who need to get their organization moving now. Keep it practical and short.

## Decisions

1. **Recommend passkeys first.** Fallback where a passkey is not offered: a long passphrase in a password
   manager. Stored passwords use a memory-hard hash such as Argon2id (Scott's recommendation, stated as
   such, not cited as a requirement).
2. **Leave biometrics out of the copy.**
3. **Do not quote the NIST IR 8547 deprecation and disallow dates (2030 and 2035), anywhere.** They change,
   the sources found were secondary, and the document was still a draft. Link to NIST's current
   transition page instead. Describe the migration as urgent without a deadline date.
4. **Keep a short "what's next" section** on future ideas (post-quantum signatures in passkeys, other
   future authentication). Do not go deep: "it's a deep well."
5. **Style:** no em dashes. Verb-first, plain language. Avoid self-congratulatory "I" statements.

## Facts that were checked (2026-10-22)

| Fact | How far it was checked |
|---|---|
| NIST finalized ML-KEM (FIPS 203), ML-DSA (FIPS 204), SLH-DSA (FIPS 205) in August 2024. FIPS 203 gives 13 August 2024 as its publication and effective date. | FIPS 203 read in the primary document. The dates for 204 and 205 come from NIST slides. Open the 204 and 205 documents before quoting an exact day for them. |
| Chrome, Edge and current Firefox use the hybrid key exchange X25519MLKEM768 by default. | Secondary sources. |
| Server support lags the browsers. Sources gave 3.7% to about 15% of origin servers depending on source and date. | Secondary, and they disagree. Check Cloudflare Radar for a current figure before citing one. |
| A Cloudflare April 2026 post reports more than two-thirds of human-generated TLS traffic to its network uses the hybrid exchange. | Secondary (a guide citing the post). |
| Against a quantum attacker, AES-256 keeps about 128-bit security and AES-128 falls to about 64 bits (Grover's algorithm). | Secondary. No NIST primary publication was found stating the recommendation in these words. |
| The main exposure is the public-key layer (RSA and elliptic-curve: key exchange, signatures, certificates), not the password. | Standard framing, consistent with all the sources above. |

## Claims not verified (state as recommendations, or check first)

- Passkeys typically use classical signature algorithms today, so they fix phishing and credential theft
  now and still join the post-quantum migration later. Written from general knowledge. Check the current
  WebAuthn/FIDO algorithm support before publishing.
- Argon2id as the password hash (standard guidance, RFC 9106 and OWASP, not re-checked).
- "Harvest now, decrypt later" is a recognized threat. No public evidence was found that it is happening
  at scale, so do not write that it is "already happening."
- The sync account and account recovery are the weak points of passkeys. Judgment, widely made, not cited.

## Where the guide's content should come from

- Inventory first: find where RSA and elliptic-curve cryptography live, rank by how long the data must
  stay secret, and move long-lived items first.
- Agent angle (Scott's edge): every service identity, token and signing key an AI agent holds is a
  credential to migrate. Link to the appraisal in this repo for the measured agent-risk side.
- Cite only final standards and primary sources. Record each source and how far it was checked in
  `SOURCES.md`, as this repo already does.
