<!-- This is the markdown template for the final project of the Building AI course, 
created by Reaktor Innovations and University of Helsinki. 
Copy the template, paste it to your GitHub README and edit! -->

# Predicting violent conflicts with open source data and deep learning

Building AI course project

## Summary

This project uses freely available data, including satellite images, socio-economic data, and conflict history, to predict the probability of violent conflicts at sub-national level in African countries, based on deep learning methods.


## Background

Large-scale conflicts kill thousands of people across the globe and forces affected people to relocate within their countries or even across borders and continents. Armed conflicts have various economic consequences and can undermine the functioning of political systems, prevent countries from escaping poverty, and hinder humanitarian support where it is mostly needed.

The challenges of preventing and mitigating to conflicts are evident when it escalates in regions and at times where it is not expected. Policymakers, humanitarian aid agencies and first responders could benefit from tools that map and monitor regions at risk of conflict and that has the capability of forecasting the probability of conflict onset.

The main objective of this project is predicting the probability of violent conflicts for countries in Africa at the sub-national level, based on different open geodata (e.g. satellite images, meterological data), socio-economic statistical data (such as GDP), and past conflict history.


## How is it used?

Describe the process of using the solution. In what kind situations is the solution needed (environment, time, etc.)? Who are the users, what kinds of needs should be taken into account?

Combining data driven crisis forecasting and prevention could help to prevent conflicts from escalating into violence. Even an imperfect forecasting system could have the potential to inform the placement of humanitarian aid missions, peacekeepers, or the deployment of NGO resources to prevent the outbreak of violence, which could ultimately save lives and minimize economic and political consequences.

## Study area
The study area encompasses countries of continental Africa. The prediciton of conflict probability will be at the level of individual administrative units (one level below national administrative borders).
![Study area](/StudyAreaAfrica_ConflictPredictionGeodata.png)

## Data sources and AI methods

# Response variable
To assess conflicts, this project uses monthly data on armed conflict events per country occurring between 2000 and 2020 from the [Uppsala Conflict Data Program](https://ucdp.uu.se/). Three types of conflict are reported in this data base:

- **"State-based violence"** (A state-based armed conflict is a contested incompatibility that concerns government and/or territory where the use of armed force between two parties, of which at least one is the government of a state, results in at least 25 battle-related deaths in one calendar year.)

- **"Non-state violence"** (The use of armed force between two organised armed groups, neither of which is the government of a state, which results in at least 25 battle-related deaths in a year.)

- **"One-sided violence"** (The deliberate use of armed force by the government of a state or by a formally organised group against civilians which results in at least 25 deaths in a year.)

The conflicts data will be sused as both, predictor and response variable, respectively (because it is hypothesised that conflict histiry has an impact on future conflicts)

# Predictor variables
Eleven socio-economic variables were considered as predictor variables in this project. The data source is the [World Bank Open Data portal](https://data.worldbank.org ), where these data can be sourced from as *.csv files.

- **arbl**:	Arable land (% of land area).
- **wres**:	Renewable internal freshwater resources per capita (cubic meters).
- **gdp**: GDP per capita (current US).
- **gdpgr**: GDP per capita growth (annual percentage).
- **gdpcp**: GDP per capita, PPP (current international US Dollar).
- **mort**: Mortality rate, under-5 (per 1,000 live births).
- **infl**: Inflation, GDP deflator (annual percentage).
- **refu**: Refugee population by country or territory of asylum.
- **unempl**: Unemployment, total (percentage of total labor force) (modeled ILO estimate).
- **wwith**: Annual freshwater withdrawals, total (percentage of internal resources).
- **ythb**: Age dependency ratio (percentage of working-age population).

Additional predictor variables will be generated with Google Earth Engine. These predictor variables characterise the environmental conditions in the study area. This will be a comprehensive data base of the following variables:
- **Monthly average temperature** data from ECMWF.
- **Monthly precipitation** data from CHIRPS.
- **Monthly precipitation anomaly** data from CHIRPS (to assess droughts).
- **Eucledian distance to freshwater** sources.
- **Average travel time** to larger cities (to proxy market access).
- **Terrain characteristics** (e.g. elevation, slope).

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

## Challenges
This project will not predict the exact number of fatalities or the conflict parties involved. Rather, it will predict conflict probability.
What does your project _not_ solve? Which limitations and ethical considerations should be taken into account when deploying a solution like this?

## What next?

How could your project grow and become something even more? What kind of skills, what kind of assistance would you  need to move on?

Next steps currently undertalen include the preprocessing of the environmental predictor variables in Google Earth Engine and the definition of a suitable deep learning architecture (will be based on Tensorflow).


## Acknowledgments

* list here the sources of inspiration 
* do not use code, images, data etc. from others without permission
* when you have permission to use other people's materials, always mention the original creator and the open source / Creative Commons licence they've used
  <br>For example: [Sleeping Cat on Her Back by Umberto Salvagnin](https://commons.wikimedia.org/wiki/File:Sleeping_cat_on_her_back.jpg#filelinks) / [CC BY 2.0](https://creativecommons.org/licenses/by/2.0)
* etc
