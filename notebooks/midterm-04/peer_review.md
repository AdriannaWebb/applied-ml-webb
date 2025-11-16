# Peer Review — Classification Analysis of the Titanic Dataset (Midterm Project)

- **Author reviewed:** Jarred Gastreich
- **Reviewed by:** Adrianna Webb
- **Notebook:** [Classification Analysis of the Titanic Dataset (.ipynb)](https://github.com/jarjarredred/ml-modules/blob/main/notebooks/midterm/mlmidterm_jarred.ipynb)

## 1. Clarity & Organization

**What worked well**

- Clear section headers make the flow easy to follow.
- Missing-value summaries and describe() outputs are printed early, which grounds the later choices.

**Actionable suggestions**

- Reduce duplication in imports (many libraries repeated 2–3x). This improves readability and avoids the impression of copy/paste. 
  - Why: Cleaner top-cell improves maintainability and signals intentional choices.
  - How: Keep one consolidated import block.
- Remove redundant dataset loads (sns.load_dataset('titanic') appears multiple times) and the Windows path saving section unless it’s necessary for the assignment.
  - Why: Extra steps distract from the main workflow.

## 2. Feature Selection & Justification

**What worked well**

- Chosen features (pclass, sex, age, fare) are sensible and supported by your EDA and Titanic domain logic.
- You created derived features like family_size / is_alone, which aligns with known survival patterns.

**Actionable suggestions**

- Tie each selected feature to a specific insight from your plots.
  - Why: Strengthens the causal story between EDA and modeling.
  - How: “We observed higher survival among females (count plot), so sex is included.”

- State the target and encoding choices explicitly for every case.
  - Why: Keeps each modeling scenario self-contained and reproducible.
  - How: A short bullet list per case: target, features, encoding/NA handling.

## 3. Model Performance & Comparisons

**What worked well**

- You evaluated multiple models (Random Forest, Decision Tree) and reported accuracy, precision, recall, F1, plus confusion matrices.
- Stratified splits were used for at least one setup—nice for imbalanced labels.

**Actionable suggestions**

- Emphasize class-wise performance, not just overall accuracy.
  - Why: Survivor class is minority; accuracy can be misleading.
  - How: Call out survivor (class 1) recall in each model; compare where models miss.

- Consider simple regularization on the Decision Tree (max_depth, min_samples_split).
  - Why: Your DT underperforms RF—regularization may close the gap and improve generalization.

## 4. Reflection Quality

**What worked well**

- Reflections discuss missing data, overfitting, and the precision/recall trade-off—good conceptual grounding.
- You connected results to domain expectations (e.g., “women and children first”).

**Actionable suggestions**

- Be more specific with numbers in reflections.

- Propose targeted, testable next steps.
  - Why: Moves beyond narrative to an improvement plan.
  - How: “Next, tune DT max_depth grid [3, 5, 7]; try class-weight balancing for SVC; log-transform fare to reduce skew; re-test survivor recall.”