# Week 3 Assignment: ICU Stays Dataset Analysis

## I 320D: Data Science for Biomedical Informatics | Spring 2026

### 📋 Assignment Version B

---

## 🎯 This Week's Mantra

> **"Every Column Tells a Story"**

In this assignment, you'll apply the 10-Point Data Inspection to a real-world healthcare dataset from the MIMIC-IV database focusing on ICU stays. By the end, you'll understand not just *what* the data contains, but *why* each variable matters for hospital operations and patient outcomes.

---

## Learning Objectives

By completing this assignment, you will be able to:

1. ✅ Apply the systematic 10-Point Inspection to a new healthcare dataset
2. ✅ Identify and classify feature types (continuous, discrete, categorical, ordinal, datetime)
3. ✅ Detect and document data quality issues (missing values, unexpected values, duplicates)
4. ✅ Research and document clinical meaning for healthcare variables
5. ✅ Create meaningful data groupings based on clinical standards
6. ✅ Formulate answerable research questions about ICU utilization patterns

---

## About the Dataset

**Dataset:** MIMIC-IV ICU Stays  
**Source:** MIMIC-IV Clinical Database (subset)  
**File:** `icustays.csv`  
**Focus:** ICU admission patterns and length of stay

### Clinical Context

Intensive Care Units (ICUs) are specialized hospital units that provide critical care to patients with severe or life-threatening conditions. Understanding ICU utilization patterns is crucial for:

- Hospital capacity planning and resource allocation
- Quality improvement initiatives
- Predicting patient outcomes
- Reducing healthcare costs while maintaining care quality
- Staffing decisions and shift planning

The MIMIC (Medical Information Mart for Intensive Care) database is a freely accessible critical care database that has been instrumental in healthcare research worldwide.

---

## Getting Started

First, load the dataset and import your libraries:

```python
# Import libraries


# Load the dataset


# Display first few rows to confirm it loaded

```

---

## Part 1: The 10-Point Data Inspection (40 points)

Complete each inspection step and document your findings.

### Step 1: Shape (4 points)

**Your Code:**
```python

```

**Your Findings:**
- How many rows (observations)? _______________
- How many columns (features)? _______________
- What does each row represent in clinical terms? _______________

---

### Step 2: Column Names (4 points)

**Your Code:**
```python

```

**Your Findings:**
- List all column names:

- Which columns might need further research to understand? (Hint: What do the abbreviations mean?)

---

### Step 3: Data Types (4 points)

**Your Code:**
```python

```

**Your Findings:**
- Which columns are numeric (int64 or float64)?

- Which columns are categorical (object/string)?

- Are there any columns that should be a different data type? (Hint: Think about the time-related columns)

---

### Step 4: First Look (4 points)

**Your Code:**
```python

```

**Your Findings:**
- What do the actual values look like?

- What do you notice about the care unit names?

- What format are the dates/times in?

---

### Step 5: Last Look (4 points)

**Your Code:**
```python

```

**Your Findings:**
- Does the data end cleanly?

- Are the last rows consistent with the first rows?

---

### Step 6: Memory Usage (4 points)

**Your Code:**
```python

```

**Your Findings:**
- How much memory does the dataset use? _______________ KB (or MB)
- Is this a "small" or "large" dataset by data science standards?

---

### Step 7: Missing Values (4 points)

**Your Code:**
```python

```

**Your Findings:**
- Which columns have missing values (according to `.isnull()`)?

- What percentage of each column is missing?

- In a clinical context, why might missing values be particularly problematic for ICU data?

---

### Step 8: Duplicates (4 points)

**Your Code:**
```python

```

**Your Findings:**
- Are there any duplicate rows? _______________
- Are all `stay_id` values unique? _______________
- Are all `subject_id` values unique? _______________ (Why might this be different from `stay_id`?)

---

### Step 9: Basic Statistics (4 points)

**Your Code:**
```python

```

**Your Findings:**
- What is the range of Length of Stay (LOS) values? _______________ to _______________ days
- What is the mean LOS? _______________ days
- What is the median LOS? _______________ days
- Why might the mean and median be different? What does this tell you about the distribution?

---

### Step 10: Unique Counts (4 points)

**Your Code:**
```python

```

**Your Findings:**
- How many unique patients (`subject_id`) are in the dataset? _______________
- How many unique ICU types (`first_careunit`) are there? _______________
- Does the number of unique `stay_id` values match the number of rows? _______________
- What does it mean that there are more rows than unique patients?

---

## Part 2: Data Dictionary (20 points)

Complete the following data dictionary. For each column, you must:
1. **Research** the clinical meaning
2. **Identify** the feature type (Continuous, Discrete, Categorical-Nominal, Categorical-Ordinal, Datetime, Identifier)
3. **Document** the valid values/range you observe
4. **Note** any issues or questions

| Column | Description | Feature Type | Valid Values/Range | Notes/Issues |
|--------|-------------|--------------|-------------------|--------------|
| `subject_id` | | | | |
| `hadm_id` | | | | |
| `stay_id` | | | | |
| `first_careunit` | | | | |
| `last_careunit` | | | | |
| `intime` | | | | |
| `outtime` | | | | |
| `los` | | | | |

### Clinical Research Questions for Version B

Answer these questions based on your research (you may need to use Google or the MIMIC documentation):

**1. What is the difference between a MICU (Medical ICU) and a SICU (Surgical ICU)? What types of patients would you expect in each?**

Your answer:

---

**2. What is a CCU (Coronary Care Unit) and what specialized equipment or monitoring would you expect there?**

Your answer:

---

**3. Why do hospitals have different types of ICUs rather than one general ICU? What are the advantages of specialization?**

Your answer:

---

**4. What is "step-down" care (like Neuro Stepdown)? How does it differ from intensive care?**

Your answer:

---

## Part 3: Data Validation (15 points)

### 3.1 Length of Stay Validation (5 points)

Write code to investigate the Length of Stay (LOS) distribution:
- How many stays are less than 1 day?
- How many stays are longer than 7 days?
- How many stays are longer than 14 days?
- What is the shortest stay? Does this make clinical sense?

**Your Code:**
```python

```

**Your Findings:**

- What might explain very short ICU stays (under 1 day)?

- What might explain very long ICU stays (over 7 days)?

---

### 3.2 Patient Stay Validation (5 points)

Write code to identify patients with multiple ICU stays:
- How many patients have exactly 1 ICU stay?
- How many patients have 2 or more ICU stays?
- Which patient has the most ICU stays, and how many?

**Your Code:**
```python

```

**Your Findings:**

- What percentage of patients have multiple ICU stays?

- What might this tell us about the patient population?

---

### 3.3 Transfer Validation (5 points)

Write code to identify patients who were transferred between ICU units (where `first_careunit` ≠ `last_careunit`):
- How many stays involved a transfer?
- What are the most common transfer patterns?

**Your Code:**
```python

```

**Your Findings:**

- What percentage of stays involve an ICU transfer?

- Why might a patient be transferred from one ICU type to another?

---

## Part 4: Create ICU Type Groups (10 points)

Create a new column called `icu_category` that categorizes the ICU types into broader clinical categories based on the **first_careunit**.

### Version B: ICU Specialty Categories

Use these categories based on clinical specialization:

| ICU Category | Units Included | Clinical Rationale |
|--------------|----------------|-------------------|
| Medical | MICU, MICU/SICU | Non-surgical critical illness (sepsis, respiratory failure, overdose) |
| Surgical | SICU, TSICU | Post-operative care, trauma, surgical complications |
| Cardiac | CCU, CVICU | Heart-related conditions (MI, heart surgery, arrhythmias) |
| Neurological | Neuro SICU, Neuro Stepdown, Neuro Intermediate | Brain/spine conditions (stroke, TBI, neurosurgery) |

**Note:** You'll need to look at the exact values in `first_careunit` to match them to these categories.

### Your Code:

```python
# First, see all unique values in first_careunit
print(df['first_careunit'].unique())

# Create the icu_category column
# You can use a dictionary mapping or a custom function with .apply()


```

### Verify your groupings worked:

```python
# Show counts per ICU category

```

### Calculate the average LOS for each ICU category:

```python
# Calculate the average Length of Stay for each ICU specialty

```

### Analysis Questions:

**1. How many ICU stays are in each specialty category?**

Your answer:

---

**2. What is the average Length of Stay for each ICU specialty category?**

Your answer:

---

**3. Which ICU category has the longest average stays? Does this make clinical sense based on what you learned about these specialties?**

Your answer:

---

## Part 5: Research Questions (15 points)

### 5.1 Write Three Answerable Questions (9 points)

Write three questions that THIS dataset can answer. Remember: the data can show relationships and patterns, but cannot prove causation.

**Your questions must explore these specific areas:**

1. **A question comparing Medical vs. Surgical ICU patterns:**


---

2. **A question about cardiac ICU (CCU or CVICU) utilization:**


---

3. **A question about the relationship between ICU type and transfers:**


---

### 5.2 Identify One Question the Data CANNOT Answer (3 points)

Write one question about **patient mortality or outcomes** that this dataset cannot answer, and explain why.

**Question:**


**Why it cannot be answered with this data:**


---

### 5.3 Grouping Analysis (3 points)

Answer this question using a groupby analysis:

**"What is the total number of ICU days (sum of LOS) for each ICU type?"**

**Your Code:**
```python

```

**Your Interpretation:**

Which ICU type accounts for the most total patient days? What does this tell you about resource allocation needs?


---

## Part 6: ICU Utilization Analysis (Bonus - 5 points)

Analyze which ICU types are most utilized and how patients move between them.

**Your Code:**
```python
# Analyze which ICU types are most common as first vs. last care unit
# Identify common transfer pathways
# Compare admission patterns by ICU type

```

### Bonus Questions:

**1. Which ICU type is most commonly the first unit for patients? Which is most commonly the last?**

Your answer:

---

**2. What are the 3 most common transfer patterns (first_careunit → last_careunit)?**

Your answer:

---

**3. Create a simple visualization (bar chart or similar) showing the number of stays by ICU category.**

Your code and visualization:

---

**4. Based on your analysis, if you were a hospital administrator deciding where to add beds, which ICU type would you prioritize and why?**

Your answer:

---

## Submission Checklist

Before submitting, verify you have completed:

- [ ] **Part 1:** All 10 inspection steps with code AND written findings
- [ ] **Part 2:** Complete data dictionary with all 8 columns filled in
- [ ] **Part 2:** Answered all 4 clinical research questions
- [ ] **Part 3:** All 3 validation checks with code and answers
- [ ] **Part 4:** Created `icu_category` column using the **ICU Specialty Categories**
- [ ] **Part 4:** Calculated average LOS by ICU category with interpretation
- [ ] **Part 5:** Three research questions (Medical vs. Surgical, Cardiac, Transfers)
- [ ] **Part 5:** One unanswerable question about mortality/outcomes
- [ ] **Part 5:** Total ICU days by type groupby analysis
- [ ] **Bonus (Optional):** ICU utilization analysis

---

## Grading Rubric

| Component | Points | Requirements for Full Credit |
|-----------|--------|------------------------------|
| Part 1: 10-Point Inspection | 40 | All 10 steps complete with working code AND thoughtful written analysis |
| Part 2: Data Dictionary | 20 | All 8 columns documented with correct feature types and clinical research |
| Part 3: Data Validation | 15 | All validation checks complete with working code and insightful answers |
| Part 4: ICU Categories | 10 | Working code that creates correct groups AND meaningful interpretation |
| Part 5: Research Questions | 15 | Three good questions in specified areas, one clear limitation, groupby analysis complete |
| **Bonus:** Utilization Analysis | +5 | Thoughtful analysis with visualization and administrative insight |
| **Total** | 100 (+5 bonus) | |

---

## Hints (Read Before You Get Stuck!)

### ⚠️ Common Pitfalls:

1. **ICU names are long and contain parentheses** - be careful when matching strings; use `str.contains()` if exact matching is difficult

2. **MICU/SICU is a combined unit** - decide which category it belongs to (Medical, Surgical, or both)

3. **Multiple rows per patient** - don't assume each row is a unique patient; use `subject_id` to identify patients

4. **Creating categories from text** - dictionaries with `.map()` work well, or you can use `np.select()` with conditions

### 💡 Pro Tips:

- Use `value_counts()` liberally to understand categorical columns
- When mapping categories, print your unique values first to avoid typos
- For transfer analysis, create a combined column like `df['first_careunit'] + ' → ' + df['last_careunit']`
- Consider using `groupby(['first_careunit', 'last_careunit'])` for transfer patterns

---

## Useful Resources

- **MIMIC-IV Documentation:** https://mimic.mit.edu/docs/iv/
- **ICU Types Explained:** Search "types of intensive care units"
- **Coronary Care Unit Info:** https://www.heart.org/
- **Pandas Mapping Documentation:** https://pandas.pydata.org/docs/reference/api/pandas.Series.map.html
- **Pandas GroupBy Documentation:** https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html

---

*Remember: "Every Column Tells a Story" - your job is to figure out what that story is!*

---

**Due Date:** [See Canvas]

**Submission:** Upload your completed Jupyter notebook (.ipynb) to Canvas
