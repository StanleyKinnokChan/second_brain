# Predictive Analysis

**Alteryx predictive tools flowchart**

[https://community.alteryx.com/t5/Data-Science/Alteryx-Predictive-Tools-Flowchart/ba-p/602881](https://community.alteryx.com/t5/Data-Science/Alteryx-Predictive-Tools-Flowchart/ba-p/602881)

- Investigate and prepare data for analysis
• Identify suitable variables for predicting a target
variable
• Select predictor variables that fit given criteria
• Create training and validation datasets
• Select appropriate algorithms to model datasets
• Train models
• Compare models
• Interpret model reports
• Score new data with trained models
• Classification
• Regression
• Time series
• Optimization

Note:

- Arima/ETS can specify the starting period
- logistic regression tool must have only 2 values for target variables
- Optimization tool:
    - **Manual input:**
        - **objective:** function to minimize/ optimize
        - **constraint:** constraint of the function of variable
        - **Bound:** range of possible value of the variable
    - **O anchor** (listed vertically), [”variable”] [”coefficient”]
        - • The order of variables for input **O** and input **A** *must* be the same.
        - Display field mapping for input anchor to map the field
        - variable for the objective function (no inequality because we always want to optimize the coefficient)
    - **A anchor** (constraint matrix using the combination of variables from O anchor)
        - **Constraints in rows (preferred):** one row one constraint, [var1] [var..] [”dir”] [”rhs”]
        - **Variables in rows:** one row one var (need dir & rhs as input B) [’variable’] [factor]
    - **maximize Onjective?:** default to be minimize if this option is not ticked
