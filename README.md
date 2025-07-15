This project aimed to **reduce losses from booking cancellations** by developing a **prediction model** to identify high-risk bookings. The goal was to allow the hotel to take early action to mitigate these cancellations. **This project was performed using KNIME Analytics Platform.** 
### **Our Approach**
*   **Data:** The model was developed using **20,000 past reservations**.
*   **Feature Selection Strategies:** Three main strategies were explored to select input variables:
    *   **Filter Method:** Used statistics like Spearman correlation for numerical data (e.g., Lead Time, Previous Cancellations, Booking Changes, ADR, Special Requests) and variety for categorical data. Variables with over 80% dominance in one category were excluded.
    *   **All Variables:** A baseline model using all available variables without filtering was tested for comparison.
    *   **Wrapper Method:** Utilized a genetic algorithm and Decision Tree to find optimal variable combinations, which takes longer to run but can discover hidden relationships.
*   **Data Processing:** Missing values were filled (most common for categories, median for numerical), outliers were adjusted with winsorization, and numerical values were scaled using Min-Max normalization.
*   **Models Tested:** Four common algorithms were tested for each feature set: **Logistic Regression, Decision Tree, Random Forest, and Gradient Boosted Learner**. These models range from easy-to-understand to more advanced ones that can capture complex patterns.
*   **Validation:** **10-fold cross-validation** was used to ensure consistent performance, splitting data into 10 parts and testing multiple times. A separate validation set confirmed the model's ability to generalize to new data, showing consistent results.
*   **Evaluation Metrics:** **Accuracy** (percentage of correct predictions) and **AUC (Area Under the ROC Curve)** were used to evaluate model performance. AUC is a score between 0 and 1 that shows how well the model distinguishes between cancellations and non-cancellations.

### **Key Findings**
*   The **Gradient Boosted Learner** consistently provided the best results across all scenarios for both Accuracy and AUC, making it the best choice overall.
*   The **best-performing model reached an accuracy of 86%**, reliably flagging high-risk bookings.
*   The combination of the **Filter Method and Gradient Boosted Learner** was selected as the final solution, showing strong results: **Accuracy = 0.8470, AUC = 0.92**.
*   **Optimal Action Threshold:** A threshold of **60% (0.6)** probability of cancellation was found to be the most financially sensible point to treat a booking as high risk, leading to the **lowest overall misclassification cost ($881,520.19)**.
    *   **Predicting a cancellation that doesn’t happen (false positive) costs about $633.27**.
    *   **Missing a real cancellation (false negative) costs $316.63**.

### **Solutions & Proposed Value**
*   **Integration:** The model can be **integrated into the hotel’s reservation system** to automatically estimate cancellation risk for each booking.
*   **Proactive Actions:** For high-risk bookings, hotel staff can:
    *   Send **reminders or special offers** to encourage guests to keep their bookings.
    *   **Adjust overbooking strategies** to avoid empty rooms.
*   **Benefits:** Using this model can lead to:
    *   Spotting likely cancellations early.
    *   Improved revenue and planning.
    *   **Reduction in losses due to last-minute cancellations**.
    *   **Increase in occupancy rates**.
    *   More stable and predictable income.

### **Recommendations for Long-Term Effectiveness**
To keep the model accurate and useful, the following are recommended:
*   **Regular Monitoring:** **Review the model’s performance every 3–6 months** by comparing predictions with actual cancellations. If accuracy or AUC drops, the model should be **retrained using the latest data**.
*   **Data Enhancement:** **Collect additional useful information** beyond basic booking data. Examples include a guest’s past booking or cancellation history, how they respond to reminders, or local event information.
*   **Model Exploration:** While the Gradient Boosted Learner performs well, **exploring other model types** (e.g., time-series models for trends) may provide new insights and further improve results, especially as the business environment changes.
*   **Thoughtful Actions:** Actions based on predictions (e.g., sending offers) should be carried out thoughtfully to avoid overwhelming guests.
*   **Data Protection:** Customer data must always be handled securely and responsibly, complying with privacy regulations.
