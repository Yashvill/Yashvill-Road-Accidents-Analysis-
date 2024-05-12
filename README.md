Step-By-Step Approach:
● Data Cleaning
● Data Modeling
● Data processing
● Data Visualization
Data cleaning:
Finding Nulls Values and Duplicates. In this Data set Almost there are No Null Values
And in Some Attributes Values are Wrong Like in Accident_Severity there is Fatal and
Fetal,So we replaced ‘Fetal’ with ‘Fatal’. By doing this almost cleaning part was Done
Data Modeling:
Created another Table Which is Known as Calendar Table, So we can do Time
Intelligence Function Like it's better to create the Calendar Table, in this Date are
Distinct

In order Build Connection We have to Drag the “Accident Data” from Data to “Date”
from Calendar ( One to Many Relationship)

Data Processing:
We do some Grouping in the records like in “Weather_Conditions” they are different
types of classifying are there and can't show all of them, So make it group
Same goes to the “Vehicle_Type”

We take Some New measure by Using DAX formulas Like :
CY Casualties = TOTALYTD(SUM(Data[Number_of_Casualties]),'calander'[Date])
CY Accidents Count = TOTALYTD(count(Data[Accident Date]),'calander'[Date])
PY Accidents =
CALCULATE(COUNT(Data[Accident_Index]),SAMEPERIODLASTYEAR('calander'[Date]))
PY Casualties =
CALCULATE(SUM(Data[Number_of_Casualties]),SAMEPERIODLASTYEAR('calander'[Date]))
MaxCasualtiesLocation =
VAR MaxCasualties =
MAXX (
SUMMARIZE (
'data',
'data'[Local_Authority_(District)],
"TotalCasualties", SUM('data'[Number_of_Casualties])
),
[TotalCasualties]
)
RETURN
SELECTCOLUMNS (
FILTER (
SUMMARIZE (
'data',
'data'[Local_Authority_(District)],
"TotalCasualties", SUM('data'[Number_of_Casualties])
),
[TotalCasualties] = MaxCasualties
),
"Location", 'data'[Local_Authority_(District)]
)

Data Visualization:
Adding KPIs to the Dashboards:
MaxCasualtiesLocation: Its Shows the Location Name Where Maximum
Casualties Occurs
Total CY casualties : Total current Casualties And percentage of Casualties
Increased/Decreased compared to Previous year
Total CY Accidents : Total current Accidents And percentage of Accidents
Increased/Decreased compared to Previous year
● Finding Correlations using Graphs:
● Weather Conditions vs. Accident Severity
● Road Surface Conditions vs. Accident Severity
● CY vs PY Casualties
● Speed Vs No.of.Casualties
● Casualties by Urban/Rural
● Casualties by Light Conditions
● Casualties Based on the Vechicle_type

Key findings and Insights:
Its Shows that Maximum Casualties Occurred in “ Birmingham” Using Slicer its shows
the Location based On Accident Severity, Road Type
Total CY casualties: 195.7K and 11.89% percent Casualties Decreased
Total CY Accidents: 144.4K and 11.70% percent Accident Decreased
In Weather Conditions “ Fine” Most Accident Severity Happened
In Road Surface Conditions “Dry” Most Accident Severity Happened
At Speed of “ 30 km per hr “ has More No.of.Casualties ( Unexpected)
Casualties by Urban : 162K and Rural: 256K
Casualties by Light : 113K and Darkness:305K
