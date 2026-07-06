---
company: Department for Business and Trade
context: L&D slot, DBT Data Science forum
tags: [ml-technical-depth, mlops-deployment, upskilling-colleagues, communicating-and-influencing, developing-self-and-others]
---

## Technical skill - Data Science

Theoretical understanding of and expertise utilising data science techniques for a range of applications (e.g. natural language processing, classification, forecasting, regression).

I developed and delivered a technical workshop on classification methodology to upskill colleagues, presented during the L&D slot in DBT's Data Science forum. The objective was to demonstrate a comprehensive understanding of theoretical concepts across the entire machine learning lifecycle, from data preparation through to deployment and maintenance.

I designed the session around a case study on heart disease prediction from Kaggle. Following exploratory data analysis and data preparation, I implemented Random Forest, XGBoost, and Logistic Regression as a baseline. Using scikit-learn pipelines, I incorporated stratified train-test splits and standard scaling. I optimised hyperparameters through randomised search and evaluated models using nested cross-validation to avoid optimistic bias. Random Forest performed best on recall, which was the primary metric, since false negatives carry a higher risk in a medical context.

For interpretation, I applied SHAP values to assess feature importance, confirming that key cardiovascular metrics strongly influenced predictions. Critically, I extended beyond model development to cover deployment considerations, comparing API design approaches (FastAPI) and infrastructure trade-offs between ECS and SageMaker, and discussing the need for ongoing monitoring and retraining strategies.

I presented findings using visualisations, including correlation matrices, ROC curves, and confusion matrices, alongside workflow diagrams. The deployment discussion sparked a valuable conversation that crystallised an important insight: data scientists often focus heavily on model optimisation without considering how models will be used in practice. Real value depends on thoughtful deployment, continuous monitoring, and systematic retraining. I now ensure deployment and maintenance are always discussed from the start and are not treated as afterthoughts.
