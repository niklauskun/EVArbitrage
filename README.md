# MarkovEV arbitrage

This repository use Markov model to predict real-time price bias (compare to day-ahead price) and evaluate battery state-of-charge(SoC) level. With value function of SoC, we optimize battery price abitrage using stochastic dynamic programming.

## How to use this code

Markov models for 4 zones in NYISO are pre-trained and saved in csv files. Python scripts are available for other Markov model training. Use Matlab scripts to test different cases.

### Markov Model Trainning

Use pre_processing_main.py script:

Use Line 10-11 to change training data size by changing year.

Use Line 12-13 to change location by changing real-time price and day-ahead-price file name.

optional_kwargs are in Line 35.

### Battery Arbitrage Case Setting

Use main_EV.m script:

For different cases, change parameters in Case Setting section.

location could be ```['NYC', 'LONGIL', 'NORTH', 'WEST']```.

startDay and endDay could be any dates in test dataset (2019 for current code), the startDay should be at least 1 day ahead of endDay.

Current code have several parameters for different EV usage patterns:

direction could be ```[0, 1]```, 0-charge only; 1-bidirection.

pluginPeriod could be ```[1, 2]```, which means number of plug-in period per day.

startPeriod and endPeriod are start plug-in time period and end plug-in time period, change numbers between [0,48]. When pluginPeriod = 1, startPeriod2 and endPeriod2 are not used.

eC1 and eC2 are SoC consumption during plug-off period. When eC2 is not used.

e0 is initial SoC, only used in first plug-in period of startDay.

ef is final SoC target, used in all plug-in period.

efp is the penalty for final discharge level.

Pr is normalized power rating wrt energy rating, storage duration is 1/Pr (ex. Pr=0.5, storage duration is 2hrs). Battery size is normalized to 1MWh.

eta is battery one-way efficiency.

c is marginal discharge cost - degradation, only used in bidirection cases.

### Organization of this directory
Folder PATH listing for volume OS
Volume serial number is 000000C5 5EFD:6DDE
C:\USERS\WENMI\DESKTOP\EVARBITRAGE
岫  Arb_Value.m
岫  Arb_Value_Charge.m
岫  CalcValueNoUnc.m
岫  CalcValueNoUnc_Charge.m
岫  main_EV.m
岫  pre_processing_functions.py
岫  pre_processing_main.py
岫  README.md
岫      
念岸DAP_data
岫      DAP_LONGIL_2010_2019.mat
岫      DAP_NORTH_2010_2019.mat
岫      DAP_NYC_2010_2019.mat
岫      DAP_WEST_2010_2019.mat
岫      
念岸RTP_data
岫      RTP_LONGIL_2010_2019.mat
岫      RTP_NORTH_2010_2019.mat
岫      RTP_NYC_2010_2019.mat
岫      RTP_WEST_2010_2019.mat
岫      
弩岸transition_matrix

