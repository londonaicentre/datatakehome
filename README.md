# Data Engineering — Take-Home Assessment

## Scenario

You are a data engineer at an NHS hospital that has recently migrated from a legacy EHR system to a new system. During the migration, historical data has been extracted as CSV files. You have been asked to build a data pipeline that produces analyst-ready data for the Emergency Department (ED) clinical team. Your line manager has asked you to implement a Extract Load Transform (ELT) approach.

The ED clinical lead wants to answer two questions:

1. **What is the average length of stay for ED encounters per presenting condition?**
2. **Which patients are frequent ED attenders (3+ visits in 12 months)?**

The data you have been given is in the `data/` directory.

---

## Data Files

| File | Description |
|------|-------------|
| `data/patients.csv` | Patient demographics |
| `data/encounters.csv` | All encounter records (not just ED) |
| `data/encounters_schema_change_batch.csv` | A batch of encounters from a second source system with a different schema |
| `data/conditions.csv` | Patient conditions / diagnoses |
| `data/observations.csv` | Clinical observations (vitals, lab results) |
| `data/medications.csv` | Medication prescriptions |
| `data/clinical_notes.csv` | Free-text ED triage notes (for the bonus question only) |

---

## Part A: Data Loading

*Suggested time: ~30 minutes*

Load the raw CSV files into a queryable database (e.g. DuckDB, SQLite, Postgres, other) using your preferred approach.

---

## Part B: Data Assessment

*Suggested time: ~60 minutes*

You have been warned that `patients.csv` and `encounters.csv` contain data quality issues.

Now that data has been loaded, please assess these files using your preferred approach, and provide **written answers** to the following questions:

**B1. Identify at least 3 data quality issues in each of `patients.csv` and `encounters.csv`. For each issue:**
- What is the issue?
- Is it **blocking** (will cause incorrect analytics results) or **non-blocking** (cosmetic / should be flagged but won't break downstream outputs)?
- How would you handle it in your pipeline?

**B2. The file `encounters_schema_change_batch.csv` has a different schema. How would you unify this with the main encounters data?**

---

## Part C: Transformation Pipeline

*Suggested time: ~90 minutes*

Using your preferred approach, build a **pipeline** from your loaded raw data to **two analyst-ready outputs**:

1. **ED Length of Stay** — You have been asked to break this down by presenting condition where possible
2. **Frequent Attenders** — This should show frequent attenders over 12-month moving time windows

Please provide **brief written answers** to these questions:

**C1.** If this pipeline ran daily in production and one morning the source data file didn't arrive, how would you detect this? What would happen to the downstream tables?

**C2.** Describe one way you would detect a **silent failure** — where the pipeline completes successfully but the output data is wrong. Give a concrete example relevant to this dataset.

---

## Bonus (Optional)

`data/clinical_notes.csv` contains synthetic free-text ED triage notes. Describe (or implement) how you would extract **primary disorder** as structured information from these notes using an NLP or LLM approach.

Only attempt this if you finish the core task with time to spare.

---

## Tooling

During this task, please use whatever tools and approaches you are most comfortable with. We are evaluating your **approach** and **reasoning**, not a specific technology. Some options:

- dbt-core with DuckDB
- SQL scripts against DuckDB/SQLite/Postgres
- Python (pandas, polars, etc.)
- Any combination of the above

---

## What we're looking for

We are looking for the following, either in code or in your answers:

- Well structured pipeline (load -> staging -> transformation -> output)
- Evidence of understanding real data quality issues
- Tests that would catch problems if the data changed
- Documentation

---

## Submission

Submit your work as a **GitHub repository**. Organise your submission however you see fit — there is no required structure.

During the interview, **30-minutes** will be given to walk through your submission.

---

## Running out of time?

If you are unable to complete the task over the suggested time windows, please submit written responses about the approach you would have adopted.
