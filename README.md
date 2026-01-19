# Occupational Injury Trends (OSHA Severe Injury Reports)

This project analyzes OSHA Severe Injury Reports to identify common injury mechanisms, frequently affected body parts, and how severe outcomes vary across event types. The notebook includes data cleaning, exploratory analysis, and a set of ethical, clearly labeled visualizations.

## Dataset
- **Dataset:** OSHA Severe Injury Reports (Severe Injury Data)
- **Time range used in this analysis:** Jan 2015 – Mar 2025
- **Local file included in this repo:** `data/January2015toMarch2025.csv`

## Repository Contents
- `notebooks/osha_severe_injury.ipynb` — full analysis notebook (code + charts + written interpretation)
- `data/January2015toMarch2025.csv` — dataset used for the analysis
- `requirements.txt` — Python dependencies used to run the notebook
- `README.md` — project overview and run instructions

## Questions Explored
- Which injury event mechanisms (`EventTitle`) appear most often in the dataset?
- Which body parts are most frequently involved in severe injury reports?
- Among the most common event types, how often do reports involve:
  - **Any amputation**
  - **Any hospitalization**

## Measures Used
Event mechanisms are analyzed using `EventTitle` (the human-readable label for OSHA’s OIICS-coded “Event or Exposure” field).

Outcome fields such as `Hospitalized` and `Amputation` are recorded as **counts** (usually 0/1, sometimes greater than 1).  
For rate calculations, outcomes are converted to report-level indicators:

- **Any_Amputation:** `Amputation > 0`
- **Any_Hospitalized:** `Hospitalized > 0`

Outcome “rates” are computed as the mean of these 0/1 indicators within each event type (interpretable as the share of reports involving that outcome).

## How to Run
1. Create and activate a virtual environment (Windows):
   ```bash
   python -m venv venv
   .\venv\Scripts\activate
````

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Open and run the notebook:

   * Open `notebooks/osha_severe_injury.ipynb`
   * Run all cells from top to bottom.

## Limitations and Ethics Notes

* The dataset reflects reported severe injuries and OSHA coding practices; it is not a complete picture of all workplace injuries.
* Results represent report volume and patterns within this dataset, not population-level risk rates (which would require employment denominators).
* Some categories are broad or “unspecified,” which can reduce precision.
* Visuals focus on the top event types for readability; less frequent categories are not emphasized in the main outcome comparisons.