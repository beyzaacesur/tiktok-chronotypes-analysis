# tiktok-chronotypes-analysis
DSA 210 - Beyza Cesur


## **PROJECT OVERVIEW**

This project investigates the hourly patterns of my personal TikTok usage to understand how my digital behavior aligns with my daily attention rhythms. By analyzing my TikTok usage history over several months, I aim to determine whether my usage patterns reflect a **morning chronotype**, a **night owl chronotype**, or a **mixed pattern**.

Recent research shows that chronotype is strongly linked to mental health and daily functioning. Individuals with an evening chronotype have greater difficulty adapting to daytime schedules and are more likely to experience sleep problems, anxiety, depressive symptoms, and emotional fatigue. Because modern life is structured around morning oriented routines, evening types often experience chronic tiredness and “social jetlag” which can reduce cognitive efficiency. Since late night screen use reinforces evening chronotype tendencies, analyzing my TikTok usage patterns provides insight into whether my digital habits are supporting or disrupting my overall well being.

In this project, I examine:

- What time of day I use TikTok the most
- Whether usage differs on weekdays vs weekends
- Whether consistent daily “scroll loops” exist
- Whether my behavior aligns with morning-type or night-type chronotype tendencies



##  **MOTIVATION** 
Social media usage is often subconscious and habit driven. TikTok in particular encourages passive scrolling and can significantly affect:
- Sleep patterns
- Mood and stress
- Time management and productivity

Understanding when I tend to open TikTok helps reveal:
- Behavioral triggers (boredom, nighttime relaxation, procrastination)
- Whether I unintentionally reinforce late night screen cycles
- Opportunities for digital self regulation and healthier routine formation



# **DATA SOURCES AND EXTRACTION WORKFLOW**

## **1. Data Source**

The dataset used in this project was obtained directly from TikTok using its official **Download Your Data** feature.  
This approach complies with ethical data science practices, as it relies solely on personal data voluntarily requested and used strictly for academic purposes.

**Data Request Portal:**  
https://www.tiktok.com/setting/download-your-data  

## **2. Data Extraction Workflow**

1. TikTok’s official data request portal was accessed and a request was submitted to download personal account data in JSON format.  
2. After processing, TikTok provided the data export as a compressed (ZIP) archive.  
3. From the extracted contents, the following path was selected:  
   **Ads and Data → Off TikTok Activity**  
4. This section contains timestamped interaction logs, including events such as:
   - App launches  
   - Logins  
   - In-app interaction signals  
5. The raw JSON files were parsed using Python and converted into a structured tabular dataset.
6. From each event, the following attributes were derived:
   - Date  
   - Hour of day  
   - Day type (Weekday vs Weekend)  



# **DATA ANALYSIS**

## **1. Data Collection and Scope**

- **Data Source:** TikTok Off TikTok Activity logs (Personal Data Export)  
- **Observation Period:** September 2024 – December 2024  
- **Analysis Window:** Last three months of data  
- **Data Type:** Timestamped TikTok interaction events  
- **Context:** Real life personal smartphone usage behavior  


## **2. Data Preprocessing and Feature Engineering**

The raw JSON data is parsed and enriched with time-based features to enable temporal analysis:

- Conversion of timestamps to datetime format  
- Extraction of hour, date, and day of week  
- Classification of days as weekday or weekend  
- Filtering to retain only the most recent three months  

To analyze daily usage patterns, each day is divided into three standardized time periods:

- **Morning:** 05:00 – 12:59  
- **Afternoon:** 13:00 – 20:59  
- **Night:** 21:00 – 04:59  


## **3. Usage Metrics and Proxy Measures**

Because exact screen time is unavailable, usage intensity is approximated using:

- **Proxy minutes** based on event frequency  
- **Usage ratios**, calculated as the proportion of total daily activity occurring in each time period. Using ratios allows behavioral comparisons independent of total daily usage volume.  
Additionally, a **circular mean** is computed to estimate each day’s *center of activity hour*, ensuring accurate handling of time-of-day patterns across the 24-hour cycle.


## **4. Implemented Visualizations**

The following visualizations are implemented in the analysis notebook:

- **Line Plot:** Daily TikTok usage intensity (proxy minutes)  
- **Bar Chart:** Average usage by time period  
- **Bar Chart:** Average usage ratios by time period  
- **Time Series Plot:** Center of activity hour over time (mean ± standard deviation)  

These visualizations support both exploratory insights and hypothesis driven evaluation.


## **5. Research Questions**

- **Chronotype Behavior:**  
  Does TikTok usage concentrate during late-night hours?

- **Time-of-Day Preference:**  
  Is usage significantly different across morning, afternoon, and night periods?

- **Weekday vs Weekend Patterns:**  
  Does usage behavior differ between weekdays and weekends?

- **Habit Stability:**  
  Are daily usage rhythms consistent over time, or do they shift?


## **6. Hypothesis Testing**

### **6.1 Time Period Comparison (One-way ANOVA)**

- **H₀:** Usage ratios are equal across morning, afternoon, and night.  
- **H₁:** At least one time period has a significantly different usage ratio.

### **6.2 Morning vs Afternoon (Paired t-test)**

- **H₀:** Morning and afternoon usage ratios are equal.  
- **H₁:** A significant difference exists between morning and afternoon usage.

### **6.3 Morning vs Night (Paired t-test)**

- **H₀:** Morning and night usage ratios are equal.  
- **H₁:** Morning usage differs significantly from night usage.

### **6.4 Weekday vs Weekend (Independent t-test)**

- **H₀:** There is no difference between weekday and weekend usage.  
- **H₁:** Weekend usage differs significantly from weekday usage.


## **7. Data Analysis Pipeline Summary**

| Stage | Description | Tools |
|------|-----------|-------|
| Data Cleaning | Parsing JSON logs and extracting timestamps | Python, pandas |
| Feature Engineering | Time-based aggregation and categorization | pandas, datetime |
| Visualization | Temporal usage pattern analysis | matplotlib, seaborn |
| Statistical Testing | Validation of behavioral hypotheses | scipy.stats |
| Interpretation | Chronotype and habit analysis | Statistical reasoning |



# **FINDINGS**


## **1. Overall Usage Distribution**

Both exploratory visualizations and statistical tests indicate that TikTok usage is not evenly distributed throughout the day.  
The One way ANOVA results show a statistically significant difference between morning, afternoon, and night usage ratios (p < 0.05), confirming that time of day has a meaningful effect on usage behavior.


## **2. Time of Day Preference**

Bar charts based on proxy minutes and usage ratios reveal that afternoon usage accounts for the largest share of daily activity, followed closely by morning usage.  
In contrast, night usage consistently represents a much smaller proportion of overall engagement.


## **3. Chronotype Insights**

Paired t-test results show a statistically significant difference between morning and night usage ratios, while the difference between morning and afternoon usage is not statistically significant. These findings indicate that night usage is systematically lower than daytime usage, pointing to a day oriented rather than night oriented chronotype.

The center of activity hour analysis further supports this conclusion, as daily activity centers are clustered around daytime hours with no consistent shift toward late night behavior.


## **4. Weekday vs Weekend Behaviour**

The independent t test comparing weekday and weekend usage shows no statistically significant difference in overall TikTok usage intensity.  
This suggests that usage patterns remain relatively stable throughout the week, without notable increases during weekends.

## **MACHINE LEARNING ANALYSIS: K-MEANS CLUSTERING**

To further explore usage patterns without predefined labels, an unsupervised machine learning approach—**K-Means clustering**—was applied to the daily usage features.

### **Feature Set**
The following day-level features were used as input to the clustering model:
- `morning_ratio`: proportion of daily usage in morning hours  
- `afternoon_ratio`: proportion of daily usage in afternoon hours  
- `night_ratio`: proportion of daily usage in night hours  
- `center_of_activity_hour`: circular mean of activity timing

These features represent the relative distribution of usage and capture temporal preferences independently of total daily usage.

### **Model Selection**
The optimal number of clusters (`k`) was determined using:
- **Elbow method** (inertia): to evaluate cluster compactness  
- **Silhouette score**: to measure separation quality  

Based on these metrics and interpretability, a suitable `k` (e.g., 3) was selected.

### **Cluster Profiles**
After fitting the K-Means model, each day was assigned a cluster label.  
Cluster summaries reveal distinct behavioral patterns:

- **Cluster 0 – Morning-heavy usage:** Days with relatively higher usage in the morning period and earlier activity center hours.  
- **Cluster 1 – Afternoon-heavy usage:** Days with dominant afternoon usage and mid-day activity centers.  
- **Cluster 2 – Night-heavy usage:** Days characterized by a comparatively larger night usage ratio and later activity centers.

These patterns show that daily usage behavior does not form a single homogeneous group but rather can be grouped into recurring temporal profiles.

### **Visualization and Interpretation**
Cluster profiles were visualized using:
- **Bar charts of usage ratio means** for each cluster  
- **Scatter plots of center of activity vs. proxy usage intensity** colored by cluster  

Such visualizations support the interpretation that distinct daily usage habits exist, reflecting differences in chronotype and engagement rhythms. The analysis adds another dimension to the descriptive and statistical results, demonstrating that days naturally group into characteristic usage patterns without supervision.

### **Output Files**
The clustering results, including cluster labels and profile assignments for each date, were saved as:




# **LIMITATIONS AND FUTURE WORK**

## **LIMITATIONS**

- The dataset does not include actual screen time or watch duration. Usage intensity is estimated using event frequency and proxy minutes.
- Only TikTok *Off TikTok Activity* data is available, meaning passive in app browsing may not be fully captured.
- The analysis is based on a single user, so findings are not generalizable.
- Contextual factors such as sleep, stress levels, or academic workload are not included.


## **FUTURE WORK**

- Integrate true screen time data (e.g., iOS Screen Time) to improve usage estimation.
- Extend the dataset to multiple users for comparative analysis.
- Apply machine learning techniques such as clustering or time-series forecasting.
- Incorporate contextual variables (exam periods, sleep patterns) to better explain usage behavior.
- Use sequential models to detect habitual scrolling cycles.

# HOW TO RUN THE ANALYSIS

## 1. Clone the repository

```bash
git clone https://github.com/beyzaacesur/tiktok-chronotypes-analysis.git
cd tiktok-chronotypes-analysis



