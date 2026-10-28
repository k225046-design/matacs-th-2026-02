 Write-up


 1. AI vs rules

AI is used for two things only: reading messy proposal text into structured facts, and applying a
fixed rubric to two fuzzy criteria (experience, team).

Everything else is plain code: file checks, loading criteria, mandatory pass/fail,
price/timeline/warranty formulas, weighted total, sorting.

Why: AI is good at language but can vary or invent things. Code is exact and repeatable.
Anything that is arithmetic or a yes/no rule stays in code.


 2. Consistency and explainability

- Temperature 0, JSON schema, fixed rubric, and the prompt and criteria versions are stored with each run.
- Extraction is separate from scoring, and every extracted fact carries a short evidence quote.
- Same input + same versions gives the same result in the code steps. AI steps are near-identical,
  and the extracted JSON is cached so a re-rank reuses it instead of re-reading the PDF.
- The reviewer sees a per-criterion score table, the evidence quote, and the reason for each rank.


 3. Human in the loop

- A person reviews every flagged and ineligible proposal, and can override any score or status
  with a required written note.
- The final award decision is always made by a human. The tool only recommends.
- Audit log: who uploaded, file hash, criteria version, prompt version, model name, extracted JSON,
  scores, flags, overrides with reason and user, timestamps.


 4. Changing criteria

Criteria are versioned. Editing creates a new version, and old results stay tied to the old version.

Extracted facts are reused, so only the cheap scoring step is re-run. The tool shows
"scored under v1, current is v2" and the reviewer chooses whether to re-score.
Past awards are never silently changed.


 5. Risks

- Wrong extraction: evidence quotes, null for missing, schema validation, human check on flags.
- Made-up facts: "only explicit facts" instruction, evidence required, missing = flagged.
- Manipulation (prompt injection): proposal text is treated as data, an injection check runs, and the
  proposal is flagged for review. Sample C contains this. It is not rewarded and is sent to a human.
- Bias: fixed rubric, no company name or size used in scoring, overrides logged.
- Mandatory-criteria errors: strict rule. For example B is ineligible because the licence is not held by the bidder.
- Missing info: D has no timeline, so it is flagged rather than guessed.
- Cost: cheap model, cached extraction, code for calculations, limit on file size and pages.
- Privacy: only the proposal text is sent, and no personal data is stored beyond what is needed.


 Sample result

A first (about 98), E second (about 92). C flagged (manipulation), D flagged (no timeline), B ineligible.

Assumption: the experience window is the last 5 years, so installs before that would not count.
