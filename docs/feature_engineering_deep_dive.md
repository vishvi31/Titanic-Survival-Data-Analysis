# Feature Engineering Deep Dive — Titanic

Author: Vishvi
Branch: feature/feature-engineering-guide
Date: 2026-06-12

---

## Why Feature Engineering Matters

Raw Titanic data has 12 columns. After feature engineering,
the model has access to features that capture the REAL
patterns behind survival - not just raw numbers.

This single step often improves accuracy more than
switching models ever does.

---

## 1. Title Extraction from Name

```python
import re

def extract_title(name):
    match = re.search(r',\s*([^.]*)\.', name)
    return match.group(1).strip() if match else 'Unknown'

df['Title'] = df['Name'].apply(extract_title)
print(df['Title'].value_counts())

# Group rare titles together
title_map = {
    'Mr': 'Mr', 'Miss': 'Miss', 'Mrs': 'Mrs', 'Master': 'Master',
    'Dr': 'Rare', 'Rev': 'Rare', 'Col': 'Rare', 'Major': 'Rare',
    'Mlle': 'Miss', 'Ms': 'Miss', 'Mme': 'Mrs',
    'Don': 'Rare', 'Lady': 'Rare', 'Countess': 'Rare',
    'Jonkheer': 'Rare', 'Sir': 'Rare', 'Capt': 'Rare'
}
df['Title'] = df['Title'].map(title_map).fillna('Rare')
print(df.groupby('Title')['Survived'].mean())
```

Why it matters: 'Master' identifies young boys who had
much higher survival rates than 'Mr' (adult men).

---

## 2. Family Size and IsAlone

```python
df['FamilySize'] = df['SibSp'] + df['Parch'] + 1
df['IsAlone'] = (df['FamilySize'] == 1).astype(int)

print(df.groupby('FamilySize')['Survived'].mean())
print(df.groupby('IsAlone')['Survived'].mean())
```

Why it matters: Solo travelers had no one to help them
find lifeboats. Families of 2-4 had the best survival.
Families of 5+ struggled to stay together and evacuate.

---

## 3. FarePerPerson

```python
df['FarePerPerson'] = df['Fare'] / df['FamilySize']
print(df[['Fare', 'FamilySize', 'FarePerPerson']].head())
```

Why it matters: Raw Fare is skewed by group bookings.
FarePerPerson is a cleaner proxy for individual wealth.

---

## 4. Age Groups (handling non-linear age effects)

```python
def age_group(age):
    if age <= 12:
        return 'Child'
    elif age <= 19:
        return 'Teen'
    elif age <= 59:
        return 'Adult'
    else:
        return 'Senior'

df['AgeGroup'] = df['Age'].apply(age_group)
print(df.groupby('AgeGroup')['Survived'].mean())
```

Why it matters: Age has a non-linear relationship with
survival. Children had high survival, adults middling,
and seniors lower. A linear model misses this without bins.

---

## 5. HasCabin (presence as a signal)

```python
df['HasCabin'] = df['Cabin'].notna().astype(int)
print(df.groupby('HasCabin')['Survived'].mean())
```

Why it matters: Missing cabin data isn't random - it
correlates with lower class tickets. The ABSENCE of
data becomes a useful feature itself.

---

## 6. Filling Missing Age (smart imputation)

```python
# Instead of filling all missing ages with one value,
# fill based on Title group median - much more accurate
age_by_title = df.groupby('Title')['Age'].median()
print(age_by_title)

df['Age'] = df.apply(
    lambda row: age_by_title[row['Title']] if pd.isna(row['Age']) else row['Age'],
    axis=1
)
```

Why it matters: A 'Master' (young boy) with missing age
should get a child age, not the overall adult median.

---

## Summary Table

| New Feature | Built From | Why It Helps |
|---|---|---|
| Title | Name | Captures gender, age, social status |
| FamilySize | SibSp + Parch | Group evacuation dynamics |
| IsAlone | FamilySize | Solo travelers disadvantaged |
| FarePerPerson | Fare / FamilySize | Cleaner wealth proxy |
| AgeGroup | Age | Captures non-linear age effects |
| HasCabin | Cabin | Missingness as a signal |

---

Built by Vishvi - github.com/vishvi31
