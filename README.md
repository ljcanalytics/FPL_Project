
# ⚽ Fantasy Premier League Report Project

![Power BI](https://img.shields.io/badge/Power%20BI-d9b300)
![Excel](https://img.shields.io/badge/Excel-brightgreen)
![GW Refresh](https://img.shields.io/badge/Latest%20GW%20Refresh-7-brightgreen)

[![RedditShare](https://img.shields.io/badge/share-FF4500?logo=reddit&logoColor=white)](https://www.reddit.com/submit?title=Check%20out%20this%20project%20on%20GitHub:%20https://github.com/ljcanalytics/FPL_Project)
[![LinkedInShare](https://img.shields.io/badge/share-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/sharing/share-offsite/?url=https://github.com/ljcanalytics/FPL_Project)

❗💥 [Access to the report](https://app.powerbi.com/view?r=eyJrIjoiNWViMDY2N2YtZTIyOC00YjhmLWEzOWMtNDZmNmM1NDNmMmVkIiwidCI6ImYxOTdmMGRkLTUyMDQtNDg2My1iZjEzLTk0MzE2M2ViMWU1NSJ9)

## Table of Contents
  - [About](#-about)
  - [Datasets](#datasets)
  - [Report Preview](#report-preview)
  - [Contacts](#contacts)
  
## 📜 About
This is a Power BI report designed to provide users with data from various sources to make strategic decisions to maximise points in the Fantasy Premier League game.
I built this tool for the following reasons.

1. Easy to refresh report that, in my opinion, provides unique data points that are not provided by the Fantasy Premier League website.
2. Showcase my Power BI report building & my ETL skills in one accessible area.

## Datasets

|Dataset|Source|
|:-|:-|
|Fixtures|Fantasy Premier League API|
|Merged_Gw_24_25|Web link (Github)|
|Understat|Manual Excel Sheet|
|Team Badges|Manual Excel SHeet with links to web|

## Report Preview

### Summary Page

Top-level overview of the current Premier League table. Includes expected goals data from [Understat](https://understat.com/league/EPL). Identify which are the best-performing teams based on league ranking & can compare actuals against expected data to evaluate a team's performance.

The ranking is based on the below script, which uses a hierarchy based on points, goal difference then goals scored. I.e if points are the same, goal difference is used to determine rank.  

```dax
League Rank = 
RANKX(ALL(Premier_League_table),
    RANKX(ALL(Premier_League_table), 
        RANKX (ALL(Premier_League_table), Premier_League_table[Points])
            + DIVIDE( 
                RANKX(ALL(Premier_League_table), Premier_League_table[Goal Difference]), 
                (COUNTROWS(ALL(Premier_League_table)) + 1)
            )
    , , ASC) +
    + DIVIDE( 
            RANKX(ALL(Premier_League_table), Premier_League_table[Goals Scored], , DESC), 
            (COUNTROWS(ALL(Premier_League_table)) + 1)
    )
, , ASC)
```

https://github.com/user-attachments/assets/952206ad-1165-4962-9228-d73c5dd1b75d

### Fixture Targeting

Use various different measures to identify the strength of a team's future fixtures in a GW. The user can draw their own conclusions from the data and target specific teams based on a variable number of gameweeks.

https://github.com/user-attachments/assets/77523dcd-bde3-4739-a979-eb19ff039171

### Player Performance

This data is provided by [vaastav](https://github.com/vaastav/Fantasy-Premier-League/tree/master) Once you have identified the teams you want to target, you can use this page to determine which players are within budget and are the best performers based on goals, assists, expected goals, etc.    

https://github.com/user-attachments/assets/d254657c-792e-4518-bcbf-5fd96eaa8df3

## Contacts

If you have any questions or feedback regarding the report. Don't hesitate to get in touch with me using the below.
- Email:ljcanalytics@protonmail.com
