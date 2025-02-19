# More Visualizations from the Analysis
Here are more visualizations at a glance, from my analysis of healthcare provider claim fraud data.

<br></br>


## EDA
### Violin Plots

Using violin plots to identify which predictors might distribute very differently between the two states of the target, _PotentialFraud_.
<br></br>

<p align="center" width="100%">
  <img src="/visualizations/violin_plots_claims.png" width="80%">
</p>
<br></br>

<p align="center" width="100%">
  <img src="/visualizations/violin_plots_chronConds_1.png" width="80%">
</p>
<br></br>

<p align="center" width="100%">
  <img src="/visualizations/violin_plots_chronConds_2.png" width="80%">
</p>
<br></br>

<p align="center" width="100%">
  <img src="/visualizations/violin_plots_ins_amts.png" width="80%">
</p>
<br></br>


### Correlation Analysis

To identify and visualize the intercorrelations of predictors above a certain threshold, I defined a method `get_high_corrs()`. These were it's outputs, at two points in the process of correlation-based feature selection.
<br></br>

<p align="center" width="100%">
  <img src="/visualizations/cfs_plot__first_round.png" width="80%">
</p>
<br></br>

<p align="center" width="100%">
  <img src="/visualizations/cfs_plot__second_round.png" width="80%">
</p>
<br></br>


### Addressing Class Imbalance through Resampling

Using simple pie charts to illustrate the class balance in the training samples, before and after oversampling from the minority class. 

The minority class represents the flagging of a provider as potentially fraudulent. The majority class represents a provider as unflagged for this. 
<br></br>

<p align="center" width="100%">
  <img src="/visualizations/initial_class_balance.png" width="50%">
</p>
<br></br>

<br></br>

<p align="center" width="100%">
  <img src="/visualizations/rebalanced_through_oversampling.png" width="50%">
</p>
<br></br>

