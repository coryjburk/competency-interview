# Full-Time MBA Program · David Eccles School of Business Interview Scorecard

Live interviewer scorecard for the **Full-Time MBA Program · David Eccles School of Business Structured Interview Toolkit**. Single static HTML file — no server, no build step, no dependencies.

## What it does

- **Role dropdown** — 10 common MBA roles, each mapped to 5–7 competencies drawn from the Full-Time MBA Program · David Eccles School of Business Competency Model and the role competency menu.
- **Stage selector** — the canonical four-stage lifecycle (Initial Screen → Hiring Manager/Leader → Team/Panel → Final/Readiness). Each stage shows only its assigned competencies; gatekeepers appear in two stages.
- **Rubric-integrated scoring** — the 4-point behaviorally anchored scale from the Employer Edition guide, with the anchor text shown at the point of scoring. MBA Model competencies also display the 1–10 developmental mapping.
- **Live gate rules** — a score of 1 on a gatekeeper immediately overrides the band to *Do Not Advance*; two or more risk flags trigger a hiring-manager-review warning.
- **Exports** — Print/Save PDF, copy as text, download CSV. Autosaves to the interviewer's browser only.

## Repository layout and the question-bank gate

| File | Public? | Notes |
|---|---|---|
| `index.html` | **Yes** — deploy to GitHub Pages | Interviewer scorecard. Framework, competency maps, and rubric only — **no interview questions**. |
| `student_playbook.html` | **Yes** — deploy to GitHub Pages | Student prep playbook: stages, rubric, role explorer, AI practice coach. No questions. |
| `eccles_question_pack.json` | **No — never commit or deploy** | Confidential employer file: 40 question sets (2 behavioral + 1 situational + probes + red flags + strong signals each) and 2 role-motivation screen questions per role. Distributed directly to employer partners by Full-Time MBA Program · David Eccles School of Business Career Services. |
| `Eccles_MBA_Interview_Prep_Guide_Student_Edition.docx` | Yes | Student prep guide (method, story bank, worked examples). Linked from the playbook. |
| `Eccles_MBA_Interview_Prep_Student_Overview.pptx` | Yes | Student overview deck with speaker notes. Linked from the playbook. |
| `mock_interview.html` | Yes | Student mock-interview lifecycle: 4 stages, speech-to-text answers, per-stage AI coaching prompts, score logging with gates/thresholds, final debrief export. |
| `retired_bank.js` | Yes | **Single source of truth** for retired questions, competency definitions, and role maps — loaded by both `student_playbook.html` and `mock_interview.html`. Edit this one file when a pack rotates. |
| `README.md` | Yes | This file. |

**Why the split:** the student-facing edition of the framework deliberately shares competencies and rubrics but not verbatim questions. Publishing the pack on a public page would defeat that. Interviewers load the pack locally via the **Load question pack** button — the file never leaves their machine.

Add this line to `.gitignore` before the first commit:

```
eccles_question_pack.json
```

## Deploying

1. Create the repo; commit `index.html`, `student_playbook.html`, `README.md`, and the one-line `.gitignore` only. The `.gitignore` file's entire contents must be the single line `eccles_question_pack.json` — it names the file git must exclude; never paste the pack's contents into it.
2. Settings → Pages → deploy from the main branch.
3. Send `eccles_question_pack.json` to employer partners directly (email or secure share). Each interviewer clicks **Load question pack** at the start of a session. The tool is fully usable without the pack (rubric, scoring, gates, exports) — only question text is withheld.

## Distributing the question pack (chain of custody)

The pack travels person-to-person, never through this repo. GitHub's web upload ignores `.gitignore`, so the protection is the protocol, not the file:

1. **Master copy** lives in Full-Time MBA Program · David Eccles School of Business Career Services cloud storage (Box / Google Drive / OneDrive), access-scoped to career services staff. Upload the `.json` file as-is; never convert it to a Docs/Word format — converted copies will not load in the scorecard.
2. **Full-Time Eccles MBA → employer:** when an employer partner adopts the toolkit, Career Services sends the current pack to the employer's recruiting or HR lead — email attachment or a share link scoped to them.
3. **Employer lead → interviewers:** the recruiting/HR lead forwards the file to their interviewers directly (email or their own access-controlled drive — never a public intranet page or wiki), with this instruction: *"Save this file anywhere on your computer. In the scorecard, click **Load question pack** and select it — it loads locally in your browser and is never uploaded anywhere."*
4. **On rotation:** Career Services sends the new version to employer leads and asks them to delete prior copies; the retired version's questions are published in the student playbook (see lifecycle above).

If the pack is ever posted anywhere public, treat it as a rotation trigger — retire, publish, reissue — not an emergency.

## Question-pack lifecycle

The pack rotates. Each version lives one of two lives, in order:

1. **Live** — the current pack (e.g., v2). Direct-send to employer partners only. Never committed, never deployed, never quoted in public files.
2. **Retired** — when a new version replaces it, the *previous* version's questions are published as the practice bank by adding them to `retired_bank.js` (which feeds both the playbook and the mock interview tool).

Rules that keep this honest: only fully rotated-out versions are published — never a partial or current pack; rotation happens on its own schedule (or after any exposure), never to feed the practice bank; and if a live pack is ever exposed, the response is the same as a planned rotation — retire it, publish it, issue the next version. The system is designed to metabolize leaks, not to pretend they can't happen.

## Privacy

Scores and candidate names autosave to `localStorage` in the interviewer's browser and are never transmitted. On shared machines: export, then use **Clear this interview**.

## Rotating or extending questions

Edit `eccles_question_pack.json` — the structure is `competencies.{Name}.{b1,b2,s,probes,rf,ss}` and `screens.{roleId}[2]`. New competency sets can be generated with the Appendix D template in the Employer Edition guide; calibrate with the interview team before live use. Bump `version` when you rotate.

---
Adaptable framework, not a certification. Hiring decisions — and legal/HR compliance for them — remain with the employer. © University of Utah, Full-Time MBA Program · David Eccles School of Business.
