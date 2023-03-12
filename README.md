# Predicting violent conflicts with open source data and deep learning

Building AI course project


## Summary

This project uses freely available data, including satellite images, socio-economic data, and conflict history, to predict the probability of violent conflicts at sub-national level in African countries, based on deep learning methods.


## Background

Large-scale conflicts kill thousands of people across the globe and forces affected people to relocate within their countries or even across borders and continents. Armed conflicts have various economic consequences and can undermine the functioning of political systems, prevent countries from escaping poverty, and hinder humanitarian support where it is mostly needed.

The challenges of preventing and mitigating to conflicts are evident when it escalates in regions and at times where it is not expected. Policymakers, humanitarian aid agencies and first responders could benefit from tools that map and monitor regions at risk of conflict and that has the capability of forecasting the probability of conflict onset.

The main objective of this project is predicting (forecasting) the probability of violent conflicts for countries in Africa at the sub-national level, based on different open geodata (e.g. satellite images, meterological data), socio-economic statistical data (such as GDP), and past conflict history.


## How is it used?

Combining data driven crisis forecasting and prevention could help to prevent conflicts from escalating into violence. Even an imperfect forecasting system could have the potential to inform the placement of humanitarian aid missions, peacekeepers, or the deployment of NGO resources to prevent the outbreak of violence, which could ultimately save lives and minimize economic and political consequences.


## Study area and observation period

The study area encompasses countries of continental Africa. The prediciton of conflict probability will be at the level of 847 individual administrative units (one level below national administrative borders, for example provinces). The observation period is from 2001 to 2021. This corresponds to the period when all repsonse and predictor variables are available.

![Study area](/StudyAreaAfrica_ConflictPredictionGeodata.png)
African countries, represented as polygons in ESRI shapefile format. Source: [NaturalEarth](https://www.naturalearthdata.com/). 


## Data sources and AI methods

### Response variable
To assess conflicts, this project uses monthly data on armed conflict events per country occurring between 2000 and 2020 from the [Uppsala Conflict Data Program](https://ucdp.uu.se/). Three types of conflict are reported in this data base:

- **"State-based violence"** (A state-based armed conflict is a contested incompatibility that concerns government and/or territory where the use of armed force between two parties, of which at least one is the government of a state, results in at least 25 battle-related deaths in one calendar year.)

- **"Non-state violence"** (The use of armed force between two organised armed groups, neither of which is the government of a state, which results in at least 25 battle-related deaths in a year.)

- **"One-sided violence"** (The deliberate use of armed force by the government of a state or by a formally organised group against civilians which results in at least 25 deaths in a year.)

The conflicts data will be used as both, predictor and response variable, respectively (because it is hypothesized that conflict history has an impact on future conflicts).


### Predictor variables
Eleven socio-economic variables were considered as predictor variables in this project. The data source is the [World Bank Open Data portal](https://data.worldbank.org):

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

Additional predictor variables will be generated in [Google Earth Engine](https://earthengine.google.com). These predictor variables characterise the environmental conditions in the study area. This will be a comprehensive data base of the following variables:

- **Monthly average temperature** from ECMWF.
- **Monthly precipitation sum** from CHIRPS.
- **Monthly precipitation anomaly** data from CHIRPS, i.e. deviaiton of recorded precipitation from long-term evareg (1970-1990) (usefull to assess droughts).
- **Eucledian distance to freshwater** sources, based on the [JRC Global Surface Water Explorer] (https://global-surface-water.appspot.com).
- **Average travel time** to larger cities (to proxy market access).
- **Terrain characteristics** (e.g. elevation, slope).
- **Population density** data from the [WorldPop](https://www.worldpop.org) project.


## Challenges

This project will not predict the exact number of fatalities or the conflict parties involved. Rather, it will predict conflict probability.


## What has bee achieved so far, what next?

- All predictor and response variables have already been preprocessed. The result of this is a comprehensive set of (i) conflict-data, (ii) socio-economic data, and (iii) environmental data, summarized for each of the 847 administratibe units. Temporal data, such as precipitation, temperature, drought indices, and the conflict data, have a temporal resolution of one month (i.e., monthly data). Data considered temporalily "invariant", such as distance to freshwater or terrain attributes, are presented as one value per administratige unit. The complete data set is available as *.csv file and "ready-to-analyse".
- Next steps currently undertaken include the definition of a suitable deep learning architecture (this will be based on [Tensorflow](https://www.tensorflow.org)).
- Google Earth Engine Code to create the environmental predictors will be cleaned, commented and presented in this GitHub repository soon.


## Acknowledgments

### Sources of inspiration:
- ViEWS - A political violence early-warning system. Source: https://doi.org/10.1177/0022343319823860 (last accessed 05 Jan 2023).
- Schellens, M.K., Belyazid, S., 2020. Revisiting the Contested Role of Natural Resources in Violent Conflict Risk through Machine Learning. Sustainability 12, 6574. https://doi.org/10.3390/su12166574.
- Hegre, H., et al., 2019. ViEWS: A political violence early-warning system. Journal of Peace Research 56, 155–174. https://doi.org/10.1177/0022343319823860.
- Muchlinski, D., Siroky, D., He, J., Kocher, M., 2016. Comparing Random Forest with Logistic Regression for Predicting Class-Imbalanced Civil War Onset Data. Political Analysis 24, 87–103. https://doi.org/10.1093/pan/mpv024.
- Owain, E.L., Maslin, M.A., 2018. Assessing the relative contribution of economic, political and environmental factors on past conflict and the displacement of people in East Africa. Palgrave Communications 4, 47. https://doi.org/10.1057/s41599-018-0096-6.
