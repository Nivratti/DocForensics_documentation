### Performance Metrics for Document Forensics

1. **Accuracy**:
    - Measures the proportion of correctly identified instances among all instances.
    - Formula: \( \text{Accuracy} = \frac{\text{Number of Correct Predictions}}{\text{Total Number of Predictions}} \)

2. **Precision**:
    - Evaluates the proportion of true positive predictions among all positive predictions.
    - Formula: \( \text{Precision} = \frac{\text{True Positives}}{\text{True Positives} + \text{False Positives}} \)

3. **Recall (Sensitivity)**:
    - Assesses the proportion of true positive predictions among all actual positives.
    - Formula: \( \text{Recall} = \frac{\text{True Positives}}{\text{True Positives} + \text{False Negatives}} \)

4. **F1-Score**:
    - Provides a balance between precision and recall.
    - Formula: \( \text{F1-Score} = 2 \cdot \frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}} \)

5. **False Positive Rate (FPR)**:
    - Measures the proportion of false positives among all actual negatives.
    - Formula: \( \text{FPR} = \frac{\text{False Positives}}{\text{False Positives} + \text{True Negatives}} \)

6. **False Discovery Rate (FDR)**:
    - Evaluates the proportion of false positive predictions among all positive predictions.
    - Formula: \( \text{FDR} = \frac{\text{False Positives}}{\text{True Positives} + \text{False Positives}} \)

7. **Matthews Correlation Coefficient (MCC)**:
    - Provides an overall measure of quality for binary classifications.
    - Formula: \( \text{MCC} = \frac{(\text{TP} \cdot \text{TN}) - (\text{FP} \cdot \text{FN})}{\sqrt{((\text{TP} + \text{FP})(\text{TP} + \text{FN})(\text{TN} + \text{FP})(\text{TN} + \text{FN}))}} \)

8. **Area Under the Receiver Operating Characteristic Curve (AUC-ROC)**:
    - Evaluates the performance of a binary classification model.
    - The closer the AUC-ROC value is to 1, the better the model is at distinguishing between the positive and negative classes.

9. **Confusion Matrix**:
    - A table that is used to evaluate the performance of a classification model.
    - Shows true positive, true negative, false positive, and false negative values which can be used to calculate other performance metrics.

10. **Mean Squared Error (MSE)**:
    - Measures the average squared differences between the estimated values and the actual values.
    - Formula: \( \text{MSE} = \frac{1}{n} \sum (y_{\text{true}} - y_{\text{pred}})^2 \)

