# Model Behaviour Limits: Thumb Up vs Fist
## 1. Expected Model Performance
In **standard, unobstructed scenarios** with clear gestures, the model consistently delivers accurate predictions:
- Standard thumb-up gesture (thumb fully extended upward, four fingers curled inward): The model predicts `thumb_up` with 100% confidence (see evidence: `standard_thumb_up_prediction.png`).
- Standard fist gesture (all five fingers fully curled into the palm, no fingers exposed): The model predicts `fist` with 100% confidence (see evidence: `standard_fist_prediction.png`).

## 2. Unstable/Inconsistent Prediction Scenarios
When testing **non-standard transition postures** (falling between thumb-up and fist), the model’s predictions exhibit significant fluctuations:
- For the same transition posture (fingers partially curled, thumb not fully extended): 
  - Initial test result: `thumb_up` 66% + `fist` 34% (see evidence: `label_flip_shake_1.png`).
  - After a slight adjustment of hand angle (no major gesture change): Prediction shifts to `thumb_up` 32% + `fist` 68% (see evidence: `label_flip_shake_2.png`).
- Another transition posture: Prediction shows `thumb_up` 57% + `fist` 43% (see evidence: `boundary_case_confidence_split.png`).

These results indicate the model lacks stability in judging "transition states" and cannot reliably categorize ambiguous gestures.

## 3. Misleading Confidence Score Scenarios
The model demonstrates **high-confidence yet completely incorrect predictions**:
- A standard fist gesture (all fingers curled, no thumb exposure) is falsely predicted as `thumb_up` with 100% confidence (see evidence: `high_confidence_misclassification.png`).

This outcome highlights a critical limitation: "high confidence does not equal correctness." The model’s unwarranted certainty in erroneous classifications can mask its inherent judgment flaws.

## 4. Root Causes of Misclassification
Combined with the training data , misclassifications stem from **structural limitations in pre-deployment data collection and taxonomy design**:
1. **Dataset Structural Limitations**:
   The training samples for `thumb_up` (34 images) and `fist` (31 images) feature relatively uniform postures (e.g., most fist samples are "tightly curled fists"). They lack diversity in transition postures, slightly deformed fists, and complex environmental conditions. The "non-standard fist" tested falls outside the training data distribution, leading to misjudgment.
2. **Taxonomy Design Flaws**:
   Only two rigid categories ("fully thumb-up" and "fully fist") were defined, with no intermediate category for transition postures. The model is forced to arbitrarily assign ambiguous inputs to one of the two existing categories, resulting in unstable predictions.
3. **Feature Recognition Limitations**:
   The model likely relies on a single dominant feature—"whether the thumb is extended" (thumb-up = 1 extended finger; fist = 0 extended fingers)—rather than nuanced hand geometry. In the misclassification case, the curled thumb in the standard fist was incorrectly identified as "extended," leading to a false `thumb_up` prediction. Humans can easily distinguish between "a curled thumb in a fist" and "an extended thumb in a thumb-up," but the model fails to capture this subtle yet meaningful distinction.