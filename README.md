# NASA-HTTP Autoscaling Prediction
This repository contains the Python implementation of a predictive autoscaling model for Kubernetes based on the NASA-HTTP logs dataset. The model forecasts minute-by-minute request counts using machine learning techniques, with a primary focus on balancing accuracy and efficiency for real-time autoscaling in a Kubernetes environment.
## Dataset Overview
The dataset used in this project is the NASA-HTTP logs, which contain detailed HTTP requests from the Kennedy Space Center WWW server in July and August 1995. The dataset supports the development of a predictive model by providing high-resolution timestamps, allowing precise capture of temporal trends.
## Machine Learning Models
The primary objective was to predict the next minute’s request count using the previous 10-minute request counts. Several machine learning and deep learning models were evaluated:

### Deep Learning Models:
Informer
Autoformer
N-Beats
DeepAR
### Baseline Model:
Uses the previous minute's request count as the prediction.
### Linear Regression:
Selected for deployment due to its simplicity, efficiency, and explainability.
![image](https://github.com/user-attachments/assets/5553f941-63ae-4740-a6fa-542dbde53bfa)
## Key Findings:
- Linear Regression achieved comparable performance (MSE: 185.2) to the best-performing models (e.g., N-Beats: MSE: 185) with significantly reduced computational requirements.
- Prediction time for linear regression was just 0.0014 seconds per sample, making it well-suited for real-time deployment.
## Explainable Feature Relationships
The linear regression model offers interpretability:
Regression Coefficients: Highlighted the importance of recent request counts in predicting the next timestamp. For example:
T−1 (most recent request count) has the highest influence.
Influence diminishes for older request counts (T−10 to T−2).
This explainability makes linear regression reliable for understanding scaling decisions in autoscaling systems.
![image](https://github.com/user-attachments/assets/e4f32620-a58a-49ea-8d8e-453b224c51be)

## Residual Analysis
Positive Residuals (under-predictions): Observed during midday and on weekdays.
Negative Residuals (over-predictions): Common during night and on weekends.
These patterns suggest areas for model refinement, such as incorporating additional temporal features to better capture traffic fluctuations.
![image](https://github.com/user-attachments/assets/588f7c92-3b26-4726-a636-205a0e0dd5dd)


## Performance
The linear regression model effectively tracks the actual trend of HTTP requests over time, demonstrating its capability to capture temporal variations. However, future improvements are necessary to handle extreme peaks and troughs.
![image](https://github.com/user-attachments/assets/210b9af8-de6c-463b-a885-0bd8703a6fc0)
