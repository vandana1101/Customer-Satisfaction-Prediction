# Customer-Satisfaction-Prediction

This project explores customer support ticket data to identify key trends and improve satisfaction prediction using machine learning.  

### **Exploratory Data Analysis (EDA):**  
- **Ticket Trends:** The frequency of customer support tickets is analyzed over time to identify patterns in issue reporting.  
- **Common Customer Issues:** A bar chart highlights the most frequently reported issues, providing insights into recurring customer concerns.  
- **Ticket Type and Satisfaction:** Grouped bar plots illustrate the distribution of ticket types and their corresponding satisfaction ratings.  
- **Customer Demographics:**  
  - **Age Distribution:** A histogram visualizes the spread of customer ages.  
  - **Gender Distribution:** A pie chart shows the proportion of male, female, and other customers.  
- **Ticket Channels:** The preferred communication channels for ticket submission are analyzed.  
- **Product Purchases:** The most frequently purchased products are identified, categorized by gender for deeper insights.  
- **Ticket Priorities & Age Group Analysis:** Visualization of ticket urgency levels and how different age groups engage with support services.  

### **Predictive Modeling:**  
- **Preprocessing:**  
  - Categorical variables were encoded using label encoding.  
  - Missing values were dropped to ensure data consistency.  
  - Features were standardized for better model performance.  
- **Model Training:**  
  - A **Random Forest Classifier** was trained to predict **Customer Satisfaction Rating** based on features like response time, resolution time, and ticket type.  
- **Evaluation Metrics:**  
  - **Accuracy Score:** Evaluates the model’s overall performance.  
  - **Classification Report:** Provides precision, recall, and F1-score for each rating category.  
  - **Confusion Matrix:** Visualizes correct vs. incorrect predictions.  
- **Feature Importance Analysis:**  
  - The most influential features in predicting satisfaction are highlighted in a bar chart, showcasing key factors affecting customer experiences.  

This project combines exploratory insights with machine learning to improve customer service efficiency and satisfaction.
