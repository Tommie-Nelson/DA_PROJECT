--- DATA CLEANING---
alter table pancreatic_cancer
add PDAC Varchar(50);

Alter table pancreatic_cancer
add BENIGN_HEPATOBILIARY_DISEASE Varchar(50),
NO_PANCREATIC_CANCER Varchar(50);

alter table pancreatic_cancer
add Diagnoses Varchar(50)

update pancreatic_cancer
set Diagnoses = (Case when Diagnosis = 1 THEN 'Control'
				when Diagnosis = 2 THEN 'Benign Hepatobiliary Disease'
				when Diagnosis = 3 THEN 'PDAC' END)

update pancreatic_cancer
set PDAC = (Case when Diagnoses = 'PDAC' THEN 'PDAC' END)

update pancreatic_cancer
	set 
		BENIGN_HEPATOBILIARY_DISEASE = 
		(Case when Diagnoses = 'BENIGN HEPATOBILIARY DISEASE' THEN 'BENIGN HEPATOBILIARY DISEASE' END);

Update Pancreatic_Cancer
	set 
		No_Pancreatic_Cancer = (Case when Diagnoses = 'Control' THEN 'No Pancreatic Cancer' END)



---DATASET EXPLORATION-----

----Average Age of Patients---
Select AVG(Age) as AVG_Age
from Pancreatic_Cancer

---Average Age of partients with PDAC---
Select AVG(AGE) AS AVG_AGE
FROM Pancreatic_Cancer
where Diagnoses = 'PDAC'

----Number of samples in each patient cohort---
select patient_cohort, 
count (*) as NumberOfSamples
from Pancreatic_Cancer
Group by patient_cohort

----Number of Male and female patients in the dataset---
Select 
		sex, 
		count (*) as Gender_Count
		from Pancreatic_Cancer
		Group by sex

----Count Of People Groups----
Select COUNT (Diagnoses) as Healthy_Population
from Pancreatic_Cancer
where Diagnoses = 'Control';

Select COUNT (Diagnoses) as Non_Cancerous_Population
from Pancreatic_Cancer
where Diagnoses = 'Benign Hepatobiliary Disease';

Select COUNT (Diagnoses) as Cancerous_Population
from Pancreatic_Cancer
where Diagnoses = 'PDAC';

---Average Biomarker Levels for Each diagnosis---
Select 
		diagnoses, AVG (Plasma_CA19_9) AS AVG_CA919_9,
		AVG (LYVE1) AS AVG_LYVE1,
		AVG (REG1B) AS AVG_REG1B,
		AVG (TFF1) AS AVG_TFF1,
		AVG (Creatinine) as AVG_Creatinine
		from Pancreatic_Cancer
		Group By diagnoses


----Average biomarker Levels For Each Cohorts----- 

Select 
		distinct patient_cohort, diagnoses,
		count (*) as Cohort_count, 
		AVG (Plasma_CA19_9) AS AVG_CA919_9,
		AVG (LYVE1) AS AVG_LYVE1,
		AVG (REG1B) AS AVG_REG1B,
		AVG (TFF1) AS AVG_TFF1,
		AVG (Creatinine) as AVG_Creatinine
		from Pancreatic_Cancer
		Group By patient_cohort, diagnoses
		Order by patient_cohort


----Exploring biomarker levels for the PDAC different stages----
Select 
		Stage , AVG(LYVE1) AS AVG_LYVE1,
		AVG (Plasma_CA19_9) AS AVG_CA919_9,
		AVG (REG1B) AS AVG_REG1B,
		AVG (TFF1) AS AVG_TFF1
		FROM Pancreatic_Cancer
		where diagnoses = 'PDAC'
		Group by stage

----Identifying patients with the highest plasma CA19_9---
SELECT 
		Top 10 
		Sample_ID,
		sex,
		plasma_CA19_9
		from Pancreatic_Cancer
		Order By plasma_CA19_9 desc

