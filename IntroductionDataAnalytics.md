# Introduction to Data Analytics
Teacher: Gary Mercado
Source: Simplilearn
Some real-time use cases: Healthcare, Government, Education, E-commerce
## Overview
We will: explain how DA benefited accounting (1), its life cycle, types of DA and benefits

**Importance:** plays significant role in business operations and decision-making (multiple approaches, techniques and dimensions). *Remember:* data is
unpredictable but we can identify **trends, patterns, information**, so we can **increase profit, get better resource utilization and improve managerial operations**

(1) Excel sheets (manage *cash flow*), if we can't track we can't control. Small business lack of data or resources. Process Improvement and Risk Management.
Three impacts : **auditors** monitor, analyze, verify data for recommendations **tax accountant** use DS to analyze taxations, faster investment decisions, higher profit

Process Flow: Define goals, identify metrics, list/collect/extract data, explore /analyze data, interpret/visualize data, infere for decision-making

**Life Cycle**: Discovery (business domain and resources), Data Preparation (ETL: extract, load and transform), Model Planning (identify techniques and data to
understand variable relationships), Model building (testing, training and production), Communicate Results (Identify key findings, develop narrative for
stakeholder), Operationalize (final reports, briefs, codes and technical documents)

## Types of Data Analytics
- Descriptive Analytics (what happened?): get more information about past (*summary of facts*): **Data aggregation** (data gather and summarize: MS Excel, MATLAB
  SPSS, STATA) and **Data Mining**
- Diagnostic Analytics (why did this happened): Deeper look at data to see root causes: **Drill-down**, **Data mining**, **Data discovery** and **Correlation**. Why
  sells have decreased of why does someone sell less than expected
- Predictive Analytics (What will happen): future outcomes in terms of probability to events occur (e.g. sentiment analysis, recommenders)
- Prescriptive Analytics (how we can we make it happen): solution for what has been predicted

### Example: Amazon
- Diagnostic Analytics: revenue increased in West Coast in previous year -> increased spending in sales training
- Historical purchases: price, time, weather -> revenue is expected to grow x%
- Descriptive Analytics: Amazon has spent 20M in sales training in previous year
- Prescriptive Analytics: Identify sales training that fetch good ROI and implement optimization plan (which drop which continue)

## Benefits
- Decision-making: faster and better (digital marketing strategy), customer satisfaction and revenue, define customer target, preferences,
  location, popular brand, forecast demand, identify seasons, sentiment, optimum prices
- Cost reduction : (every click is monitoring) and we can see browser interest (wider demands), reduce fail campaign. Shopping patterns, demographic and time
  of purchase, weather data. Plan campaign: use predictive analysis. Example: 642B are returned because consumer miss info during purchase
  (footwear, clothing).If know which info, then can control the return rate.
- Identify potential problems, operations that yield bet results, error-prone areas
### Amazon example
They know what are you going to buy because predictive analysis and anticipate shipping (*increase sales, inventory and reduce supply chain cost*). For example,
choose warehouse near to customer (shipping cost like when some habitant buy something during a season). **Discount:** manage discount and prices (based on 
**website activity, competitor pricing, product availability, item preferences, order history, expected profit**). We cn use Power BI, Tableau and Logic
 
## Dealing with types of data
There are some terminologies that are core of Data Analytics:-
- **Observation** a record which when are grouped are call tables
- **Data sampling** statistical techinque used to select, manipulate and analyze a representative subset of data points
- **Dataset** collection of total data captured about the topic we will analyze
- **Prediction** move from what has happen to what will happen

There is structured, semi-structured (contain both like csv files) and unstructured data (lacks form like email: 80% of total data: presentations,
email, spreadsheet, documents, audio/video, images, web searches and social media posts): improve customer relationship, targeted marketing or 
perform sentiment analysis for product review.

Data can be **qualitative** or **quantitative** that has levels (nature of measurements: nominal, ordinal, interval, ratio(there's 0 value)).
There's a topic which we have to cover briefly : **Normal distribution** or Bell curve/Gauss Distribution which represents most of natural fenomena. It
has some basic parametes: Mean (average of data points), Variance (sum of squared error of data points), Standar Deviation (root of variance which represent
how far are we from a point).

## Data visualization for decision making
It's graphical representation of data, storytelling with a purpose (no just cells, instead we show trends). Thus, we can help decision makers to better outcomes, provides simplicity, clarity, patterns, etc (crisp, clear and memorable). Company leader can see flags faster, spot problems inmediately. Next, we are going to describe commonly used visualizations:
- Heatmap : visualize through color graduations, relation and strenght between multiple variables. It has a form of a matrix, whose cells represent the relationship (correlatiton)
- Frequency distribution plot: frequency of ocurrence of a variable (included normalized). It's described with tables, histogram, line graph, dot plot and pie chart.
- Swarm plot: can give better viz of data distribution but works well for small datasets (on dimensional data along an axis). Beeswarm plot for example, time vs tip.

Data viz provide acces to know data trends, outliers, patterns and help decision makers. EDA is an approach to analyze data and summarize main characteristics (first step).
### Data viz tools
Tableu: it's the most widely used because simple use. FusionChart: based on JavaScript with numeruous platforms and frameworks, example templates. HighCharts: fast and flexible solution and cross browser support. Datawrapper: simple interface for csv, charts and maps for media organizations. Plotly: more sofisticated with Python, R and Matlab. Sisense: full stack analytics with drag.drop interface. PowerBI: semi Business Analytics tools, standar customized viz. Looker: with real time analytics. DOMO: social colaboration, real time using sparklines, trend indicators, widgets and integrated Google Analytics. Qlik: clean interface, setup and various features. Board: BI systems for large companies.

There are some languages and libraries: Scala (compiled language to faster execution), Python (seaborn (high level interface for matplolive), Bokeh (interactive web apps, JSON, HTML, streaming) and matplotlib (2d and 3d graphic support)), R (ggplot2, latte graphics, Shiny (interactive web apps), etc), Java (2D, 3D abd advanced), JavaScript. Dashboard are customized viz with multiple variables, displays gauge, tables, graphs, etc (highly interactive, dynamic and real time data update). To build them, we need to plan some steps: analyze target audience, key business parameters (responsabilities KRA, process indicators KPI, process area KPA, SLA service agreement). Then, we need to know end goal of dashboard, develop the dashboard and continuous improvement iwht audience feedback.
