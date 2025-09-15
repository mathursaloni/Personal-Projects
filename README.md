# GLP-1 RA Market Access in France, Germany, UK using Python, Excel & Tableau.

This portfolio project analyses **market access** for GLP-1 receptor agonists (Ozempic, Wegovy, Victoza, Trulicity) across **France, Germany, and the UK**.  
It combines **Excel** (for structured data), **Python in Colab** (for cleaning, analysis, and charting), and **Tableau** (for interactive dashboards).  

Why this matters: GLP-1 RAs are transforming diabetes and obesity care, but access depends heavily on **pricing, reimbursement, and affordability**.  
_This project highlights those differences in a clear, data-driven way._


## Project Objectives
- Compare monthly list prices of GLP-1 drugs across the 3 countries.  
- Summarise reimbursement status (Reimbursed, Conditional, Not reimbursed) and derive an access score.  
- Visualise affordability - drug cost as % of monthly GDP per capita.  
- Package analysis and insights in a consulting-style format for portfolio use.  

## Repository Structure
glp1-market-access-eu/
├── data/
│ ├── glp1_eu_market_access.xlsx
│ └── exports/ # CSVs from Colab for Tableau
├── notebooks/
│ └── glp1_market_access_colab.ipynb
├── tableau/
│ ├── dashboard_spec.md
│ └── screenshots/
├── docs/
│ └── insights_report_template.md
├── images/
│ ├── wegovy_prices.png
│ └── ozempic_affordability.png
└── README.md

## Workflow
1. **Excel**: Input data (prices, reimbursement, GDP).  
2. **Colab notebook**: Clean, analyse, export Tableau-ready CSVs.  
3. **Tableau**: Build dashboards (see `tableau/dashboard_spec.md`).  
4. **GitHub**: Store everything & showcase as portfolio.

 ### Dataset Year: 2025

## Dashboards
- Access Map/Matrix (access score by country & brand).  
- Price Comparison (bars) (monthly price by country).  
- Affordability Scatter (price % GDP vs income).  
- Reimbursement Heatmap (country × brand).  

### Key Insights-

- Wegovy price gap: Germany shows the highest monthly Wegovy price at €300, versus €250 in France; a spread of €50 per month.
- Access score (0=No, 1=Conditional, 2=Reimbursed): United Kingdom (1.60), France (1.40), Germany (1.40).
- Ozempic affordability: Price as % of monthly GDP per capita ranges from 2.0% (Germany) to 2.2% (United Kingdom).
- Average GLP-1 monthly price (across brands): Germany (€179), United Kingdom (€168), France (€154).
- Obesity-brand coverage mix (France): Reimbursed: 0%, Conditional: 100%, Not reimbursed: 0%.
- Obesity-brand coverage mix (Germany): Reimbursed: 0%, Conditional: 50%, Not reimbursed: 50%.
- Obesity-brand coverage mix (United Kingdom): Reimbursed: 0%, Conditional: 100%, Not reimbursed: 0%.

<img width="400" height="200" alt="Image" src="https://github.com/user-attachments/assets/ddf3827a-83ef-46c8-a6e6-de15523615d4" />
<img width="400" height="200" alt="Image" src="https://github.com/user-attachments/assets/7861107f-d639-4c62-804d-f2245f5391fb" />

## Deliverables
- Excel dataset  
- Python Colab notebook (with exports)  
- Charts (PNG)  
- Interactive Tableau dashboards  
- One-page insights report

## Next Steps
- Expand to Spain & Italy.  
- Swap in real-world reimbursement & HTA data.  
- Add regression to predict access scores.  
- Compare EU vs US affordability.  
