# Intelligent Decision Support Systems

Projects completed in collaboration with **Piotr Szymaczek** as part of the **Intelligent Decision Support Systems** course — MSc Computer Science (Artificial Intelligence specialisation), Semester 1.

Each project applies a different multi-criteria decision analysis (MCDA) methodology to a real-world or data-driven problem, implemented in Python as a Jupyter notebook with a detailed written report.

---

## Projects

| #   | Method                   | Problem domain                  | Notebook                                                                                     |
| --- | ------------------------ | ------------------------------- | -------------------------------------------------------------------------------------------- |
| 1   | UTA (Ordinal Regression) | Nuclear waste management        | [`Project1-UTA.ipynb`](./Project1-UTA.ipynb)                                                 |
| 2   | Preference Learning      | Medical diagnosis (mammography) | [`Raport_Projekt_2_Preference_learning.ipynb`](./Raport_Projekt_2_Preference_learning.ipynb) |
| 3   | PROMETHEE                | Esports performance ranking     | [`Projekt_3_ELECTRE_PROMETHEE.ipynb`](./Projekt_3_ELECTRE_PROMETHEE.ipynb)                   |

---

## Project 1 — UTA: Nuclear Waste Management

**Method:** UTA (UTilités Additives) — ordinal regression over an additive value function model.

Nuclear waste management involves evaluating 27 policy variants across three dimensions (reactor type × time horizon × financing model) on four cost criteria. The goal is to derive a utility function consistent with two stakeholder groups' stated preferences.

**Approach:**

- Modelled each criterion with 5-breakpoint piecewise linear utility functions
- Formulated as a **linear programme** that maximises the discrimination margin `ε` between preferred and non-preferred variant pairs
- Constraints enforce monotonicity, minimum per-criterion weight (≥ 10%), and weight normalisation

**Results:**

| Criterion              | Weight |
| ---------------------- | ------ |
| C1 (energy efficiency) | 19.8%  |
| C2 (radioactive waste) | 30.5%  |
| C3 (debt avoidance)    | 39.7%  |
| C4 (other costs)       | 10.0%  |

Top-ranked variant: **#9** with utility score `0.679` · Discrimination margin: `ε = 0.16`

---

## Project 2 — Preference Learning: Medical Diagnosis

**Method:** Comparison of three machine learning approaches for classification as a preference learning task.

Using the **Mammographic Mass dataset** (830 patients, 5 clinical features), the project frames tumour classification (benign / malignant) as a preference learning problem and benchmarks three models:

| Model            | Description                                                             |
| ---------------- | ----------------------------------------------------------------------- |
| **XGBoost**      | Gradient boosting over clinical features                                |
| **ANN-UTADIS**   | Neural network architecture inspired by the UTADIS multicriteria method |
| **Standard ANN** | Feedforward neural network baseline                                     |

Models are evaluated on accuracy, F1-score, and ROC-AUC. Feature importance and model interpretability are analysed to understand which clinical indicators drive the classification.

**Dataset:** BI-RADS score, patient age, mass shape, margin type, tissue density — approximately balanced classes (51% benign / 49% malignant).

---

## Project 3 — PROMETHEE: Esports Champion Ranking

**Method:** PROMETHEE (Preference Ranking Organisation Method for Enrichment Evaluation) — outranking via pairwise preference flows.

The problem: which ADC (Attack Damage Carry) champion is the strongest pick in competitive League of Legends? Data from LCK (Korean pro league) covering 12 champions with 5+ match appearances.

**Criteria:**

| ID  | Criterion           | Indifference `q` | Preference `p` |
| --- | ------------------- | ---------------- | -------------- |
| G1  | Win rate (%)        | 5                | 15             |
| G2  | KDA ratio           | 1.0              | 2.5            |
| G3  | Gold diff at 10 min | 50               | 300            |
| G4  | CS per minute       | 0.2              | 0.4            |
| G5  | Damage per minute   | 60               | 140            |

**Implementation:** marginal preference functions → weighted preference index → positive/negative/net flows → partial and complete ranking.

**Top 4 by net flow:**

| Rank | Champion | Net flow |
| ---- | -------- | -------- |
| 1    | Xayah    | +3.66    |
| 2    | Sivir    | +3.65    |
| 3    | Ziggs    | +2.07    |
| 4    | Jhin     | +1.62    |

## Reports

Some projects have an accompanying written report (PDF):

- [`Raport-Project1-UTA.pdf`](./Raport-Project1-UTA.pdf)
- [`Raport_3_ELECTRE_PROMETHEE.pdf`](./Raport_3_ELECTRE_PROMETHEE.pdf)
