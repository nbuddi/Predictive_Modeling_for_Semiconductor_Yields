**Title:** Predictive Modeling for Semiconductor Manufacturing Yield

**Author:** Nikhil Buddi

**Executive Summary**
- This project aims to reduce manufacturing waste in semiconductor fabrication by predicting wafer failure early in the production cycle. Using the SECOM dataset (1,567 wafers, 591 sensors), I performed extensive data cleaning, handled extreme class imbalance, and developed a predictive model. Preliminary findings indicate that a small subset of sensors carries the majority of predictive weight for identifying "Fail" status.

**Rationale**
- Semiconductor fabrication is a high-cost, high-stakes environment. Processing a defective wafer through the entire line costs significant time and material resources. By implementing a predictive early warning system, manufacturers can scrap defective units immediately, saving downstream costs and providing engineers with data-driven insights to fix tool-level issues faster.

**Research Question**
- Can in-process sensor data collected from a semiconductor fabrication line be used to accurately predict the final pass/fail yield status of a wafer early in the manufacturing process?

**Data Sources**
- The project utilizes the SECOM dataset from the UCI Machine Learning Repository.
- **Instances:** 1,567 wafers.
- **Features:** 591 continuous variables representing sensor readings.
- **Target:** Binary label (-1 for Pass, 1 for Fail).
- **Characteristics:** Significant missing values and a 14:1 class imbalance.

**Methodology**
- **Data Engineering:** Automated ingestion via ucimlrepo API with fallback protocols.
- **Signal Auditing:** Filtered non-informative features using Variance Thresholding and implemented KNN Imputation (k=5) to recover missing signals.
- **Manifold Learning:** Applied Principal Component Analysis (PCA) to condense the active sensors into a 2D latent space for visualization.
- **Resampling Strategy:** Employed SMOTE-Tomek hybrid sampling to synthesize minority failure cases and remove borderline noise.
- **Modeling:** Trained a Logistic Regression classifier optimized for high-dimensional convergence using max_iter=2000.
- **Advanced Tuning:** Transitioned to Random Forest ensembles and performed Threshold Optimization to balance the costs of missed defects versus false alarms.

**Results**
- **Baseline Performance:** The model achieved a separation of classes in the resampled space, with performance metrics captured via a Confusion Matrix and ROC Curve analysis.
- **Threshold Optimization:** Successfully shifted the decision threshold to prioritize Recall, ensuring that the model captures a higher percentage of actual defects at the cost of manageable false alarms.
- **Key Findings:** Identified that yield failure is driven by multivariate "drift" across specific sensor groups.
- **Top Predictors:** Isolated the 15 most critical sensors, with Sensors 210, 214, & 565, showing the highest predictive power.

**Next Steps**
- **Financial ROI Modeling:** Quantify the dollar-amount savings per wafer caught early. (out of scope for this dataset)
- **Real-time Integration:** Integrate the model into the Manufacturing Execution System (MES) for live automated scrap decisions as a "Quality Gate".

**Outline of Project**
- '1_Signal_Audit_and_Recovery.ipynb'
- '2_Advanced_EDA_and_Manifold_Learning.ipynb'
- '3_Model_Architecture_and_Evaluation.ipynb'
- '4_Feature_Selection_and_Root_Cause.ipynb'
- '5_Advanced_Modeling_and_Tuning.ipynb'

**Contact Email:** 'nikhil.buddi@yahoo.com'
