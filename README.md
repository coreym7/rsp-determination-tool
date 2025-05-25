# RSP Requirements Determination Engine

This project was created to fulfill a critical compliance gap when a district’s diagnostic vendor did not yet support Reading Success Plan (RSP) eligibility reporting. It interprets complex DESE guidelines and dynamically determines which students require an RSP based on multi-metric diagnostic and programmatic data.

---

## 🧭 What This System Does

- 📘 **Parses DESE RSP Policy Logic** – Converts policy documents into programmatic matrices for cut scores and risk rules.
- 🧠 **Multi-Metric Evaluation** – Evaluates students using both standalone risk flags and weighted combinations (e.g. 2 of 3 indicators = RSP required).
- 📝 **Interprets Diagnostic Reports** – Ingests raw assessment exports and identifies qualifying risk factors.
- 📊 **Outputs Eligibility Status** – Marks students as requiring or not requiring an RSP, with explanations tied to risk categories.
- 👩‍🏫 **Teacher-Level Sorting** – Includes homeroom teacher field to support filtering and targeted intervention by classroom.
- 🔁 **Still Used On-Demand** – Although vendor reports now exist, this tool is still used for real-time local reevaluation.

---

## 🔗 Table of Contents

1. [Purpose](#purpose)
2. [Inputs](#inputs)
3. [Logic Design](#logic-design)
4. [Output](#output)
5. [Use Cases](#use-cases)
6. [Status](#status)

---

## 📌 Purpose

The Missouri Department of Elementary and Secondary Education (DESE) released a complex policy defining which students are considered “at risk” for reading success. This tool was designed to automate eligibility determination when vendor tools had not yet caught up with those rules.

---

## 📥 Inputs

- Diagnostic assessment export (CSV)
- extract from SIS with studnet ID matched to homeroom Teacher
---

## 🔧 Logic Design

- Cut scores vary by **grade** and **time of year**
- Some metrics (e.g. "Well Below Basic") independently qualify a student
- Others require a **multi-flag combination**, such as:
  - “2 of 3” risk areas met → RSP required
- User created matrices to encode cut scores, and a logic flowchart to define all policy pathways
- All logic applied in Python using a clean, modular evaluation engine

---

## 📤 Output

- Student-level report showing:
  - RSP Required: Yes/No
  - Risk factors triggered
  - Justification narrative
- Exported to CSV for intervention teams and admin review
- Includes homeroom teacher as a sortable field for targeted classroom intervention

---

## 🛠 Use Cases

- Original purpose: fill gap before vendor support existed
- Still used for:
  - Mid-cycle reevaluations
  - Post-assessment updates
  - Building-specific deep dives

---

## 📌 Status

**Active (on-demand use only)** – Logic preserved, generalized, and still used internally when faster turnaround is needed than vendor reports provide.
