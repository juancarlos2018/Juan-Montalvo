# Prompt Log

A running record of meaningful AI sessions: what I asked, what the AI produced, and how I verified or edited it.

## 2026-08-29 — Bio and Resume Drafting

**What I asked:** Convert my existing resume (PDF) into a Markdown RESUME.md, and condense a bio I wrote into the 150-200 word range for BIO.md, both for my portfolio repo.

**What the AI did:** Reformatted my resume into clean Markdown, keeping all original content and quantified achievements. Condensed my ~550-word bio draft down to ~189 words, preserving the key facts and throughline (Marine Corps → NJROTC instructor → EMBA).

**What I kept / changed:** Kept the overall structure and quantified bullets as drafted. kept the structure as drafted, just double-checked the dates and job titles were right.

## 2026-08-29 — Repo Skeleton Fix (post Stage 0 feedback)

**What I asked:** Help fixing my Stage 0 submission after professor feedback — move bio content into README.md with an engagement index, add .gitignore, build out the 7 required folders, and revise AGENTS.md/CLAUDE.md/prompt-log.md to match the actual course standard.

**What the AI did:** Drafted the updated README.md (bio + engagement index), the .gitignore using the course's exact starter block, one-line README.md stubs for each required folder, a personalized AGENTS.md based on the course baseline, and the exact one-line CLAUDE.md.

**What I kept / changed:** Reviewed each file before committing. kept the structure as drafted, just double-checked the dates and job titles were right.

## 2026-10-08 — Stage 3: Report the Findings

**What I asked:** I used AI to help me explain the results of my perfect competition model, including binding and slack constraints, shadow prices, the tomato marginal-cost dip, and how my results compared with my original Stage 1 prediction. I also used it to help organize my decision memo.

**What the AI did:** AI asked questions that helped me explain the model results in my own words and provided reference numbers and figures to support my analysis. During the review, an error was identified in the reference sheet about temporary workers, and the explanation for the tomato cost dip needed to be corrected.

**What I kept / changed:** I kept the explanations that matched my model and corrected the temporary-worker constraint after Claude checked the shadow price and showed me the result. I also revised the tomato dip explanation to reflect the owner-first labor rule. The workbook was updated with an additional column showing the corrected tomato marginal costs so the numbers in my analysis could be verified.

**Reflection:** One concrete thing I verified was the drop in tomato marginal cost between bed 5 and bed 6. I checked the Excel workbook by opening the `MarginalCostSchedules` tab and looking at column I, labeled "Tomato MC, owner-first." The values were $7,660.86 for bed 5 and $4,906.275 for bed 6. This confirmed that the marginal cost drops at bed 6.

This check mattered because I needed to make sure my explanation matched the actual model rather than just assuming the cost pattern made sense. The drop happens because the farm uses up the owner's 720 available labor hours and begins relying more on temporary workers, who have a lower hourly rate. If I had not verified the numbers, I could have incorrectly described the tomato marginal cost as continuing to rise or given an explanation that did not match the workbook. Checking the source helped me connect the numbers to the owner-first labor rule and make my analysis more accurate.

## 2026-10-10 — Research Paper: Leasing Solar in Hawaiʻi

**What I asked:** I asked AI to help me understand the assignment, find and check sources, calculate the numbers, build a chart for my research, and review my paper drafts. My topic was whether leasing solar would save me money over 25 years compared to paying the electric company.

**What the AI did:** AI helped me break down the assignment and organize my research. It reviewed the EIA information, helped calculate the yearly increase in my lease payment, built the 25-year savings model and Figure 1, and pointed out areas in my paper that needed improvement. It also helped put my sections together into drafts for me to review and revise.

**What I kept / changed:** I used the feedback to rewrite Sections 1, 2, 4, 5, and 6 in my own words. I also removed sentences that were not needed and dropped the statement about lower-income families because I did not have a source to support it. I kept the information that matched my bills, lease documents, and research, but I made changes when something did not match or needed to be explained more clearly.

**Reflection:** AI helped me organize my research, review my sources, and improve my understanding of the numbers in my solar lease project. However, I learned that I cannot assume everything AI provides is correct. One error I caught was that my first draft used $700 as my previous electricity cost and $175 as my new cost. I checked my actual bills and found that my December 2023 total was $499.18, while my current total was $355.30. I also checked the lease payment information and the EIA data because some of the numbers in my notes did not match the original documents. A note written by another AI tool included an unverified 2024 residential electricity price of 42.86 cents per kilowatt-hour, so I checked the EIA information and used the 38.00-cent figure I could verify instead. Finally, I verified the year 1 calculation using a calculator. I multiplied the $202 lease payment by 1.0471 to get about $211.52 with tax, subtracted that amount and my $0.87 electric bill from the $337.32 average monthly electricity bill, and got about $124.93 in monthly savings. Multiplying that by 12 gives about $1,499 in savings for year 1, which matches the model. This showed me that AI can help with research and feedback, but I am responsible for checking the numbers and making sure my final work is accurate.

---

## Template for future entries

## YYYY-MM-DD — [Topic]

**What I asked:**

**What the AI did:**

**What I kept / changed:**

Asked Claude to critique my Case 1 brief draft; it flagged two gaps (idle beds, tipping-point reasoning) which I added myself.
