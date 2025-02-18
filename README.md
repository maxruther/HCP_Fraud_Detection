# Healthcare Provider Fraud Detection

## Overview

I observe myriad recommendations from consulted literature to build an optimally precise classifier of healthcare providers' potential fraudulence. The datasets come from a Kaggle post, and its labels resemble one of the few publicly available sources of labelled provider fraud data, the List of Excluded Individuals/Entities (LEIE).

Please see [**my analysis**](HCPF_Full_Notebook.ipynb) in a Google Colab notebook.

## Techniques from the Literature

The recommendations I attempt to implement from the literature, on approaching fraud detection in a healthcare claim context, include the following:
- **Feature engineering to aggregate** claim and patient data to the provider level.
- **Correlation-based feature selection** to interpret variable importances and drastically reduce training times.
- **Alleviating class imbalance** to a 75-25 ratio.
- **Classifying with ensemble learning methods**, which were described as particularly effective on small samples, as well as those with rebalanced class ratios.


## Findings

Ultimately, I found these recommendations to be beneficial, overall. Below I briefly comment with my findings for each:

| Recommended Technique | My Assessment thereof in this Application |
|---|---|
| **Feature engineering to aggregate to the provider level** | **So critically necessary** for my application that it is difficult to conceive of a comparable alternative, and thus assess further. |
| **Correlation-based feature selection** | **Indeed beneficial** in interpreting variable importances and drastically reducing training times. Only slightly costed the models' precision scores, usually. |
| **Alleviating class imbalance** | **Indeed beneficial**, as models trained on samples so adjusted were nearly always more precise than their counterparts.
| **Classifying with ensemble learning methods** | Mixed findings on this point. The best models did come from two ensemble learning methods. But the two non-ensemble methods, Naive Bayes and SVM, hit higher heights than Gradient Boosting (an ensemble method.) Also counter to the notion of ensemble advantageousness was a Naive Bayes model handily outperforming the others on the more class-imbalanced datasets. |




<!--
Models trained on samples that had their class imbalance alleviated to a 75-25 ratio usually did better than those that remained more asymmetric. Correlation-based feature selection seemed effective in identifying the most important variables. CFS also was effective at reducing training times, while only slightly costing precision.

More complicated might be the findings on the first and last recommendations listed above. In my case, to form a dataset for the classification of providers, it was difficult to imagine an alternative to the recommendation: aggregating the claim data to the provider level. It is conceivable to instead train a classifier on the initially claim-level dataset, but it is too absurd to produce an interesting comparison.

My efforts yield a classifier that scores a precision of `0.864` in testing. Following this testing, I assess the effectiveness of the literature-recommended techniques in my experiment.

Using datasets on beneficiaries, inpatient claims, outpatient claims, and labels of potentially fraud providers, Using datasets pertaining to healthcare provider claim fraud from a Kaggle post, I set out to train an optimally precise classifier of potentially fraudulent healthcare providers.
-->
