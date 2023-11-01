![Cover](https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Photos/cover.png)

# 4G Mobile Data Traffic Forecasting and Analysis

## Introduction
In the mobile communications context, network dimensioning is the process of estimating the number of network elements to deliver the required coverage (range of servicing area) and capacity (ability to provide service) in a given area (Lundevall, et al. 2004 as cited in Basit 2009). It is the first step in network planning; thus, it is a crucial task as ineffective dimensioning leads to degradation of service and user experience, and poor investment-related decisions from unnecessary network upgrades (Gijon, et. al. 2021). Generally, the goal of network planning is to provide excellent quality of service and user experience while minimising investments. However, although the network has been well-planned before deployment, new applications requiring mobile network connectivity create growing traffic through time. Therefore, when planning for changes in the network such as expansion or reallocation of resources, planning engineers must consider not only the current consumption, but also the future demand for the services. Thus, there is a need for forecasting when dimensioning the mobile network elements. The first step in network dimensioning is data/traffic analysis (Basit 2009) which involves examining the current and historical consumption of the users while also aiming to forecast future demand. Both long-term and short-term forecasting have their set of benefits. Long-term forecasting is often used for large-scale upgrade planning or rolling out new technologies (Elnegaard & Stohrdahl 2012). Meanwhile, short-term forecasting is suitable for the continuous monitoring, fine tuning, and proactive optimisation of the network. There are several types of traffic in the RAN such as SMS, voice calls, and mobile data (internet). Bastos (2019) explains how mobile data trafﬁc is heavily inﬂuenced by unusual events and changes in network conﬁguration; thus, it is relatively more difficult to forecast mobile data traffic compared to legacy technologies (SMS and voice calls). This paper focuses on the application of short-term forecasting in mobile data traffic analysis for 4G or LTE RAN. For this study, the mobile traffic data is analysed on the “cell” level, the area serviced by a single cell site because capacity adjustments are mostly done in the cell level (e.g. changes in configuration and license expansions to allow more capacity). 


## Terminologies
* **Cell**  
    Refers to the geographical area serviced by the base station (cell site) in a cellular network
  
* **Cell Site**  
    Consists of radio units and radio equipment servicing a specific geographical area (cell); also called base station
  
* **LTE (Long-Term Evolution)**  
    4G wireless network communications standard featuring increased capacity and speed for mobile devices supporting SMS, voice calls, and mobile data services

* **KPI (Key Performance Indicator)**  
    A type of performance measurement. In the context of this study, it refers to the performance of the network elements

* **Operator**  
    Term used to refer to a telecommunications provider

* **RAN (Radio Access Network)**  
    The part of a mobile telecommunications system connecting users’ devices (e.g. mobile phones) to other parts of the network through the radio (air) interface. 

* **4G**  
    4th Generation Broadband Cellular Network Technology also known as LTE

* **5G**  
    5th Generation Broadband Cellular Network Technology providing higher capacity and speeds compared to preceding technology, LTE

## Data Source
The [dataset](https://www.kaggle.com/naebolo/predict-traffic-of-lte-network) used in this study is sourced from Kaggle and consists of hourly traffic for each of the 57 cells. The period of interest is from October 23, 2017, to October 22, 2018.

## Focus of the Study
With the introduction of 5G, operators should assess how long they should still invest in 4G and upgrade if the need arises or focus on 5G and prepare for 4G sunsetting. This study focuses on short-term forecasting on a cellular level. The goal of forecasting the traffic on a cell level is to determine the demand for the service on a granular level. Short-term forecasting helps operators maximize their current investments through optimization while remaining competitive against other operators.

## Objectives
* To describe the seasonality and trend components of the cellular level traffic volume.
* To assess the performance of different forecasting model and tools in short-term forecasting of mobile data traffic.
* To determine the most appropriate model for forecasting daily mobile data traffic.


## Repository Structure
This repository is organized as follows:

* Calculations: Excel file for computation of Error Metrics
* Data: Contains the dataset used in this analysis.
* Tables: Summary of Models Used and  Results
* Photos: Cover photo
* Visualizations: Graphs generated
* Viz Files: PowerBI file
* References: List of Studies and Articles used as references


## Related Work
Previous studies have explored various forecasting models for mobile data traffic, including time series forecasting models and supervised learning techniques.  
  
Chmieliauskas & Guršnys (2019) conducted a study on the feasibility of mobile traffic forecasting using fbProphet algorithm using five months of daily traffic training data and one month of testing data and assessed the Facebook fbProphet algorithm ability to forecast daily LTE traffic. According to their findings, their forecasting model is applicable to mobile traffic as it applies to 90% of the values. The resulting MAPE of their forecast is 44%.  
  
A study on long-term data traffic forecasting for LTE networks compared the performance of time series forecasting models (ARIMA and Additive Holt-Winters) with Supervised Learning (SL) techniques (Random Forest, Neural Networks and Support Vector Regression) and found SL techniques outperforming the time series approaches. Previous works have also revealed the effectiveness of Deep Learning (DL) techniques against classical time series forecasting techniques for short-term forecasting applications (Gijon et al. 2021).


## Forecasting Methodology
The KPI, total data traffic volume per cell expressed in megabytes (MB), is used to estimate and forecast the demand and consumption of 4G service within a single servicing area (cell). A single LTE cell is selected for the sample forecast. The dataset used is a time series of daily mobile data traffic volume for one year. The data consisting of 365 data points is divided into the training (335 data points) and test (30 data points) datasets to assess the performance of the forecasting models. To determine which model best suits the data, error metrics such as RMSE, MAE, MAPE, and MSE are calculated to compare the deviation from the actual values for each forecasting model. The tools used in this study are PowerBI, Tableau, and Exploratory.io. Both PowerBI and Tableau use exponential smoothing forecasting models. Using the automatic function, these programs choose the models best fitting the trend and seasonality of the data (whether they are additive or multiplicative). Exploratory.io also has automatic model selection functions, but also lets the user to define specific parameters such as model order, stationarity test, and trend and seasonality parameters. The forecasting models and tools used are listed in Table 1:  
  
*Table 1. Forecasting Tools and Models*  
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Tables/Table%201.%20Forecasting%20Tools%20and%20Models.png" width="400">
</p>

### Dataset
The total daily traffic volume per cell is computed as the sum of all the hourly traffic within a single LTE cell (Cell_003781) for a single day. After the aggregation of data, the resulting graph for the total daily 4G data traffic volume of the sample cell is shown in Figure 1.

*Figure 1. Historical Data of Total Daily 4G Data Traffic Volume of a Single Cell*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Visualizations/Figure%201.%20Historical%20Data%20of%20Total%20Daily%204G%20Data%20Traffic%20Volume%20of%20a%20Single%20Cell.png" width="800">
</p>

Overall, there is an increasing trend from October 2017 to October 2018 as indicated by the red trend line in Figure 1.  On a magnified level, the increase in traffic is mostly observed during the period from January 2018 until May 2018. The traffic from May 2018 (inflection point) onwards changed into an almost horizontal trend (slightly decreasing) with a small fluctuation on the month of July. 


### Decomposition
To verify the observations, the STL decomposition method is used to compute the trend-cycle and seasonal indices.  Figure 2 shows the results of the additive decomposition model, confirming the trend observation made from the previous paragraphs. It also depicts the data traffic volume’s weekly seasonal trend.

*Figure 2. STL for the Historical Data*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Visualizations/Figure%202.%20STL%20for%20the%20Historical%20Data.png" width="800">
</p>

## Results
The results of the forecasting models are presented in this section.

### Additive Holt-Winters Model (Tableau)
Using the automatic model selection function, out of the eight models available in Tableau, the most suitable model chosen for this time series is the AHW (both seasonal and trend components are additive). The resulting forecast in Figure 3 follows the shape of the seasonal and trend components shown during decomposition (Figure 2).

*Figure 3. Additive Holt-Winters Model Forecast using Tableau*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Visualizations/Figure%203.%20Additive%20Holt-Winters%20Model%20Forecast%20using%20Tableau.png" width="800">
</p>

### Holt's Linear and Multiplicative Holt-Winters Models (PowerBI)
PowerBI’s automatic model selection function has detected no seasonality in the data and has selected HL for its forecast as shown in Figure 4. The resulting error compared to the actual data is significantly high (refer to Table 2).

*Figure 4. Holt’s Linear Method using PowerBI*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Visualizations/Figure%204.%20Holt%E2%80%99s%20Linear%20Method%20using%20PowerBI.png" width="800">
</p>

Using the results of the decomposition in Figure 2, the seasonality for the forecast in PowerBI is manually set to weekly. By default, PowerBI uses MHW Method for seasonal data (Microsoft 2014). The resulting forecast using this model is shown in Figure 5. There is an improvement in the forecast upon consideration of the seasonality. The result is similar to the graph in Figure 3.

*Figure 5. Multiplicative Holt-Winter’s Model Forecast using PowerBI*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Visualizations/Figure%205.%20Multiplicative%20Holt-Winter%E2%80%99s%20Model%20Forecast%20using%20PowerBI.png" width="800">
</p>

### ARIMA and Prophet Models (Exploratory.io)
Similar to the decomposition results in Figure 2, Exploratory.io also detected the weekly seasonality of the data. The resulting model order automatically selected using the AIC is ARIMA(0,1,4)(1,0,0)[7]. The graph in Figure 6 reveals the forecasting results with traffic volume slowly decreasing similar to damped oscillations, while still following the seasonality component.

*Figure 6. ARIMA Model Forecast using Exploratory.io*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Visualizations/Figure%206.%20ARIMA%20Model%20Forecast%20using%20Exploratory.io.png" width="800">
</p>

Looking at the effect of seasonality shown in Figure 7, it is evident the daily traffic is higher during the weekends, especially Sunday, compared to the other days. The resulting forecast is shown in Figure 8. There were no data regarding external predictors in the dataset. However, according to Lin et al. *(2018), consideration of the holiday effects in network traffic forecasting is important for efficient congestion management and network planning. Therefore, to improve the forecast, the built-in holiday effect option in Exploratory was used assuming the same strength effect of the seasonality for comparison. The resulting forecast is shown in Figure 9. Referring to Table 2, there is a slight improvement in the forecast as confirmed by the reduction of error values and 2% in MAPE.

*Figure 7. Effect of Seasonality*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Visualizations/Figure%207.%20Effect%20of%20Seasonality.png" width="500">
</p>

*Figure 8. Prophet Forecast using Exploratory.io*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Visualizations/Figure%208.%20Prophet%20Forecast%20using%20Exploratory.io.png" width="800">
</p>

*Figure 9. Prophet Forecast with Holiday Effect using Exploratory.io*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Visualizations/Figure%209.%20Prophet%20Forecast%20with%20Holiday%20Effect%20using%20Exploratory.io.png" width="800">
</p>

## Comparison of All Forecasting Models
All forecasting results are shown in Figures 10 and 11. The graphs of the forecasts closely resemble one another, following the shape of the weekly seasonal component of the data except for the forecast using HL. Clearly, the HL forecast has the highest deviation without the need to calculate the error metrics. For the rest of the models, calculating the error metrics for each model is essential to quantify how well the models performed as they generally appear the same and some forecasts overlap the others in the graph. The summary of error metrics is in Table 2.

*Figure 10. Comparison of All Models (Zoomed out)*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Visualizations/Figure%2010.%20Comparison%20of%20All%20Models%20(Zoomed%20in).png" width="900">
</p>

*Figure 11. Comparison of All Models (Zoomed out)*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Visualizations/Figure%2011.%20Comparison%20of%20All%20Models%20(Zoomed%20out).png" width="900">
</p>

Evaluating the error metrics (computed in Excel - [see computations](https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Calculations/Error%20Metrics%20Computation.xlsx)) summarised in Table 2, the forecasts generated by Tableau using the AHW and PowerBI using MHW have the lowest error values (highest accuracy) when compared to the test dataset. Here, the additive model slightly performed better than the multiplicative model. From observation, the seasonality looks more additive than multiplicative, as most of the weekly variations have almost equal widths. Furthermore, both Tableau and Exploratory detected the characteristics of the seasonal component of the data as weekly and additive. The forecasts generated using Exploratory.io also performed relatively well with error metrics very close to one another. The Prophet forecast with Holiday Effect outperformed the ARIMA forecast. Without the holiday effect, the ARIMA model’s forecast is slightly more accurate than using the Prophet algorithm. This highlights the importance of considering the effect of holidays. As mentioned previously, through visual inspection, the forecast generated by the HL (PowerBI without seasonality) deviated significantly from the actual values. The error metrics in Table 2 confirms this observation with the MAPE of the forecast almost twice the percentage error of the other models. Out of all the models, only HL did not consider the seasonality of the data. Whereas the other models accounted for the seasonality component and produced satisfactory forecasts.  Although the overall trend is increasing, the models put more weight to the most recent values. Consequently, all the forecasts followed an almost horizontal trend (slightly decreasing).

*Table 2. Comparison of Error Metrics*
<p align="center">
   <img src="https://github.com/mrylprz/LTE-traffic-forecasting/blob/main/Tables/Table%202.%20Comparison%20of%20Error%20Metrics.png" width="600">
</p>

## Conclusion
In summary, the seasonality of the daily mobile data traffic volume per cell is additive in nature and follows a weekly pattern resulting to most forecasts resembling the weekly pattern. Overall, the different time-series forecasting models performed satisfactorily with MAPEs below 30% except for the forecast using HL. AHW has outperformed the rest of the models. However, its error metrics are close to that of the MHW and the Prophet algorithm factoring the effect of holidays. With 60% of each of the Top 3 models’ datapoints below their MAPE, using any of these 3 models for forecasting the daily traffic volume per cell in an LTE network is acceptable in a high-level traffic analysis to determine the next course of action in network planning. 


## Recommendations
While the time-series forecasting models had acceptable results for traffic analysis, there are several ways to improve forecasts for network planning:
*	Finding a more recent dataset for a more relevant conclusion on the traffic’s trend considering the effect of introduction of 5G services
*	Sourcing a larger dataset to explore other seasonality effects (e.g. yearly or quarterly)
*	Exploring other ways to forecast traffic demand and applying forecasting on those data (e.g. forecasting number of subscribers consuming data and forecasting the average data consumption per user)
*	Improving the forecast using Prophet Algorithm by determining external predictors with strong effect on the variation of the mobile data traffic 
*	Using automatic time-series forecasting techniques (e.g. Auto.ARIMA or automatic selection of ETS models) instead of default forecasting functions in data visualisation tools 
*	Exploring machine learning techniques such as Supervised Learning and Deep Learning techniques for both Short-Term and Long-Term Forecasting in Network Planning
