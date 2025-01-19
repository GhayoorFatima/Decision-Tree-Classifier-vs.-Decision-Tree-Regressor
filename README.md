# Decision-Tree-Classifier-vs.-Decision-Tree-Regressor
Decision trees are a cornerstone of machine learning, known for their simplicity and versatility. They are widely used for both classification and regression tasks, but understanding the differences between a Decision Tree Classifier and a Decision Tree Regressor is crucial for choosing the right approach for your problem.

---

## What is a Decision Tree?

A decision tree is a hierarchical structure that splits data into subsets based on feature values. Each internal node represents a decision, each branch corresponds to an outcome, and each leaf node provides a prediction. The goal is to maximize predictive accuracy by minimizing uncertainty or error at each split.

---

## Key Differences: Classifier vs. Regressor

### 1. Purpose

**Decision Tree Classifier:** Used for classification tasks, predicting discrete labels or categories.  
*Example:* Determining if a loan application will be approved (Yes/No).

**Decision Tree Regressor:** Used for regression tasks, predicting continuous numerical values.  
*Example:* Estimating house prices based on features like size and location.

---

### 2. Output

- **Classifier:** Produces a class label or a probability distribution over classes.
- **Regressor:** Produces a continuous numerical value, typically the mean of the target variable in the leaf node.

---

### 3. Splitting Criteria

The splitting criteria determine how a dataset is divided at each node.

#### For Classifiers

- **Gini Impurity:**

  \[ G = 1 - \sum_{i=1}^{k} p_i^2 \]

- **Entropy (Information Gain):**

  \[ E = - \sum_{i=1}^{k} p_i \log_2(p_i) \]

#### For Regressors

- **Mean Squared Error (MSE):**

  \[ \text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \bar{y})^2 \]

- **Mean Absolute Error (MAE):**

  \[ \text{MAE} = \frac{1}{n} \sum_{i=1}^{n} |y_i - \bar{y}| \]

---

### 4. Leaf Nodes

- **Classifier:** Represents a class label or a probability distribution over classes.
- **Regressor:** Represents a numerical value, usually the mean of the target variable in that subset.

---

## Mathematical Examples

### Example 1: Decision Tree Classifier (Predicting Loan Approval)

**Dataset:**  
Features: Income (Low, Medium, High), Credit Score (Good, Bad).  
Target: Loan Approval (Yes/No).

At the root, we have 10 samples: 6 "Yes" and 4 "No".

#### Step 1: Calculate Entropy at the Root

\[
E_{\text{root}} = - \left(\frac{6}{10} \log_2 \frac{6}{10}\right) - \left(\frac{4}{10} \log_2 \frac{4}{10}\right)
\]

\[
E_{\text{root}} \approx 0.971
\]

#### Step 2: Split on Income

- **Low:** 3 "Yes", 1 "No".  
  \[ E_{\text{Low}} \approx 0.811 \]
- **Medium:** 3 "Yes", 2 "No".  
  \[ E_{\text{Medium}} \approx 0.971 \]
- **High:** 0 "Yes", 1 "No".  
  \[ E_{\text{High}} = 0 \]

#### Step 3: Weighted Entropy After Split

\[
E_{\text{split}} = \frac{4}{10} E_{\text{Low}} + \frac{5}{10} E_{\text{Medium}} + \frac{1}{10} E_{\text{High}}
\]

\[
E_{\text{split}} \approx 0.810
\]

#### Step 4: Information Gain

\[
\text{IG} = E_{\text{root}} - E_{\text{split}}
\]

\[
\text{IG} \approx 0.161
\]

The split on Income reduces entropy by 0.161. The feature with the highest Information Gain is selected for the split.

---

### Example 2: Decision Tree Regressor (Predicting House Prices)

**Dataset:**  
Features: Size (sq ft), Number of Rooms.  
Target: House Price (in $).

At the root, the target values are: [200k, 250k, 300k, 350k, 400k].

#### Step 1: Calculate MSE at the Root

\[
\bar{y} = 300k
\]

\[
\text{MSE}_{\text{root}} = \frac{1}{5} \left[(200 - 300)^2 + (250 - 300)^2 + \dots + (400 - 300)^2 \right]
\]

\[
\text{MSE}_{\text{root}} = 5000
\]

#### Step 2: Split on Number of Rooms

- **2 Rooms:** [200k, 250k]  
  \[ \bar{y} = 225k, \text{MSE}_{\text{2 Rooms}} = 625 \]
- **3 Rooms:** [300k, 350k, 400k]  
  \[ \bar{y} = 350k, \text{MSE}_{\text{3 Rooms}} = 1666.67 \]

#### Step 3: Weighted MSE After Split

\[
\text{MSE}_{\text{split}} = \frac{2}{5} \times 625 + \frac{3}{5} \times 1666.67
\]

\[
\text{MSE}_{\text{split}} = 1250
\]

The split minimizes the overall MSE, and the feature with the lowest MSE is selected for the split.

---

## Comparison Table

| Feature                     | Decision Tree Classifier               | Decision Tree Regressor              |
|-----------------------------|-----------------------------------------|---------------------------------------|
| **Purpose**                 | Predicts discrete labels/categories    | Predicts continuous numerical values |
| **Output**                  | Class labels or probabilities          | Continuous values                    |
| **Splitting Criteria**      | Gini Impurity, Entropy                 | MSE, MAE                             |
| **Leaf Node**               | Class label or probability distribution| Mean of target values                |

---

## Conclusion

Both decision tree classifiers and regressors are powerful tools, but their use depends on the nature of the problem. If you’re dealing with discrete categories, the classifier is your go-to option. For continuous numerical predictions, the regressor shines. By understanding their differences and underlying math, you can harness their full potential for your machine learning tasks.
