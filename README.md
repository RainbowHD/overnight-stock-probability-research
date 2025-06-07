# Overnight stock probability research

## Project Overview
This research was driven by a desire to enhance understanding of market behavior through patterns observed during intraday trading. To reach a usable outcome, raw data had to be merged, cleaned, and reshaped multiple times until it became a clean, structured OHLCV dataset. This format made it possible to manipulate the data effectively and extract meaningful insights to support deeper market analysis.

## Workflow Summary
1. **Merge datasets** into one unified source.
2. **Convert timestamps** to UTC-4 (Eastern Time).
3. **Clean the DataFrame** by removing duplicate time rows and handling contract rollovers.
4. **Define the overnight (OVN) session.**
5. **Merge RTH and OVN data** into a consolidated dataset.
6. **Calculate breaches** of overnight session levels.
7. **Visualize insights** using pie charts, bar charts, and box plots for NQ and ES.

## Research Objective
  - Determine the distribution of Overnight High/Low level breaches during the RTH session, as well as the time- and frequency-based distribution for ES and NQ futures.
  - Assess the probability of breaking the Overnight High/Low levels during RTH depending on the gap size. 

#### Study Periods:
  - Last 5 years: March 3, 2020 – February 28, 2025
  - Last 15 years: June 6, 2010 – February 28, 2025

## Calculation of Overnight High and Overnight Low

  - Overnight High: the highest price reached between 4:00 PM and 9:29 AM New York time.
  - Overnight Low: the lowest price reached between 4:00 PM and 9:29 AM New York time.

## Mechanics of Level Breaches

  - If a 1-minute candle close > Overnight High → “High broken”*
  - If a 1-minute candle close < Overnight Low → “Low broken”*
  - If a 1-minute candle close > Overnight High and < Overnight Low → “High & Low broken”*
  - If no breach occurs → “None broken”
    
*Important note: if the session open occurs above (below) the Overnight High (Low), that is counted as a breach at 9:30 AM.

Data source: [www.databento.com](https://www.databento.com)

## Here are some images from the presentation that represent the distribution of NASDAQ: 

![Project screenshot](src/img/Picture%201.png)

This is a boxplot, which quickly shows the distribution and central tendency. The colored box spans from Q1 to Q3 (the interquartile range),
containing 50% of all RTH-session occurrences. The area from the minimum up to Q1 covers 25% of cases, and from Q3 up to the maximum
covers the remaining 25%.
<br>From this, we can conclude that 75% of occurrences happen between 9:30 and 10:38. Any points beyond the “whiskers” are called “outliers”
and represent rare events.</br>

![Project screenshot](src/img/Picture%202.png)
The bar plot shows the distribution of “OVN Low” breaches, with each bar representing one minute on the x-axis. Seventy-five percent of all breaches occur between 9:30 and 10:38. The y-axis shows the number of breaches, grouped by minute, and the x-axis tick interval is set to 5 minutes.

![Project screenshot](src/img/Picture%203.png)
The bar plot shows the distribution of “OVN High” breaches, with each bar representing one minute on the x-axis. Seventy-five percent of all breaches occur between the session open at 9:30 and 10:28. The y-axis indicates the number of breaches, with the data grouped by minute. The x-axis has a tick interval of 5 minutes.

![Project screenshot](src/img/Picture%204.png)
![Project screenshot](src/img/Picture%205.png)

![Project screenshot](src/img/Picture%206.png)
The bar plot shows the distribution of second-touch events from the OVN High & Low sample.

![Project screenshot](src/img/Picture%207.png)


<div style="display: flex;">
  <div style="flex: 1; padding-right: 1em;">
    Date: 2010-06-07 - 2025-02-28

    Observations: 3817
    Broken days: 3540
    Not broken: 277
    OVN High broken: 1482
    OVN Low broken: 1219
    High & Low broken: 839
  </div>
  <div style="flex: 1;">
    Date: 2020-03-03 - 2025-02-28

    Observations: 1298
    Broken days: 1201
    Not broken: 97
    OVN High broken: 512
    OVN Low broken: 417
    High & Low broken: 272
  </div>
</div>