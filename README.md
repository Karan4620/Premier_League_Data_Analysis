# 🏟️ Premier League Match Data – Scraping & Analysis

This project scrapes and analyzes English Premier League (EPL) match data from [FBref](https://fbref.com/en/) for the most recent season. It is split into two main parts:

1. **Web Scraping using Selenium + BeautifulSoup**
2. **Data Cleaning & Exploratory Analysis with Pandas & Matplotlib**

---

## 📁 Project Structure

├── PL_Match_Data_Extraction.ipynb # Web scraping logic
├── PL_Data_Analysis.ipynb # Data cleaning & exploratory analysis
├── premier_league_match_info.csv # Scraped match metadata
├── team_div_summary_map.csv # Mapped team div IDs for scraping stats
├── pl_merged_stats.csv # Final cleaned player stats (input to analysis)
├── final_soccer_column_dictionary.csv # Column definitions and rename map


---

## 🕸️ 1. Match Data Scraping (FBref.com)

The `PL_Match_Data_Extraction.ipynb` notebook performs the following:

- Parses the EPL fixtures & results HTML file saved locally from FBref.
- Extracts:
  - Gameweek number
  - Match date
  - Home and Away teams
  - Match report URLs
- Uses **Selenium** to render dynamic content and extract internal stat section identifiers.
- Maps each team to their respective stat div IDs.
- Saves results to CSV for use in downstream analysis.

> ⚠️ Note: FBref dynamically loads content, so a headless Chrome browser is required.

---

## 📊 2. Player-Level Analysis

The `PL_Data_Analysis.ipynb` notebook does the following:

- Loads and renames columns using a dictionary (`final_soccer_column_dictionary.csv`)
- Filters out goalkeepers for outfield player analysis
- Performs key metrics and aggregations:
  - Top 10 goal scorers
  - Goal difference vs. expected goals (xG)
- Creates visualizations and SQL-style reports using `sqlite3`

---

## 🚀 How to Run

### 🔧 Requirements

Install the necessary packages:

```bash
pip install pandas beautifulsoup4 selenium matplotlib seaborn