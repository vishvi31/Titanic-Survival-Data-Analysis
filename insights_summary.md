# 📊 Key Insights Summary — Titanic Survival Analysis

> A quick-reference card of the most important findings from this project.
> Full analysis: see the Jupyter Notebook.

---

## 🔢 Survival Statistics at a Glance

| Group | Survival Rate | Key Takeaway |
|---|---|---|
| **Women** | 74.2% | "Women first" protocol clearly in effect |
| **Men** | 18.9% | 3.9× lower survival than women |
| **1st Class** | 63.0% | Wealth = proximity to lifeboats |
| **2nd Class** | 47.3% | Middle ground |
| **3rd Class** | 24.2% | 2.6× lower than 1st class |
| **Solo travelers** | 30.4% | No support network |
| **Small families (2-4)** | 61.8% | Sweet spot — mutual aid |
| **Large families (5+)** | 13.4% | Coordination breakdown |

---

## 💔 The Inequality Paradox

> **3rd class children (43.1%) had lower survival than 1st class men (36.9%)**

This single statistic encapsulates the entire project:
socioeconomic inequality persisted even in a life-or-death crisis.

**Why?**
- Physical barriers (locked gates between classes)
- Lower decks = farther from lifeboats
- Language barriers and information gaps
- Crew deference to wealthy passengers

---

## 🤖 Best Model: Logistic Regression

| Metric | Score |
|---|---|
| Validation Accuracy | **82.7%** |
| AUC-ROC | **0.867** |
| Cross-Validation | 80.2% (±2.5%) |

Logistic Regression outperformed Random Forest and Gradient Boosting
due to better generalisation and interpretability.

---

## 🔑 Top Survival Predictors (Feature Importance)

1. **Sex** — single strongest predictor
2. **Pclass** — socioeconomic status
3. **Title** — extracted from name (Master = child male)
4. **FarePerPerson** — wealth proxy
5. **FamilySize** — group dynamics
6. **Age** — moderated by class
7. **HasCabin** — data presence = wealth signal
8. **IsAlone** — solo travelers at disadvantage

---

## 🛠️ Feature Engineering Highlights

| Feature | How Created | Why It Matters |
|---|---|---|
| `Title` | Extracted from Name | Captures gender + social status + age |
| `FamilySize` | SibSp + Parch + 1 | Group evacuation dynamics |
| `IsAlone` | FamilySize == 1 | Solo = lower survival |
| `FarePerPerson` | Fare / FamilySize | Better wealth proxy than raw fare |
| `AgeGroup` | Bins: Child/Teen/Adult/Senior | Age effects are non-linear |
| `HasCabin` | Cabin is not null | Data presence signals wealth |

---

## ⚠️ Ethical Note

This model is for **historical analysis only**.
It must never be used for real-world triage or life-or-death decisions.

Every data point = a real human life. 1,502 people died.

---

*Author: Vishvi | Part of Data Science Portfolio*
*GitHub: [vishvi31](https://github.com/vishvi31)*
