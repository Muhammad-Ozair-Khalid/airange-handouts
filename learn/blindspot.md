# Field notes: Blindspot

**Logistic regression, feature weights and adversarial input**

## A linear classifier has inspectable parts

A logistic-regression classifier computes a weighted sum of features, then compares the result with a decision threshold. A positive weight raises the logit; a negative weight lowers it. Feature coefficients describe the model’s behavior, not necessarily causal truth. A word can become a reassuring signal because of patterns in the training set.

An evasion task asks how an input can change while remaining within a budget. Here the original message is fixed and exactly four permitted words may be added, each with a stated cost. Evaluate candidate changes against the released coefficients and threshold. Then optimize cost and apply the explicit tie-breaking rule. A brute-force search over four-word combinations is small enough to audit and gives a useful cross-check for hand reasoning.

The file includes a small synthetic training set and a fitted linear classifier. It is not a chatbot, and the challenge is not solved by prompting an AI model. Robust systems test these edge cases, constrain features, and avoid treating a single score threshold as a complete security decision.

Learning reference: [scikit-learn linear models](https://scikit-learn.org/stable/modules/linear_model.html).

---
*AIRANGE Learning Lab · Medium · Use authorized challenge files only.*
