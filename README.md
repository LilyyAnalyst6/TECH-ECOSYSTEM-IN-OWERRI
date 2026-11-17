# Tech Ecosystem in Owerri

An analysis of who works in tech in Owerri, how they got there, what they earn, what holds them back and what they know about the policies that affect them.

| | |
|---|---|
| **Author** | Alexander Lilian |
| **Date** | November 2026 |
| **Tools** | Google Forms, Excel, Power BI Desktop |
| **Data** | Primary survey, 28 usable responses from 44 submissions |
| **Deliverables** | This report, a four-page Power BI dashboard, the cleaned dataset, power point presentation, data dictionary, cleaning log |

## Contents

1. [Executive summary](#1-executive-summary)
2. [Background and objectives](#2-background-and-objectives)
3. [Data and method](#3-data-and-method)
4. [Data model and measures](#4-data-model-and-measures)
5. [Dashboard walkthrough](#5-dashboard-walkthrough)
6. [Additional analysis](#6-additional-analysis)
7. [Recommendations](#7-recommendations)
8. [Limitations](#8-limitations)
9. [Next steps](#9-next-steps)
10. [Repository structure](#10-repository-structure)
- [Appendix A: Survey structure](#appendix-a-survey-structure)
- [Appendix B: Data dictionary](#appendix-b-data-dictionary)

---

## 1. Executive summary

The report analyses an online survey of people who live or work in Owerri and either work in tech or are learning a tech skill. After cleaning, 28 of 44 submissions were usable. The results are presented in a four-page Power BI dashboard: overview, people and participation, careers and opportunities, and challenges, government and support.

**What the data shows**

- **The sample is young and early in its career.** 26 of 28 respondents are aged 18 to 34, 24 are single, and 16 (57.1%) have less than a year in tech. 15 (53.6%) are still training.
- **Income is low and uneven.** 13 respondents (46.4%) report no income from tech. Only 2 (7.1%) earn above ₦150,000 a month. Of the 13 who have been paid for tech work, 12 received their first payment within a year.
- **Women are concentrated in the training stage.** Women are 42.9% of respondents, but 10 of the 12 women are still training and none of the 7 respondents in the "earn income from a tech skill" group is a woman. 9 of 12 women report no income, against 4 of 16 men.
- **Infrastructure is the main barrier.** 64.3% name poor or costly internet as a barrier and 60.7% name unstable power. 57.1% get less than 4 hours of electricity on a typical workday, and 32.1% do not own a laptop.
- **Awareness of policy is low.** 16 of 28 (57.1%) have never heard of Imo State tech policies, and 13 (46.4%) have never heard of the Nigeria Startup Act. 8 respondents (28.6%) have a registered business.
- **Respondents ask for funding first.** 75.0% chose funding or grants, followed by co-working space with power and internet (57.1%), mentorship (53.6%) and access to clients (50.0%).

Section 7 turns these findings into recommendations. Every figure comes from 28 respondents recruited through personal and professional networks, so the results describe the respondents and should not be read as a measure of all of Owerri.

## 2. Background and objectives

This project is my final project for a three-month intensive data analytics program. The brief was to research the tech ecosystem in Owerri: who works in it, what it takes to become a techie, gender and marital status, the brands, firms and hubs involved, and the government regulations that shape it.

I turned the brief into five questions:

1. Who works in tech in Owerri? (gender, age, marital status, education)
2. How do people get into tech, and what does it cost them?
3. What are income and working conditions like?
4. Which hubs, firms and brands do respondents know and use?
5. How aware are respondents of the policies that affect them, and what support do they want?

## 3. Data and method

### 3.1 Survey design

I built the survey in Google Forms. It has 27 questions and takes about five minutes. I kept it short to limit drop-off, and used mostly single-tap choices. Income, age, cost and time are asked in bands, not exact figures, because people answer bands more honestly.

Two screening questions end the survey for anyone who does not live or work in Owerri, or who is not active in tech. Demographic questions come last. The survey is anonymous. A final question asks whether the respondent will take part in a follow-up interview, and contact details collected for that purpose are not part of the dataset. The full structure is in [Appendix A](#appendix-a-survey-structure).

### 3.2 Collection and sample

The survey was shared online through personal and professional networks, including LinkedIn. This is a non-probability sample. 44 submissions were received. After cleaning, 28 remained.

### 3.3 Cleaning

I kept an untouched copy of the raw export and numbered every row so each change can be traced.

| Step | Action | Result |
|---|---|---|
| 1 | Remove respondents who chose "None of these" as their tech involvement | 10 rows removed |
| 2 | Remove respondents who answered No to living or working in Owerri but completed the survey | 6 rows removed |
| 3 | Check for duplicate submissions | None among the 28 kept (8 identical blank rows were among those removed) |
| 4 | Standardise labels, for example "Others" to "Other", and spelling variants of hub and firm names | Counts no longer split across spellings |
| 5 | Split multi-name answers into separate names and turn non-answers such as "Nil" and "None yet" into blanks | Names can be counted individually |
| 6 | Rename columns to short names and add numeric order codes for bands | Bands sort from low to high in charts |
| 7 | Convert checkbox answers into 0/1 columns with formulas | Each option can be counted |
| 8 |Dropped the "Do you live in Owerri"? column after filtering and cleaning | Every respondent answered "Yes" so it carries no information |

**Data quality notes**

- 3 respondents say they have not been paid for tech work but report income below ₦50,000. 1 respondent reports a first paid job but no income. I left these answers as given.
- The form could not limit the number of boxes ticked. 9 respondents chose more than the three barriers the question asked for, and 17 chose more than the two support options requested. All ticks are counted.
- 2 respondents chose "Prefer not to say" for income. They are kept in the denominator of every income percentage.
- 1 respondent selected the "Under 18" age band. The response is included in the figures. The Age group slicer on pages 1, 2 and 4 lets a reader exclude it.

### 3.4 Conventions

- Percentages use 28 respondents as the denominator unless stated, and are rounded to one decimal place.
- Questions with several answers allowed (learning route, barriers, payment methods, support) produce percentages that add up to more than 100%.
- Income is monthly income from tech work, in naira.

## 4. Data model and measures

| Table | Purpose |
|---|---|
| Clean Data | One row per respondent: 28 rows with the survey answers, plus helper columns for band order and the number of options ticked |
| Learning route | 0/1 columns for the checkbox questions. The support chart reads from it |
| Measure, Measure 1 | Tables that hold the DAX measures |

**Measures**

| Measure | What it reports |
|---|---|
| Total Respondents | Number of unique respondents (28) |
| Female Respondents, Male Respondents | Respondents by gender (12 and 16) |
| Female Participation %, Male Participation % | Each gender's share of respondents (42.9% and 57.1%) |
| Tech Learners | Respondents training in a tech skill (15) |
| Tech Earners | Respondents who earn income from a tech skill (7) |
| Tech Business Participants | Respondents who run or work in a tech business (6) |
| % Tech Earners | Tech Earners as a share of all respondents (25.0%) |
| % Not Yet Paid, Not Yet Paid | Respondents who have not yet been paid for tech work, as a share (53.6%) and as a count (15) |
| Income Earners | Respondents who report income from tech work (13). This is wider than Tech Earners, because it also counts learners and business participants who report income |

## 5. Dashboard walkthrough

The dashboard has four pages on a 1920 by 1080 canvas. Most pages carry slicers for gender, age group, main field and work status, so a reader can filter any chart to a subgroup.

<img width="985" height="547" alt="Tech ecosystem 1" src="https://github.com/user-attachments/assets/6bc72ff3-56f4-4d4b-bac3-43cd6e423b42" />




### Page 1: Overview

**Purpose.** Show who responded and how far along they are.

**Visuals.** Cards for total respondents, tech earners, tech learners and tech business participants, and for the share not yet paid. Charts for participant type, years in tech, work status, main field and government support rating.

**Findings**

- 15 respondents are learners (53.6%), 7 are earners (25.0%) and 6 run or work in a tech business (21.4%).
- 16 respondents have under a year in tech, 8 have 3 to 5 years, 3 have more than 5 years and 1 has 1 to 2 years.
- Work status is split between freelancers (8), students (8), employed (6), interns or trainees (4) and unemployed (2).
- UI/UX or graphic design is the largest field (8 respondents, 28.6%), ahead of software or web development (5) and data analytics (3). 6 chose "Other".

<img width="324" height="274" alt="gender" src="https://github.com/user-attachments/assets/25ed3e86-5f9c-4b99-aa4f-0dff9b2e26fa" />


### Page 2: People and participation

**Purpose.** Describe the people in the sample, with a focus on gender, age, marital status and education.

**Visuals.** Cards for female and male participation, and charts for gender, age group, marital status, education, family effect and gender by main field.

<img width="982" height="549" alt="Tech ecosystem 2" src="https://github.com/user-attachments/assets/657ef353-8e46-42b3-b696-26d14ebdb139" />

**Findings**

- 12 respondents are women (42.9%) and 16 are men (57.1%).
- Women are younger. 8 of the 12 women are aged 18 to 24, while 11 of the 16 men are aged 25 to 34.
- 24 respondents are single (85.7%). 2 are married and 2 are in a relationship.
- 14 respondents hold a bachelor's degree (50.0%), 7 an HND (25.0%), 5 a secondary school certificate (17.9%) and 2 an OND or NCE (7.1%).
- 22 of 28 say family or relationship status has had a positive effect or no effect on their tech career. 1 says it has had a negative effect only.
- UI/UX or graphic design is the largest field among women (5 of 12). Men are spread across "Other" (5), software or web development (4) and UI/UX (3). No woman works mainly in IT support or networking.



### Page 3: Tech careers and opportunities

**Purpose.** Show what it costs to learn, how long it takes to earn, what people earn, and how much they know about the policies that affect them.

**Visuals.** Cards for tech learners (15), income earners (13) and those not yet paid (15). Charts for monthly income, CAC registration, learning cost and time to first pay, and a table of awareness of four government policies.

<img width="963" height="543" alt="Tech ecosystem 3" src="https://github.com/user-attachments/assets/136a660b-8d37-43f3-b90c-e513c2841a58" />


**Findings**

- Learning is cheap for most. 21 of 28 respondents (75.0%) paid less than ₦50,000 to learn their skill, and 10 of them paid nothing. 4 paid more than ₦300,000.
- 15 respondents have not been paid yet, and all 15 are in the training group. Of the 13 who have been paid, 6 were paid within 6 months, 6 within 6 to 12 months and 1 after more than a year.
- 13 respondents (46.4%) report no income, 8 (28.6%) earn ₦50,000 to ₦150,000, and 2 (7.1%) earn above ₦150,000. 3 earn below ₦50,000 and 2 prefer not to say.
- Experience matters. 11 of the 16 respondents with under a year in tech report no income. Of the 11 with three or more years, 8 report income, 2 declined to say and 1 reports none.
- 8 respondents (28.6%) have a CAC-registered business, 13 (46.4%) do not, 4 say it does not apply and 3 are not sure. 4 of the 6 business participants are registered, against 2 of the 15 learners.
- Awareness of policy is low. 16 respondents have never heard of Imo State tech policies, 13 have never heard of the Nigeria Startup Act, 10 have never heard of the Nigeria Data Protection Act (NDPA) and 8 have never heard of NITDA programs. Few say they understand any of them.

| Policy | Never heard of it | Heard of it | Understand it |
|---|---|---|---|
| NDPA | 10 | 15 | 3 |
| Startup Act | 13 | 13 | 2 |
| NITDA | 8 | 15 | 5 |
| Imo State policies | 16 | 9 | 3 |



### Page 4: Challenges, government and ecosystem support

**Purpose.** Show the working conditions respondents face and the help they want.

**Visuals.** Charts for support options, hours of electricity, laptop brand, internet provider and government support rating.

<img width="956" height="534" alt="Tech ecosystem 4" src="https://github.com/user-attachments/assets/2f287bc2-acd1-43ff-aede-c9259f62c80b" />


**Findings**

- 16 respondents (57.1%) get less than 4 hours of electricity on a typical workday. This applies to 9 of the 12 women (75.0%) and 7 of the 16 men (43.8%).
- MTN is the main internet provider for 20 respondents (71.4%). Glo and Airtel have 3 each, and Starlink has 1.
- HP is the most used laptop brand (11 respondents, 39.3%), followed by Dell (7). 9 respondents (32.1%) have no laptop, and 7 of them are in the training group.
- The average rating of government support is 3.1 out of 5. 11 respondents rated it 4 or 5, 9 rated it 3, and 8 rated it 1 or 2. Interns and trainees rate it highest (4.0, n = 4) and the 2 unemployed respondents lowest (1.5).
- Funding or grants is the most requested support (21 respondents, 75.0%), followed by co-working space with power and internet (16, 57.1%), mentorship (15, 53.6%), access to clients (14, 50.0%), equipment (12, 42.9%), free or cheap training (10, 35.7%) and business registration help (4, 14.3%).


## 6. Additional analysis

These cuts come from the same cleaned dataset. They are not yet in the dashboard (see [Next steps](#9-next-steps)).

### Barriers

Poor or costly internet (18 respondents, 64.3%) and unstable power (17, 60.7%) lead the list, followed by the cost of a laptop (13, 46.4%). The cost of training and finding clients are each named by 9 respondents (32.1%). Respondents chose 3.3 barriers on average.

Women name internet and laptop cost most often (7 of 12 each, 58%), followed by power (6 of 12, 50%). Men name internet and power equally (11 of 16, 69%), then finding clients (7 of 16, 44%). With 12 women and 16 men, treat these gaps as indications to test with a larger sample.


### How people get paid

Bank transfer is the most common channel (13 respondents, 46.4%), followed by Opay (11, 39.3%). 8 chose "Other", 3 use Payoneer or Wise, 2 use Kuda, 2 use crypto and 1 uses Moniepoint.

### Hubs and firms

13 of 28 respondents said they belong to a hub or community. GDG Owerri is named most often (3 respondents). 21 different firms, schools and community groups were named when respondents were asked which tech organisations they know. ShopCop and DeFi FUTO are each named twice, and every other name once. The list mixes companies with training providers and events, so it should not be read as a directory of firms.

## 7. Recommendations

These are suggestions to test, not conclusions. Each rests on a small sample.

| Finding | Recommendation | Possible owner |
|---|---|---|
| 57.1% get under 4 hours of power a day. Internet and power are the top two barriers | Provide co-working space with backup power and reliable internet, with day passes for people in training | Hubs, state ICT agency, private sponsors |
| 46.4% name laptop cost as a barrier and 32.1% have no laptop. 7 of the 9 without one are in training | Pair training programs with device loans or subsidised laptops | Training providers, funders |
| 15 respondents have not been paid yet, but 12 of the 13 who have been paid were paid within a year. 50.0% want access to clients | Add placements, internships and client matching to the end of training programs | Training providers, hubs |
| 10 of 12 women are in training and none of the 7 respondents in the earning group is a woman. Women report more power problems and laptop cost barriers | Offer targeted mentorship and support for moving from training to paid work, and track gender at each stage with a larger sample | Hubs, training programs |
| 57.1% have never heard of Imo State tech policies. Only 28.6% have a registered business | Run short awareness sessions and registration clinics through hubs | State ministry, NITDA, hubs |
| 75.0% ask for funding or grants | Publish a one-page guide to available grants and small loans, with eligibility rules | State agencies, funders |

## 8. Limitations

- **Small sample.** 28 respondents means one person is 3.6 percentage points. Subgroup comparisons, such as women against men, are indicative only.
- **Non-random sample.** Respondents came through personal and professional networks and LinkedIn. The sample leans young, single and in training. It describes these respondents, not all of Owerri's tech workers.
- **Self-reported answers.** Income, cost and timing are not verified. Income and age are banded, so exact averages cannot be calculated.
- **Recruitment channel not recorded.** The survey did not track which channel each response came from, so channel bias cannot be measured.
- **Contradictions and limit breaks remain.** They are flagged in the cleaning notes and left in the data.
- **Training and earning overlap with gender.** The income gap between women and men mostly reflects who is still training. The sample is too small to compare pay for the same role.
- **Skipped questions.** For the hub and firm questions, a blank can mean no answer or none named.

## 9. Next steps

1. Increase the sample to at least 100 responses, with a separate link per channel so recruitment bias can be measured.
2. Run 5 to 8 follow-up interviews. 21 respondents agreed to be contacted. Use them to explain the income gap and the gender pattern.
3. Build a directory of hubs, firms and training providers from desk research, and map each regulation to the agency that enforces it.
4. Refresh the dashboard as new responses arrive.

## 10. Repository structure

```
.
├── README.md
├── dashboard/
│   └── Tech_Ecosystem_Owerri_Dashboard.pbix
├── data/
│   └── Owerri_Tech_Ecosystem_cleaned.xlsx
└── assets/
    ├── charts/
    └── dashboard/
```

**To open the dashboard:** download the `.pbix` file and open it in Power BI Desktop. The data is embedded, so no connection setup is needed.

---

## Appendix A: Survey structure

| Section | Topics | Questions |
|---|---|---|
| Screening | Lives or works in Owerri, involvement in tech | 2 |
| Role | Main field, work status, years in tech | 3 |
| Entry into tech | Learning route, learning cost, time to first pay, barriers | 4 |
| Income and working conditions | Monthly income, electricity, internet provider, laptop brand, payment methods | 5 |
| Firms and community | Hub membership, firms known, support wanted | 3 |
| Government and regulation | CAC registration, awareness of four policies, rating of government support | 3 |
| About you | Gender, age group, marital status, family effect, education | 5 |
| Close | One suggested change, interview consent | 2 |

https://docs.google.com/spreadsheets/d/19VBERgvobfef1TCs2PQlUxAHqsw_8_Bx8VrA_Et7hvs/edit?usp=sharing


## Appendix B: Data dictionary

The Clean Data table has 28 rows and 38 columns.

| Group | Columns | Notes |
|---|---|---|
| Identifier | Respondent ID | R001 to R028 |
| Role | Participant Type, Main Field, Work Status, Years in Tech | |
| Learning | Learning Route, Learning Cost, Time to First Pay | Learning Route allows several answers |
| Income and conditions | Monthly Income, Power Hours, Internet Provider, Laptop Brand, Payment Methods | Payment Methods allows several answers |
| Challenges | Barriers, Support Needed | Several answers allowed |
| Ecosystem | Hub Member, Firms Named, CAC Registered | Hub Member holds hub names. Blank means none named or skipped |
| Policy | Know NDPA, Know Startup Act, Know NITDA, Know Imo Policy, Gov't Rating | Awareness on a three-point scale. Rating from 1 to 5 |
| Demographics | Gender, Age group, Marital Status, Family Effect, Education | |
| Open response | Suggested Change, Interview Open | Suggested Change is free text as written |
| Helper columns | Years Order, Cost Order, First Pay Order, Income Order, Power Order, Age Order, Barriers Count, Support Count | Order codes sort bands from low to high. Counts show how many options were ticked |

