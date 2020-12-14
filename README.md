CEE 6410 - Water Resources Systems Analysis

By Patrick Campana 
patrickcampana555@gmail.com 
Fall Semester 2020


Model Title: Flaming Gorge Managment Objectives Tradeoffs With Imposed Managment Objective
of Maximizing Releases to Lake Powell.

Written By: Patrick Campana
Contact Info: patrickcampana555@gmail.com

Model Status: Fails to work as intended, problem likely with how binary
variable Env is being used by the model.


Model Description:


Models Flaming Gorge Dam releases and hydrologic inputs for a 5 year period. Utilizes
monthly times step. Model was designed to examine trade offs in satisfying 7 different
managment objectives. These objectives are:

1.        Satisfy hydropower demand
2.        Maintain enough storage capacity to successfully route floods
3.        Maintain enough storage to meet water supply demands
4.        Satisfy baseflow requirements
5.        Maximize the number of years environmental spring flow releases are met for Humpback Chub larvae flood plain access in Reach 2
6.        Maximize the number of years environmental summer base flows are met for Colorado Pikeminnows in Reach 2.
7.        Maximize the flow sent to Lake Powell from Flaming Gorge


Model was intially designed to use hydrologic scenarios and, therefore, all variables
had(Location,Month,Year) dimensions. However I could not figure out how to properly
reference the Year and Month ordinates when coding my mass balance constraint equations
so I converted everything to months and removed the year dimension from most variables,
hence the title of the file SemseterProjectCodeMonthsONLY.

Data for different hydrologic scenarios can be copied into this model directly out of the spreadsheet in this github repository
called F.G._MODEL_MASTER_DATASHEET_PLUS_EXCEL_MODEL.xlsm. The first sheet in the work book containts the data. 
If you decide to edit the data, the monthly flow demands refer to specific hydrologic
scenarios. Therefore make sure to sync the hydrologic scenrios of the hydrologic inputs
and the monthly flow demands. In addition make sure to set the baseflow in the month
of June to zero to allow other constraints to bind in this month, ideally the LTRP constraint

The binary variable "Env" in this code is intended to be multiplied by the EnviroFlows Value
and be used as X('Dam',M6,M18,M30,M42,M54) constraint for the month of June. That way the model could turn
the LTRP flow on and off if the model became infeasible by meeting it. However,
considering this not what happens I am guessing this is not how the MIP solver works.

All flow and storage volumes are in Ac-ft/month and Ac-ft respectively.
