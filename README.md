# Healthcare Provider Fraud Detection

![]()

<p align="center" width="100%">
  <img src="/visualizations/stock_image--healthcare_fraud.jpg" width="30%">
</p>
<br></br>

## Overview

I observe myriad recommendations from consulted literature to build an optimally precise classifier of healthcare providers' potential fraudulence. The datasets come from a Kaggle post, and its labels resemble one of the few publicly available sources of labelled provider fraud data, the List of Excluded Individuals/Entities (LEIE).

Please see [**my full analysis**](HPFD_Full_Analysis.ipynb) in a Google Colab notebook.

If the notebook of my full analysis is too large, please see these segments into which I've broken it up:
1. [Setup](analysis_in_segments/HPFD_1_Setup.ipynb)
2. [Integration I](analysis_in_segments/HPFD_2_Integration1.ipynb)
3. [Feature Engineering](analysis_in_segments/HPFD_3_FeatureEngineering.ipynb)
4. [Integration II](analysis_in_segments/HPFD_4_Integration2.ipynb)
5. [EDA](analysis_in_segments/HPFD_5_EDA.ipynb)
6. [Sampling](analysis_in_segments/HPFD_6_Sampling.ipynb)
7. [Modelling](analysis_in_segments/HPFD_7_Modelling.ipynb)

<br>

The highlights of this work might relate to the following topics, and reside in the corresponding notebooks:

| Topic of Highlight | Resident Notebook(s) |
| --- | --- |
| data integration and feature engineering | [Integration I](analysis_in_segments/HPFD_2_Integration1.ipynb), [Feature Engineering](analysis_in_segments/HPFD_3_FeatureEngineering.ipynb), [Integration II](analysis_in_segments/HPFD_4_Integration2.ipynb) |
| exploratory visualization | [EDA](analysis_in_segments/HPFD_5_EDA.ipynb) |
| correlation-based feature selection | [EDA](analysis_in_segments/HPFD_5_EDA.ipynb) |
| resampling to mitigate class imbalance | [Sampling](analysis_in_segments/HPFD_6_Sampling.ipynb) |
| hypertuning, testing, and logging numerous models through automated means | [Modelling](analysis_in_segments/HPFD_7_Modelling.ipynb) |

<br></br>

## Recommendations from the Literature

The recommendations I implement from the consulted literature, which mostly concerns approaches to fraud detection in healthcare claim data, include the following:
- **Feature engineering to aggregate** claim and patient data to the provider level. \[1\]
- **Correlation-based feature selection** to interpret variable importances and drastically reduce training times. \[2\]
- **Alleviating class imbalance** to a 75-25 ratio. \[3\]
- **Classifying with ensemble learning methods**, which were described as particularly effective on small samples, as well as those with rebalanced class ratios. \[3\]

#### Bibliography

1. Kumaraswamy, Nishamathi, et al. "Healthcare fraud data mining methods: A look back and look ahead." _Perspectives in health information management_ 19.1 (2022).

2. Bolón-Canedo, Verónica, et al. "A review of microarray datasets and applied feature selection methods." _Information sciences_ 282 (2014): 111-135.

3. Herland, Matthew, Richard A. Bauder, and Taghi M. Khoshgoftaar. "Approaches for identifying US medicare fraud in provider claims data." _Health care management science_ 23 (2020): 2-19.

<br></br>

## Findings

### Assessing the Recommended Techniques

Ultimately, I found these recommendations to be beneficial, overall. Below I briefly comment with my findings for each:

| Recommended Technique | My Assessment thereof in this Application |
|---|---|
| **Feature engineering to aggregate to the provider level** | **So plainly necessary** for my application that I cannot consider it as a recommendation taken. |
| **Correlation-based feature selection** | **Beneficial** in interpreting variable importances and drastically reducing training times. Only slightly costed the models' precision scores, usually. |
| **Alleviating class imbalance** | **Beneficial**, as models trained on samples so adjusted were nearly always more precise than their counterparts.
| **Classifying with ensemble learning methods** | **Mixed findings** on this point. The best models did come from two ensemble learning methods. But the two non-ensemble methods, Naive Bayes and SVM, hit higher heights than Gradient Boosting (an ensemble method.) Also counter to the notion of ensemble advantageousness was a Naive Bayes model handily outperforming the others on the more class-imbalanced datasets. |

<br></br>

### Optimal Classifier of Potentially Fraudulent Providers

The optimally precise classifier came from using Ada Boosting on the rebalanced, CFS-reduced sample. It scored a precision of `0.864`.

<br></br>
![test](/visualizations/model_comparison_test.png)




<!--
--- SAVED WRITING / SCRATCH ---

it is difficult to conceive of a comparable alternative, and thus assess further.


Models trained on samples that had their class imbalance alleviated to a 75-25 ratio usually did better than those that remained more asymmetric. Correlation-based feature selection seemed effective in identifying the most important variables. CFS also was effective at reducing training times, while only slightly costing precision.

More complicated might be the findings on the first and last recommendations listed above. In my case, to form a dataset for the classification of providers, it was difficult to imagine an alternative to the recommendation: aggregating the claim data to the provider level. It is conceivable to instead train a classifier on the initially claim-level dataset, but it is too absurd to produce an interesting comparison.

My efforts yield a classifier that scores a precision of `0.864` in testing. Following this testing, I assess the effectiveness of the literature-recommended techniques in my experiment.

Using datasets on beneficiaries, inpatient claims, outpatient claims, and labels of potentially fraud providers, Using datasets pertaining to healthcare provider claim fraud from a Kaggle post, I set out to train an optimally precise classifier of potentially fraudulent healthcare providers.
-->
