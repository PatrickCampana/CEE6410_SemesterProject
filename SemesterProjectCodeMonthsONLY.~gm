$ontext

CEE 6410 - Water Resources Systems Analysis

Flaming Gorge Managment Objectives Tradeoffs With Imposed Managment Objective
of Maximizing Releases to Lake Powell.

Written By: Patrick Campana
Contact Info: patrickcampana555@gmail.com

Model Status: Fails to work as intended, problem likely with how binary
variable Env is being used by the model.


Model Description:

Models Flaming Gorge Dam releases and hydrologic inputs for a 5 year period. Utilizes
monthly times step. Model was designed to examine trade off in satisfying 7 different
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
reference the Year and Month ordinates when coding my mass balance constraints
so I converted everything to months and removed the year dimension from most variables,
hence the title of the file SemseterProjectCodeMonthsONLY.

Data for different hydrologic scenarios can be copied directly out of the spreadsheet in this github repository
called F.G._MODEL_MASTER_DATASHEET_PLUS_EXCEL_MODEL.xlsm. The hydrologic data is
in the last three sheets of the worksheet. The current model uses the wet hydrologic
scenario 5 years in a row. The monthly flow demands refer to specific hydrologic
scenarios. Therefore make sure to sync the hydrologic scenrios of the hydrologic inputs
and the monthly flow demands. In addition make sure to set the baseflow in the month
of June to zero to allow the hydropower constraint to bind in the month of June.
Enviromental Releases in the month of June are controlled by the EnviroFlows variable

The binary variable "Env" in this code is intended to be multiplied by the EnviroFlows Value
and be used as X('Dam',M6,M18,M30,M42,M54) constraint for the month of June. That way the model could turn
the LTRP flow on and off if the model became infeasible by meeting it. However,
considering this not what happens I guessing this is not how the MIP solver works.

All flow and storage volumes are in Ac-ft/month and Ac-ft respectively.

$offtext

* 1. DEFINE MODEL DIMENSIONS
SETS Loc Locations in Model / Res "For storage or water surface elevation in F.G."
          Dam "For Flow out of F.G. Dam"/


     Years number of years modeled /Y1*Y5/

     Months variable for each month of the year M1 corresponds to January /M1*M60/
     HydrologicScenarios the three different hydrologic scenarios I envisioned for this model /W1*W3/;

* 2. DEFINE INPUT DATA
PARAMETERS

*Hydropower Constraints
   HydroPower(Months) Hydropower Monthly Flow Volumes
         /
M1        110062.8099
M2        108932.2314
M3        50745.12397
M4        49731.57025
M5        51806.28099
M6        124661.157
M7        89708.42975
M8        108694.2149
M9        98433.71901
M10        63808.26446
M11        77208.59504
M12        105988.7603
M13        110062.8099
M14        108932.2314
M15        50745.12397
M16        49731.57025
M17        51806.28099
M18        124661.157
M19        89708.42975
M20        108694.2149
M21        98433.71901
M22        63808.26446
M23        77208.59504
M24        105988.7603
M25        110062.8099
M26        108932.2314
M27        50745.12397
M28        49731.57025
M29        51806.28099
M30        124661.157
M31        89708.42975
M32        108694.2149
M33        98433.71901
M34        63808.26446
M35        77208.59504
M36        105988.7603
M37        110062.8099
M38        108932.2314
M39        50745.12397
M40        49731.57025
M41        51806.28099
M42        124661.157
M43        89708.42975
M44        108694.2149
M45        98433.71901
M46        63808.26446
M47        77208.59504
M48        105988.7603
M49        110062.8099
M50        108932.2314
M51        50745.12397
M52        49731.57025
M53        51806.28099
M54        124661.157
M55        89708.42975
M56        108694.2149
M57        98433.71901
M58        63808.26446
M59        77208.59504
M60        105988.7603
/


*Flow Into Flaming Gorge Dam
 FlowIn(Months) Flow Into F.G.
/
M1        110062.81
M2        108932.23
M3        50745.12
M4        49731.57
M5        51806.28
M6        124661.16
M7        89708.43
M8        108694.21
M9        98433.72
M10        63808.26
M11        77208.60
M12        105988.76
M13        110062.81
M14        108932.23
M15        50745.12
M16        49731.57
M17        51806.28
M18        124661.16
M19        89708.43
M20        108694.21
M21        98433.72
M22        63808.26
M23        77208.60
M24        105988.76
M25        110062.81
M26        108932.23
M27        50745.12
M28        49731.57
M29        51806.28
M30        124661.16
M31        89708.43
M32        108694.21
M33        98433.72
M34        63808.26
M35        77208.60
M36        105988.76
M37        110062.81
M38        108932.23
M39        50745.12
M40        49731.57
M41        51806.28
M42        124661.16
M43        89708.43
M44        108694.21
M45        98433.72
M46        63808.26
M47        77208.60
M48        105988.76
M49        110062.81
M50        108932.23
M51        50745.12
M52        49731.57
M53        51806.28
M54        124661.16
M55        89708.43
M56        108694.21
M57        98433.72
M58        63808.26
M59        77208.60
M60        105988.76
/

*Remember to set M6, M18, M30, M42, M54 to zero, i.e. June
BaseFlows(Months) Base Flow Constraints In Each Year Monthly Flow Volumes (Ac-ft)
/M1        61487.60331
M2        55537.19008
M3        49190.08264
M4        47603.30579
M5        50578.5124
M6       0
M7        98380.16529
M8        98380.16529
M9        95206.61157
M10        52264.46281
M11        50578.5124
M12        61487.60331
M13        61487.60331
M14        55537.19008
M15        49190.08264
M16        47603.30579
M17        50578.5124
M18        0
M19        98380.16529
M20        98380.16529
M21        95206.61157
M22        52264.46281
M23        50578.5124
M24        61487.60331
M25        61487.60331
M26        55537.19008
M27        49190.08264
M28        47603.30579
M29        50578.5124
M30        0
M31        98380.16529
M32        98380.16529
M33        95206.61157
M34        52264.46281
M35        50578.5124
M36        61487.60331
M37        61487.60331
M38        55537.19008
M39        49190.08264
M40        47603.30579
M41        50578.5124
M42        0
M43        98380.16529
M44        98380.16529
M45        95206.61157
M46        52264.46281
M47        50578.5124
M48        61487.60331
M49        61487.60331
M50        55537.19008
M51        49190.08264
M52        47603.30579
M53        50578.5124
M54        0
M55        98380.16529
M56        98380.16529
M57        95206.61157
M58        52264.46281
M59        50578.5124
M60        61487.60331
/;


*LTRP enviromental flows for each year obtained by  subtracting Yampa river flows
*From Green River in Jensen Utah flows to approximate Flaming Gorge Release in June
*These flows also assume the entirety of the LTRP release occurs in the month of June

*W1 is a dry year, W2 is a average year, W3 is a wet year
Table EnviroFlows(Years,HydrologicScenarios) Enviromental Flow Release For Each Year and Hydrologic Scenario
          W1                    W2            W3
Y1        167147.11        287623.14        473652.89
Y2        167147.11        287623.14        473652.89
Y3        167147.11        287623.14        473652.89
Y4        167147.11        287623.14        473652.89
Y5        167147.11        287623.14        473652.89;


SCALARS

*Maximum outflow possible in one month. Does not consideer using the spillway
         MaxFlowOut  Maximum Flow Out In One Month (Ac-ft)   /511736/

*Maximum F.G. storage s.t.  1 to 10% exceedance can be routed at anytime
         MaxStore Maximum Water Storage in F.G. Reservoir (Ac-ft) /3086976/

*Minimum F.G. storage set midway between rated hydropower storage and minimum hydropower storage
         MinStore Minimum Water Storage in F.G. Reservoir (Ac-ft)/545757.5/

*Setting Intial Storage In Reservoir For Model, I arbitrarily chose this value
*It corresponds to a reservoir elevation of 6009.27 ft which may be a bit high
*in reality for january. Model results are likely sensitive to this value

*$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
         IntStrg Intial Reservoir Storage of F.G. Reservoir (Ac-ft) /2617726.50/
*$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$2$$$$$$$$


*Total Monthly Flow Release Over the 5 year period. Estimate at first by setting
*Zero then gradually increase

*$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$2$$$$$$$$
 TotRelease Total Volume of Water Released Over Model Period /7270874.141/;
*$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$2$$$$$$$$


*3. Define Variables
VARIABLES
         Env(Years) Enviromental flows
         Yenv number of years LTRP flows were met
         X(Loc,Months) volume of water flowing out of Dam or Stored in Reservoir;


*3a. Define Select Variables as Binary
BINARY VARIABLES
       Env;


*3b. Define Positive Variables
POSITIVE VARIABLES
         X;

*4. COMBINE variables and data in equations
EQUATIONS
*Binary Constraints
         TotalEnv used to sum the number of times enviromental flows are met

*Note do not need to set lower bound of Env to 0 and upper to 1
*These are GAMS defaults for binary variables and therefore do not need to be specified with a
*Constraint

*Enviromental Flow Constraint if Env = 1
         Enviro1 year 1 enviro flow
         Enviro2 year 2 enviro flow
         Enviro3 year 3 enviro flow
         Enviro4 year 4 enviro flow
         Enviro5 year 5 enviro flow

*F.G. Flow and Storage Constraints

*This equaiton will be set later to determine maximum and minimum bounds of Water to be
*Released over a five year period. This is my maximumize flows to Lake Powell Constraint

*#####################################################################################
   TotalOut used to sum total outflows from F.G. over the model period
*####################################################################################

     MMinStore(Months) used to check minimum storage is met for each month
     MMaxStore(Months) used to check maximum storgage is not surpassed in each month
     MMaxFlowOut(Months) used to check that maximum outflow is not surpassed in any year
     Hydro(Months) used for hydropower constraints
     BF(Months)    used baseflow constraints
*Conservation of Mass Constraints;

     IResMB used to require conservation of mass in the first timestep
     ResMB(Months) used to require conservation of mass in the following time steps;


*$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
*Constraint Equations
*$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

*Function being maximized in this model, Sum # of years LTRP flows are met
*   TotalEnv.. Yenv =E= Env('Y1')+Env('Y2')+Env('Y3')+Env('Y4')+Env('Y5');
     TotalEnv.. Yenv =E= SUM(Years,Env(Years));

*Equation relying on set Lake Powell Release Volume
TotalOut.. SUM((Months),X('Dam',Months))=G= TotRelease;

*Flow is always less than bypass tunnel and spillway capacity
     MMaxFlowOut(Months).. X('Dam',Months) =L= MaxFlowOut;

*Flow is always greater than hydropower constraints
      Hydro(Months).. X('Dam',Months) =G= HydroPower(Months);

*Flow is always greater than baseflow constraints, ColoradoPikeMinnow Summer Base Flows are built into BaseFlows
     BF(Months).. X('Dam',Months)=G= BaseFlows(Months);

*Minimum storage constraint. Corresponds to reservoir elevation midway between rated hydropower
*Elevation and minimum hydropower elevation needed for hydropower
         MMinStore(Months).. X('Res',Months) =G= MinStore;

*Maximum storage constraint. Corresponds to
         MMaxStore(Months).. X('Res',Months)=L= MaxStore;

*3.) Define Enviromental MIP LTRP Flow
*When this contraint is satisified Enviromental flows are met, I am fairly sure
*Multiplying the EnviroFlows parameter by the binary Env Variable will allow the model
*Flexibility in choosing to trying to meet enviromental flows or using hydropower
*constraint in June
          Enviro1.. X('Dam','M6')=G= Env('Y1')*EnviroFlows('Y1','W3');
          Enviro2.. X('Dam','M18')=G= Env('Y2')*EnviroFlows('Y2','W3');
          Enviro3.. X('Dam','M30')=G= Env('Y3')*EnviroFlows('Y3','W3');
          Enviro4.. X('Dam','M42')=G= Env('Y4')*EnviroFlows('Y4','W3');
          Enviro5.. X('Dam','M54')=G= Env('Y5')*EnviroFlows('Y5','W3');

*4.) Define Minimum allowable total flow to Lake Powell for 5 year period
*Note: I am going to start this constraint extremely low and then increment to see
*when it binds, and finally when it causes the model to become unfeasible
*This will be difficult for determininigs mixes of wet, dry, avg years
*I believe intial storage volume will heavily influence this constraint aswell

*3.) Define Massbalance Equations
*Intial Reservoir Mass Balance,
IResMB.. X('Res','M1')=E= FlowIn('M1')+IntStrg-X('Dam','M1');

* Following timesteps reservoir mass balance
ResMB(Months)$(ORD(Months)ge 2 ).. X('Res',Months)=E= FlowIn(Months)+X('Res',Months-1)-X('Dam',Months) ;




*5. DEFINE the MODEL from the Equations
MODEL FlamingGorge /ALL/;
         option solslack = 1;

*6. Solve the Model as an MIP
SOLVE FlamingGorge USING MIP MAXIMIZING Yenv;

*7. Dump File to Excel Workbook
Execute_Unload "SemesterProj.gdx";
* Dump the gdx file to an Excel workbook
Execute "gdx2xls SemesterProj.gdx"
* To open the GDX file in the GAMS IDE, select File => Open.
* In the Open window, set Filetype to .gdx and select the file.







