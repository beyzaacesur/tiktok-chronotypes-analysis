# tiktok-chronotypes-analysis
DSA 210 - Beyza Cesur


## Project Overview

This project investigates the hourly patterns of my personal TikTok usage to understand how my digital behavior aligns with my daily attention rhythms. By analyzing my TikTok usage history over several months, I aim to determine whether my usage patterns reflect a **morning chronotype**, a **night owl chronotype**, or a **mixed pattern**.

Recent research shows that chronotype is strongly linked to mental health and daily functioning. Individuals with an evening chronotype have greater difficulty adapting to daytime schedules and are more likely to experience sleep problems, anxiety, depressive symptoms, and emotional fatigue. Because modern life is structured around morning oriented routines, evening types often experience chronic tiredness and “social jetlag” which can reduce cognitive efficiency. Since late night screen use reinforces evening chronotype tendencies, analyzing my TikTok usage patterns provides insight into whether my digital habits are supporting or disrupting my overall well being.

In this project, I examine:

- What time of day I use TikTok the most
- Whether usage differs on weekdays vs weekends
- Whether consistent daily “scroll loops” exist
- Whether my behavior aligns with morning-type or night-type chronotype tendencies


## Motivation
Social media usage is often subconscious and habit driven. TikTok in particular encourages passive scrolling and can significantly affect:
- Sleep patterns
- Mood and stress
- Time management and productivity

Understanding when I tend to open TikTok helps reveal:
- Behavioral triggers (boredom, nighttime relaxation, procrastination)
- Whether I unintentionally reinforce late night screen cycles
- Opportunities for digital self regulation and healthier routine formation


## Data Sources

Data Extraction Workflow

1-) I accessed https://privacy.apple.com and submitted a request to download my personal device analytics data.

2-) After Apple processed the request, I downloaded the data export ZIP file provided.

3-) From the extracted contents, I navigated to the Analytics Logs folder, which stores timestamped application usage records.

4-) I isolated entries corresponding to TikTok by filtering for its application bundle identifier

5-) I parsed and transformed the analytics logs into a structured dataset containing the following fields: Date, Hour of the Day, Total Minutes of TikTok Usage During That Hour, Day Type (Weekday vs Weekend)


## Data Collection Period

Data Source: iOS Device Analytics Usage Logs (Apple Data Privacy Export)   
Observation Period: Approximately August 2024 – January 2025 ( ~6 months )   
Data Resolution: Hourly TikTok screen time usage events   
Location / Context: Personal device usage in daily life environments     

## Research Questions:

Chronotype Behavior: 
Does my TikTok usage peak during late night hours, indicating a night owl chronotype?

Weekday vs Weekend Usage: 
Is there a significant difference in TikTok usage patterns between weekdays and weekends?

Habitual Cycle Detection: 
Are there recurring daily “scroll windows” where usage consistently spikes across days?

Attention Rhythm Stability: 
Do these usage rhythms remain stable over months, or do they shift during exam periods, stress, or schedule changes?

## Hypotheses
1. Chronotype Hypothesis

 **Null Hypothesis (H₀):**
 TikTok usage is evenly distributed throughout the day, with no specific high-usage hours.

 **Alternative Hypothesis (H₁):**
 TikTok usage significantly peaks during late evening and night hours, indicating a night owl chronotype.

2. Weekday vs Weekend Usage Hypothesis

 **Null Hypothesis (H₀):**
 There is no significant difference between weekday and weekend TikTok usage levels.
 
 **Alternative Hypothesis (H₁):**
 Weekend TikTok usage patterns differ significantly from weekday patterns (e.g., earlier start, longer duration).

3. Habit Formation Hypothesis 

 **Null Hypothesis (H₀):**
 TikTok usage does not exhibit repeated, time linked behavioral cycles.

 **Alternative Hypothesis (H₁):**
 TikTok usage forms habitual “scroll loops”, consistently occurring at similar hours each day.

## Data Analysis

| Stage | Description | Tools |
|------|-------------|------|
| Data Cleaning | Parsed analytics logs and extracted timestamps | Python, pandas |
| Feature Engineering | Computed hourly usage + weekday/weekend grouping | pandas, datetime |
| Visualization | Created usage patterns and heatmaps | matplotlib, seaborn |
| Behavioral Interpretation | Identified peak usage and repeated behavior cycles | Statistical reasoning |

### Planned Visualizations:
- **Line Plot**: TikTok usage by hour of day
- **Heatmap**: Hour × Weekday vs Weekend usage intensity
- **Distribution Plot**: Concentration of evening vs morning usage


## Findings

Preliminary expected results:
- TikTok usage likely peaks during the late evening or night hours, suggesting a night owl chronotype pattern.
- Usage on weekdays may increase after academic or daily obligations, indicating stress relief or decompression behavior.
- On weekends, usage may start earlier in the day and last longer that reflects schedule flexibility.
- The heatmap may reveal recurring daily usage windows (example: 22:00–01:00), which would indicate habit loops rather than spontaneous usage.
- If strong evening usage patterns are confirmed, this would align with literature showing delayed melatonin rhythm, social jetlag effects, and emotional regulation patterns commonly seen in evening chronotypes.


## Limitations and Future Work

 Limitation:

- Data reflects foreground app time, not content type 
- Chronotype inference is behavioral, not clinically validated 
- Only TikTok analyzed 
- No causal interpretation 

 Future Improvement:
 
- Incorporate TikTok scroll depth or category models in next iteration 
- Run formal MEQ to compare 
- Expand study to include **Instagram Reels** and **YouTube Shorts** 
- Introduce controlled screen time reduction experiments 
