# tiktok-chronotypes-analysis
DSA 210 - Beyza Cesur



## Table of Contents
1. [Project Overview](#project-overview)
2. [Objectives](#objectives)
3. [Motivation](#motivation)
4. [Data Collection & Sources](#data-collection--sources)
   - [Primary Data Source](#primary-data-source)
   - [Additional Context Variables](#additional-context-variables)
5. [Research Questions](#research-questions)
6. [Tools & Libraries Used](#tools--libraries-used)
7. [Data Analysis Process](#data-analysis-process)
8. [Visualizations](#visualizations)
9. [Key Findings](#key-findings)
10. [Limitations & Future Work](#limitations--future-work)
11. [Example Data Structure](#example-data-structure)



## Project Overview
This project investigates the hourly patterns of my personal TikTok usage to understand how my digital behavior aligns with daily attention rhythms. By analyzing the timestamps of TikTok videos I watched over several months, I aim to determine whether my usage patterns reflect a morning chronotype, a night owl chronotype, or a mixed pattern.  

This project focuses on my **personal TikTok browsing history**.  
By analyzing the **timestamps** of every video I watched, I investigate:

- What time of day I use TikTok the most
- Whether usage differs on weekdays vs weekends
- Whether consistent daily routines (or “scroll loops”) exist
- Whether my behavior aligns with **morningn type** or **night type** chronotype tendencies



## Objectives
- Extract and structure timestamp based usage data from TikTok
- Measure usage frequency by hour of day
- Compare weekday and weekend consumption patterns
- Identify habitual scrolling windows
- Interpret patterns in terms of chronotype behavior
- Visualize findings clearly through temporal charts and heatmaps



## Motivation
Social media usage is often subconscious and habit driven. TikTok in particular encourages passive scrolling and can significantly affect:
- Sleep patterns
- Mood and stress
- Time management and productivity

Understanding when I tend to open TikTok helps reveal:
- Behavioral triggers (boredom, nighttime relaxation, procrastination)
- Whether I unintentionally reinforce late night screen cycles
- Opportunities for digital self regulation and healthier routine formation


## Data Collection Period

Data Source

The dataset used in this project consists of my personal TikTok usage records, retrieved through the Apple Data & Privacy Export system. Since TikTok’s own export did not provide full watch history timestamps, I obtained long-term usage data from iOS Device Analytics Logs, which store application usage events at the system level.

1-) I visited https://privacy.apple.com and requested a copy of my personal device analytics data. 
2-) Once prepared by Apple, I downloaded the data export ZIP file. 
3-) Inside the exported files, I located the Analytics Logs, which include timestamped app usage sessions. 
4-) I filtered the logs for TikTok’s application identifier. 
5-) I converted the analytics logs into a structured table containing: Date, Hout of the day, Total minutes of TikTok usage during that hour, Weekday vs Weekend label

