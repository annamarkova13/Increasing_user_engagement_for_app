# Enhancing User Engagement in the 'Unnecessary Things' Mobile Application: An Exploratory Data Analysis of User Behavior and Conversion Patterns


## **Project Overview**

### **Project Introduction**  
In this project, I conducted a detailed exploratory data analysis for the mobile application "Unnecessary Things", focusing on the period from October 7, 2019, to November 3, 2019. The primary objective was to increase user engagement within the app by analyzing user behavior and identifying patterns that lead to the target action of viewing seller contact information.

### **Overview**  
The analysis focused on exploring the relationship between the target event (viewing contacts) and other user actions within the app. The goal was to identify the key scenarios that drive users to perform the target action. Additionally, I calculated relative frequencies of various events across two groups of users—those who viewed contacts and those who did not—and tested hypotheses regarding user behavior.  

By examining user behavior, we identified specific actions and scenarios, such as interacting with recommended ads, viewing photos, and adding items to favorites, that significantly impacted the likelihood of users viewing contacts. The study also involved creating conversion funnels for the most common user actions and scenarios.

The ultimate aim was to provide recommendations for increasing user engagement, improving the recommendation system, and enhancing the visibility and appeal of listings, especially in the context of encouraging users to engage with seller contacts.

### **Tools Used:**  
- **Programming Languages**: Python
- **Libraries**: Pandas, NumPy, SciPy, Matplotlib & Seaborn, Statsmodels
- **Platform**: Google Colab

### **Data Analysis Methods Used:**  
1. **Exploratory Data Analysis (EDA)**: 
   - Data cleaning and preprocessing
   - Analyzing user actions and event sequences
   - Visualizing data distributions and user behavior patterns  
   
2. **Conversion Funnel Analysis**: 
   - Constructed conversion funnels based on user actions leading to the target event (viewing contacts)
   
3. **Hypothesis Testing**: 
   - Performed statistical hypothesis testing (e.g., z-tests) to compare conversion rates between different user groups (e.g., users who viewed contacts vs. users who did not)
   
4. **Relative Frequency Analysis**: 
   - Calculated the relative frequencies of different events (such as viewing contacts, adding to favorites, clicking on ads) for various groups of users

### **Tags:**  
- Exploratory Data Analysis (EDA)  
- Conversion Funnel Analysis  
- Hypothesis Testing  
- User Behavior Analysis  
- Python  
- Data Visualization  
- Statistical Analysis  
- Google Colab  
- Mobile App Data Analysis  
- User Engagement

## General Conclusions Based on Research Results and Recommendations

Based on the research, answers were obtained to the **key questions and tasks of the client** and **hypotheses were tested**:

- To conduct the analysis, we identified user sessions, setting the maximum time difference between adjacent events for a single user as 7.5 minutes (which corresponds to the upper whisker limit of Q3 + 1.5*IQR).
- As a result, we obtained 13,824 sessions.
- Of these, 1,323 sessions (or 9.6%) ended with a target event `contacts_show` or `contacts_call`.
- In total, within the identified sessions that ended with the target event, we were able to identify 191 scenarios.

### **1. Analysis of the Relationship Between the Target Event (Contact View) and Other User Actions**

By examining the chains of actions leading to the target event, we obtained the following results:
- Most scenarios consist of chains with no more than 4 events.
- The majority of scenarios consist of a single event — viewing contacts (35% of scenarios). This suggests that the case occurs when an ad is opened via a link, and the first action is viewing the contacts to contact the seller.
- Following that, there are composite scenarios consisting of 2 or more actions: 22% of sessions have the sequence `tips_show, contacts_show` — viewing a recommended ad and viewing contacts.
- In 12% of sessions, the sequence includes viewing contacts and making a call via the app (`contacts_show, contacts_call`).
- In 6% of sessions, there is the sequence `photos_show, contacts_show` — viewing photos and then viewing contacts.
- In 5% of sessions, the sequence is `search, contacts_show` — searching and viewing contacts.
- In 4% of sessions, there is the sequence `search, contacts_show, contacts_call` — searching, viewing contacts, and making a call via the app.

**User Action Chains Visualization** was created using a Sankey diagram, where the flow of user action sequences is clearly visible.
<img width="753" alt="Screenshot 2025-01-09 at 19 49 51" src="https://github.com/user-attachments/assets/553c3968-8d33-46aa-9e35-0d7c9dcb989c" />

In the next step, we analyzed the identified user behavior scenarios leading to the target action and **built conversion funnels for the selected scenarios by unique users**. In total, we considered four scenarios:
```
Scenario 1 - `tips_show -> contacts_show` conversion at step 18%
Scenario 2 - `contacts_show -> contacts_call` conversion at step 22%
Scenario 3 - `photos_show -> contacts_show` conversion at step 31%
Scenario 4 - `search -> contacts_show` conversion at step 23%
```
- Among users who view recommended ads, 18% have viewed the seller's contacts at least once.
- Among users who viewed contacts, 22% called via the app.  
- The best conversion results to the target action were seen among those who viewed photos; nearly a third of users who viewed photos also viewed the seller's contacts.  
- Of those who used search, 23% viewed contacts at least once.  
   
Also, in the context of the first research question, we **calculated the session duration with and without viewing contacts** and determined that **the difference between the means is statistically significant** at `alpha=0.05`:
- The average session duration with contact viewing = 8.5 minutes (median = 5.2 minutes).
- The average session duration without contact viewing = 6.6 minutes (median = 4.5 minutes).
- The difference in means is 2 minutes.  

### **2. Calculation of Relative Frequency (Proportion) of Events by Two Groups of Users:**  
```
Group 1: Users who viewed contacts
Group 2: Users who did NOT view contacts
```
- The calculation results show that in Group 1, where users viewed contacts, they less frequently saw recommended ads (11% fewer), did slightly fewer searches (2% less), opened ads' cards less frequently (4% less), opened the map less frequently (2% less), and watched photos slightly more (1% more).
- They added ads to favorites and clicked on recommended ads with the same frequency (2% and 1%, respectively).
- Across all events, both groups of users most frequently saw recommendations (47% and 58%), then viewed photos (14% and 13%).
- As expected, there were no call events from the app in the second group.
<img width="928" alt="Screenshot 2025-01-09 at 20 20 26" src="https://github.com/user-attachments/assets/cc3e9e6d-3753-4658-972c-6ab3b7b65020" />

### **3. Results of Hypothesis Testing:**  
- The conversion to contact view for two groups of users (one group performs the actions tips_show and tips_click, while the other performs only tips_show) is different. The conversion rate for the first group is 31%, and for the second group, it is 17%.  
  The statistical test showed that the differences in conversion values are statistically significant. This means that users who open recommended ads are more likely to view seller contacts.
- The conversion to contact view for two groups of users (one group added products to favorites, the other did not) is also different — 39% versus 11%, respectively. The statistical test showed that the difference is statistically significant. This means we can conclude that users who add products to their favorites are more likely to reach the contact view stage.

## **Recommendations:**
- Attention should be paid to the low number of clicks on recommended ads. It’s possible that irrelevant ads are being displayed, and it would be helpful to include attractive product alternatives, substitute products, or complementary products in the results.
- For more detailed analysis, additional event tracking should be implemented, such as the source from which the app was opened (from the main screen, via a link), and tracking of user movements between screens.
- Based on the results of the study, we determined that the conversion to a seller call is higher among users who have added the ad to their favorites. To increase the attractiveness of ads, it would be beneficial to create and publish recommendations for sellers on how to create more appealing ads.




