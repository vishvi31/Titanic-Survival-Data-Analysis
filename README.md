# Titanic-Survival-Data-Analysis
Titanic Survival Data Analysis predicts the survival chances of the people including children, male, female, oldies in the tragedy of Titanic destruction.
# 🚢 Titanic Survival Data Analysis: A Comprehensive Data Science Investigation


### Titanic Survival Data

[train.csv](https://github.com/user-attachments/files/25268008/train.csv)




> **A complete end-to-end data science project analyzing factors that determined survival in the 1912 Titanic disaster using machine learning.**

---

## 📊 Project Overview

This project investigates the RMS Titanic disaster through the lens of data science, uncovering critical insights about how gender, socioeconomic status, age, and family structure influenced survival outcomes. Through comprehensive exploratory data analysis and predictive modeling, we reveal a tragic paradox: while the "women and children first" protocol clearly existed, **third-class children had lower survival rates than first-class men**.

### 🎯 Key Objectives

1. **Understand survival patterns** through statistical analysis
2. **Engineer meaningful features** from historical context
3. **Build predictive models** with 82%+ accuracy
4. **Extract actionable insights** about inequality in crisis situations
5. **Demonstrate end-to-end data science workflow**

---

## 🔍 Critical Findings

### The Numbers That Tell the Story

| Factor | Finding | Impact |
|--------|---------|--------|
| **Gender** | Women: 74.2% survival / Men: 18.9% survival | **3.9× difference** |
| **Class** | 1st: 63.0% / 2nd: 47.3% / 3rd: 24.2% | **2.6× difference** |
| **The Inequality Tragedy** | 3rd class children: 43.1% / 1st class men: 36.9% | **Poor children < Rich men** |
| **Family Size** | Solo: 30.4% / Medium (2-4): 61.8% / Large (5+): 13.4% | **U-shaped relationship** |

### 💔 The Most Shocking Discovery

**Third-class children (43.1% survival) fared worse than first-class men (36.9% survival)**

This reveals that socioeconomic inequality persisted even in a life-or-death situation, likely due to:
- Physical barriers (locked gates between classes)
- Distance from lifeboats (lower deck accommodations)
- Information gaps (language barriers, lack of crew communication)
- Structural disadvantages that money couldn't overcome in time

---

## 🤖 Model Performance

| Model | Validation Accuracy | AUC Score | Cross-Validation |
|-------|-------------------|-----------|------------------|
| **Logistic Regression** 🏆 | **82.7%** | **0.867** | 80.2% (±2.5%) |
| Random Forest | 79.9% | 0.853 | 83.0% (±2.5%) |
| Gradient Boosting | 78.2% | 0.822 | 80.8% (±3.7%) |

### Why Logistic Regression Won

1. **Interpretability**: Clear feature coefficients show what matters
2. **Generalization**: Best validation performance
3. **Simplicity**: Avoided overfitting with fewer parameters
4. **Statistical power**: Linear relationships captured the main effects well

---



---

## 🚀 Quick Start


### Running the Analysis

**Jupyter Notebook**
```bash
jupyter notebook notebooks/Titanic_Survival_Data_Analysis.ipynb
```

### Expected Output

- `comprehensive_eda.png` - 9-panel visualization showing all key patterns
- `titanic_predictions.csv` - Competition-ready predictions
- `detailed_predictions.csv` - Predictions with passenger info and probabilities
- `analysis_summary.txt` - Executive summary report

---

## 🔬 Methodology

### 1. Exploratory Data Analysis

**Statistical Testing:**
- Chi-square test for gender (χ² = 260.72, p < 0.001)
- T-test for age differences (p = 0.0023)
- Correlation analysis for numeric features

**Visualizations:**

<img width="5970" height="3543" alt="comprehensive_eda" src="https://github.com/user-attachments/assets/42c84b54-c242-40a2-85bb-9be1f168fbfb" />


- Survival distributions by key demographics
- Gender × Class interaction heatmap
- Age and fare distributions
- Family size U-curve analysis

### 2. Feature Engineering

**Created Features:**
1. `FamilySize` - Total family members (SibSp + Parch + 1)
2. `IsAlone` - Binary solo traveler indicator
3. `Title` - Extracted from name (Mr, Mrs, Miss, Master, Rare)
4. `AgeGroup` - Categorical bins (Child, Teen, Adult, Middle, Senior)
5. `FarePerPerson` - Wealth per capita proxy
6. `FareGroup` - Quartile-based fare categories
7. `HasCabin` - Binary cabin information presence
8. `IsChild` - Children under 16 (evacuation priority)
9. `IsSenior` - Elderly passengers (60+)

**Data Preprocessing:**
- Age: Imputed using median by Title × Class
- Fare: Filled missing with median
- Embarked: Filled with mode (Southampton)

### 3. Model Training

**Models Evaluated:**
- Logistic Regression (with StandardScaler)
- Random Forest (200 trees, max_depth=10)
- Gradient Boosting (200 estimators, learning_rate=0.05)

**Validation Strategy:**
- 80-20 train-validation split
- Stratified sampling to preserve class balance
- 5-fold cross-validation for robustness

### 4. Evaluation Metrics

- **Accuracy**: Overall correct predictions
- **AUC-ROC**: Discrimination ability
- **Precision/Recall**: Class-specific performance
- **Cross-Validation**: Generalization estimate

---

## 📈 Key Insights

### 1. Gender: The Dominant Factor

- Women were **3.9× more likely** to survive than men
- This confirms the "women and children first" evacuation protocol
- However, class heavily moderated this effect:
  - 1st class women: 96% survival
  - 3rd class women: 46% survival

### 2. Class: The Hidden Determinant

- 1st class passengers were **2.6× more likely** to survive than 3rd class
- This wasn't just about money - it was about:
  - **Physical location**: Higher decks = closer to lifeboats
  - **Information access**: Crew warnings reached wealthy first
  - **Social priority**: Deference to upper class was institutional

### 3. Family Dynamics

**U-Shaped Relationship:**
- **Solo travelers (30% survival)**: No assistance during evacuation
- **Small families (62% survival)**: Mutual support + manageable coordination
- **Large families (13% survival)**: Coordination difficulty + staying together despite danger

**Possible explanations:**
- Families prioritized staying together over survival
- Large groups moved slower in panicked evacuation
- Parents sacrificed spots for children

### 4. Age: Moderated by Class

- Overall, survivors were slightly younger (28.3 vs 30.6 years)
- BUT: This advantage disappeared for third-class children
- Children were protected within their class, not universally

---

## 💡 Historical Context & Modern Relevance

### What This Reveals About 1912 Society

1. **Strict gender norms**: "Women first" was law, not suggestion
2. **Physical class separation**: Gates literally divided passengers
3. **Information inequality**: Warnings propagated by social network
4. **Wealth bought safety**: Better location + priority = survival

### Modern Parallels

This analysis has disturbing parallels to contemporary disasters:

| Historical | Modern Parallel |
|-----------|----------------|
| Locked gates between classes | Geographic segregation in cities |
| Lower decks farther from escape | Poor neighborhoods in flood zones |
| Language barriers for immigrants | COVID-19 information inequality |
| Crew priority to wealthy | Emergency services response times |

**Key Lesson**: In crises, existing inequalities are amplified, not erased.

---

## ⚠️ Limitations & Considerations

### Data Limitations

1. **Missing cabin data (77%)**: Likely not recorded for lower classes
2. **Missing age data (20%)**: Required imputation
3. **Survivorship bias**: Only includes people who boarded
4. **Historical accuracy**: 1912 record-keeping was imperfect

### Model Limitations

1. **Cannot account for luck**: Random factors (location during impact, lifeboat proximity)
2. **Doesn't capture heroism**: Individual sacrifices and bravery
3. **Assumes pattern stability**: Test data must match training distribution

### Ethical Considerations

**⚠️ CRITICAL**: This model should **NEVER** be used for:
- Modern triage decisions
- Evacuation prioritization
- Any life-or-death decision-making

**Purpose**: Understanding history, NOT creating policy.

---

## 🎓 What I Learned

### Technical Skills

- Advanced feature engineering from domain knowledge
- Proper handling of missing data with contextual imputation
- Model comparison methodology beyond simple accuracy
- Statistical significance testing for validating findings

### Data Science Process

- Domain research before analysis yields better features
- Visualization as discovery tool, not just presentation
- Critical evaluation of model assumptions and limitations
- Communication of technical findings to non-technical audience

### Domain Knowledge

- Historical context transforms data interpretation
- Social structures leave measurable signatures in data
- Disasters reveal underlying societal patterns
- Every data point represents a human life

---

## 🚀 Future Work

### Potential Improvements

1. **Geographic Analysis**
   - Map cabin locations to lifeboat proximity
   - Analyze ship layout and evacuation routes
   - Consider impact location effects

2. **Network Analysis**
   - Study family and group ticket bookings
   - Analyze last names for extended family networks
   - Investigate crew-passenger relationships

3. **Advanced Modeling**
   - Neural networks for complex interactions
   - Ensemble stacking (combining model predictions)
   - Bayesian approaches for uncertainty quantification

4. **External Data Integration**
   - Crew records and assignments
   - Timeline of disaster (who knew what when)
   - British/US inquiry testimonies

5. **Causal Inference**
   - Move beyond correlation to causation
   - Estimate treatment effects of interventions
   - Control for confounding variables properly

---

## 📚 Technologies Used

- **Python 3.8+**: Core programming language
- **pandas**: Data manipulation and analysis
- **numpy**: Numerical computations
- **scikit-learn**: Machine learning models and evaluation
- **matplotlib & seaborn**: Data visualization
- **scipy**: Statistical testing
- **Jupyter**: Interactive analysis environment

---

## 📖 References

### Historical Sources

1. Lord, Walter (1955). *A Night to Remember*
2. British Wreck Commissioner's Inquiry (1912)
3. US Senate Inquiry into Titanic Disaster (1912)
4. Encyclopedia Titanica - www.encyclopedia-titanica.org

### Technical Resource

1. Kaggle Titanic Competition - https://www.kaggle.com/c/titanic

---

## 🤝 Contributing

Contributions are welcome! Areas for improvement:

- Additional feature engineering ideas
- Alternative modeling approaches
- Enhanced visualizations
- Historical context additions
- Code optimization

Please open an issue first to discuss proposed changes.

---

## 📧 Contact

**Author**: [Vishvi]  
**Email**: [12thc.vishvi.30@gmail.com]  
**LinkedIn**: [Vishvi Vishvi]  
**GitHub**: [vishvi31]  

---

## 🙏 Acknowledgments

- **Kaggle** for hosting the Titanic dataset and competition
- **Titanic historians** for maintaining accurate records
- **Survivors and victims** - may their stories not be forgotten

---

## 💭 Final Thoughts

This project demonstrates that data science is more than algorithms and accuracy scores. It's about:

1. **Understanding human stories** behind the numbers
2. **Revealing hidden patterns** in historical events
3. **Learning from the past** to inform present decisions
4. **Communicating insights** that resonate with people
5. **Maintaining ethical awareness** of impact

The Titanic disaster claimed 1,502 lives. Our model achieves 83% accuracy, but the 17% it misses represents real people with real stories. 

**Remember: Every data point is a person.**

---

*This project was created as a comprehensive data science portfolio piece demonstrating end-to-end analysis, from exploratory data analysis through predictive modeling to actionable insights.*

**⭐ If you found this analysis valuable, please star this repository!**
