# VistaGrades Agent Instructions

## Project Purpose

VistaGrades is a student-focused website that sells AI-generated exam-style practice PDFs.

The website must stay simple, serious, professional, and easy to use.

## Product Rules

- VistaGrades sells digital PDF practice materials.
- Content is AI-generated and selected for better exam performance and made for study support only.
- VistaGrades does not claim the PDFs are official exams, past exams, or university-approved material.
- Do not guarantee grades, passing, academic results, or exam outcomes.
- Always make it clear that VistaGrades is not affiliated with or endorsed by any university.

## Pricing and Access Rules

- VistaGrades uses one-time payments only.
- A Single Course purchase costs $12.99 and gives access to one course.
- A Program Pack costs $49.99 and gives access to the program-specific courses shown for that program.
- Have a sign next to the Program Pack option that says it used to cost 64.99$ with a strikethrough.
- There is no monthly subscription unless the user explicitly adds one later.
- A user can access a paid PDF only after buying the related Single Course or Program Pack.
- Paid access must be checked server-side before downloads are allowed.

## Engineering Core Courses

- ENGR 213, ENGR 233, and ENGR 371 are Engineering Core courses.
- Engineering Core is not an engineering program.
- Engineering Core courses are not included in any Program Pack.
- Engineering Core courses must be bought separately as Single Course purchases.
- They may appear as recommended add-ons for programs, but access still requires a separate purchase.

## Stripe Rules

- Use Stripe Checkout for payments.
- Use server-side checkout session creation.
- Never expose Stripe secret keys in frontend code.
- Store Stripe secrets and price IDs in environment variables.
- Never collect or store full card details.
- Do not trust frontend prices.
- Verify payment status server-side before unlocking access.

## PDF Security Rules

- Do not store paid PDFs in the public folder.
- Do not commit paid PDFs to the public repository.
- Do not expose direct PDF links in frontend code.
- Use protected download routes.
- Check user access before returning any PDF.
- Use signed temporary links or secure server-side delivery.

## Course Rules

- Focus on engineering-related courses.
- Do not add unrelated courses.
- Keep course data centralized when possible.
- Reuse overlapping courses instead of duplicating them unnecessarily.

## Website Copy Rules

Use clear, direct student-focused language.

- Never add an "Included courses" list, per-course "in preparation" descriptions, or a publication/exclusion paragraph in pricing cards. Keep course-by-course details and availability on the Courses page.
- Do not add a "Choose your program" dropdown to pricing cards. Program Pack checkout uses the engineering field saved on the signed-in account; never silently default to another program.
- Keep Program Pack cards concise: price, short benefits, and purchase action. Do not reintroduce the removed descriptive block unless the user explicitly requests it.

Good style:
- Need one course? Buy it once.
- Need several program courses? Choose a Program Pack.
- AI-generated exam-style practice for focused revision.

Avoid:
- Guaranteed A+
- Official exam questions
- Past exam bank
- University approved
- Revolutionary AI platform
- Long generic marketing text

## Legal Pages

The website must include:
- Privacy Policy
- Terms and Conditions
- Refund Policy

These pages must explain:
- Products are digital.
- Content is AI-generated.
- VistaGrades does not guarantee academic results.
- VistaGrades is not affiliated with or endorsed by any university.
- Refunds are limited once access or download is provided.
- Single Course purchases and Program Packs are one-time payments.

## AI Content Disclaimer

Use this wording when needed:

VistaGrades creates carefully selected AI-generated exam-style practice materials designed to support focused revision. The content should be used as practice support and may not always reflect every instructor, course section, or exam format.

## Design Rules

- Keep the design simple and professional.
- Use the dark VistaGrades theme.
- Main background color: #0A0F1C.
- Use readable text, clean spacing, and strong contrast.
- Avoid childish visuals, fake testimonials, and clutter.
- Keep pricing and course pages easy to understand.

## Code Rules

- Keep code simple and readable.
- Avoid unnecessary features.
- Avoid over-engineering.
- Reuse components where practical.
- Keep pricing values centralized.
- Keep course data centralized.
- Validate user input server-side.
- Add loading and error states.
- Keep the mobile layout clean.

## Before Finishing Any Task

- Remove conflicting old pricing text.
- Remove unrelated courses or fake content.
- Check that paid PDFs are not exposed publicly.
- Check that Stripe logic is server-side.
- Check that users understand what they get before paying.

## Preservation Rule

Do not rebuild the website from scratch unless the user explicitly asks for a full rebuild. Always inspect the existing code first, preserve working features and designs, and make the smallest safe change needed for the requested task.

## VistaGrades PDF requirements

Apply these rules whenever creating or editing an exam-practice PDF. They do not apply to ordinary website changes.

### Required content
- Use the requested course and title: Core Exam Practice or Advanced Exam Practice.
- Every exam must contain:
  - 8 multiple-choice questions
  - 6 true-or-false questions
  - 10 long-answer questions
  - An answer key
- Total: 24 questions worth exactly 120 points.
- Show question marks clearly and verify that they add up to 120.
- Keep answers consistent with the questions after every revision.
- Follow the supplied course outline and requested topic coverage.
- Advanced practice should require deeper reasoning and harder applications than Core practice.

### Reusable lessons from PDF revisions

This file is a living instruction and feedback record for future agents, not model-weight training. After correcting a user-identified PDF flaw, capture the reusable lesson here when it applies beyond that one question. Refine an existing rule before adding a duplicate. Keep examples generic; never store private exam content, answer keys, or course-specific question numbers here. A one-off request becomes a general rule only when the user's intent supports that generalization. Explicit instructions for the current task take precedence.

#### Content selection and difficulty
- Before drafting, map the planned questions to the supplied course-content topics. Choose familiar classroom applications of those topics; a broad topic label does not justify adding specialized techniques or extra prerequisites.
- Core should test direct application of taught concepts. Advanced should require more reasoning through those same concepts, such as combining familiar rules, explaining a result, or testing a changed assumption. Do not create difficulty through obscure contexts, long wording, excessive calculation, or unrelated theory.
- Keep long-answer questions focused on one main learning objective. Prefer one or two purposeful parts, with a maximum of three. Remove redundant follow-ups and unrelated tasks; a single complete proof or calculation does not need artificial subparts.
- When simplifying, preserve a meaningful skill to assess. Replace a complicated application with a direct exercise in its underlying concept, rather than merely shortening the wording or lowering the numbers.
- Use code or pseudocode only when the requested coverage calls for programming or algorithm analysis. For a mathematical concept that can be assessed directly, prefer a calculation, sequence, relation, diagram, or proof. A code-free request excludes code from both questions and answers.
- Avoid specialized story settings that require more explanation than the concept being tested. For example, an elaborate applied system can be replaced by a direct use of its underlying mathematical rule when the requested coverage permits. This is not a blanket ban on any course topic.

#### Question design and representations
- Mix direct calculations, interpretation, and reasoning as appropriate to the course. Use short, familiar situations for accessible conceptual MCQs; keep the premises explicit and ask what necessarily follows, rather than relying on everyday assumptions.
- Where reasoning rules are taught, a harder question may combine several familiar rules in a short argument. Require justified steps, and optionally a counterexample after changing a premise. Apply the same idea to other courses through their own taught methods; do not insert logic exercises into unrelated subjects.
- Use the representation students are expected to work with. For example, a topic taught with matrices, tables, graphs, or diagrams should include a suitable concrete representation when relevant to the requested coverage. State ordering, labels, units, domains, and conventions needed to interpret it.
- Every MCQ must have exactly one defensible answer. Distractors should reflect plausible mistakes, not ambiguous wording. In quantified situations, distinguish statements about every member from statements about some members; do not assume existence from a universal statement alone.

#### Revision and presentation discipline
- Replace only the questions requested unless a broader revision is authorized. Preserve unrelated content and the approved design. Update the corresponding answer, explanation, marks, and any affected references together.
- Preserve the required question counts and total points when removing subparts. Allocate marks to meaningful work and ensure each solution's marking guidance matches the revised task.
- Size blank answer areas for the expected work, especially proofs, matrices, and drawings. Match the approved visual style without forcing an identical page count; avoid both cramped solutions and unnecessary page breaks.
- Keep premises and supplied data together with the question. Keep each answer-key entry intact where practical, with clear mathematical steps and the required black text and question-number-only heading.

#### Correctness after changes
- Solve each new or changed question from its stated data before finalizing the key. Check assumptions, domains, boundary cases, and whether the requested result actually follows. Accept equivalent valid methods where appropriate.
- For an argument, verify that its premises can hold together, that the conclusion follows, and that any proposed counterexample satisfies all retained premises while falsifying the conclusion. For an MCQ, check every option, not just the intended answer.
- Use independent calculations, enumeration, or other suitable checks when helpful. Recheck affected calculations and representations after any edit; a correct earlier version does not validate a revised question.
- Recompile and visually inspect affected question and answer pages, checking neighboring content for reflow. Verify the final page count, all question counts and marks, headers, footers, and answer-key consistency before recording the update.

### Format and typography
- Write every PDF in LaTeX.
- Match the latest user-approved PDF’s layout, typography, spacing, colours, headers, footers, and answer-space style.
- Refer to any similar documents in the folders for reference in style and formatting the each document appropriately, if necessary.
- Typeset every mathematical expression, variable, fraction, exponent, bound, interval, and recurrence in LaTeX math mode.
- Use actual superscripts and properly formatted fractions, Greek letters, logarithms, and floor/ceiling notation.
- Never display raw notation such as `n^2`, `Theta(n)`, or `floor((lo+hi)/2)` in ordinary prose.
- Make multiple-choice labels **A**, **B**, **C**, and **D** bold, with generous separation between choices.
- Provide clearly indented pseudocode when a question asks students to analyse a loop or algorithm.
- Leave sufficient working space, especially for drawing trees, diagrams, and multi-step solutions.
- For long-answer questions, do not write the words “Working Space”; leave the space blank.
- Keep headings with their content and prevent awkward wrapping, clipping, and overlapping text.
- Always start every page with a question (except for the first page which must introduce the course name and question types and numbers and points, as well as its terms and conditions briefly) and leave no page mostly blank only because of a couple of lines, stay efficient.
- There must be a reasonable and consistent line spacing throught each generated PDF (between titles and text, etc.). The header must appear on the first page of every PDF. It should be clean, professional, and consistent across all generated PDFs. Use the correct course code, course title, and practice type for each PDF.

### Wording
- Use “long-answer questions,” not “structured questions.”
- Use “Answer key included,” not “Worked solutions included.”
- Keep the cover and instructions concise.
- Avoid unnecessary page-by-page directions, detailed outline-location references, and repetitive explanations.
- Retain the approved educational disclaimer and copyright footer.
- Student email used for sign up on website must be included next to copyright.
- All footer content must be centered except for the page number.
- Every page in the answer key must have an indication in the header somewhere that these pages are part of the answer key.
- All answer key text must be in black, without the title of the questions, only saying the question number is enough.
- Do not claim that these are official exams or professor-provided questions.

### Verification
- Compile the LaTeX and inspect the rendered PDF before delivery.
- Check question counts, the 120-point total, answer correctness, mathematical notation, choice spacing, and page layout.
- Do not claim successful compilation or visual verification unless actually completed.

### Private delivery
- Never commit or push exam PDFs, rendered page images, private exam LaTeX sources, or scripts containing exam content to GitHub.
- Keep temporary generation files outside the repository and remove task-created temporary files after delivery is confirmed.
- Do not delete unrelated files or the only usable copy before confirming delivery.

### Update log
- Create or update `logs/pdf-updates.md` whenever a PDF changes.
- Record the course, PDF title, version, actual update date, verified page count, question count, total points, and private status.
- Summarize changes in short, natural bullet points.
- Do not include exam questions, answers, private download paths, or invented public-sample links in the log.
- Website-only changes do not require a PDF log entry.
- All generated PDFs must be saved in the pdf folder in Courses folder, given seperate access to (not in repo).

### Course Resources
- You have access to the “Courses” folder, provided separately from the GitHub repo. It contains course titles and course outline images for each engineering program. Each program has its own folder, and the image files inside each folder are named according to their corresponding course titles.
- You also have access to `eng_list.md`, which has info on courses offered for each program. In that file, the common courses shared between engineering programs are written in **bold**.
- Use only the course content sections from the outline images to create mock exam PDFs, by extracting all the text to read contents. These sections may be titled “Course Content,” “Schedule,” or something similar.
- Do not use irrelevant outline information such as grading breakdowns, dates, policies, instructor details, office hours, or administrative notes.
- The generated mock exam PDFs must follow exactly what is taught in the course content. Do not add topics that are not listed. If a course content section is too broad or unclear, more details will be provided in the prompt.
- Common course outlines are located in the “Engineering Core” folder for courses listed in the “Engineering Core” section of the website.
- Every generated PDF must stay consistent in design, structure, formatting, problem style, syntax, and solvability.
- Apply the reusable revision lessons above to the current course's taught concepts; examples illustrate design principles, not mandatory topics or question templates for every course.

### Code Approval
- Do not commit to GitHub unless prompted.


Specific instructions from the user override these defaults.

<!-- BEGIN:nextjs-agent-rules -->

# This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` (resolved from this file's directory; in monorepos the `next` package may not be visible from the repo root) before writing any code. Heed deprecation notices.

This block is written and re-added by `next dev` — verify at `node_modules/next/dist/server/lib/generate-agent-files.js`. Removing it from a diff only re-creates the uncommitted change; committing it with your work keeps the tree clean.

<!-- END:nextjs-agent-rules -->
