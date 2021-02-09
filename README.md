Extract SF36 GOLMEPSA Codes

USE [SSD_GOLMePsA]
GO 

WITH Max_ver AS
(
SELECT 
 *
FROM (SELECT
    ROW_NUMBER() OVER(PARTITION BY PatientStudyID, VisitDate, VisitNumber, AppointmentType 
          ORDER BY DateCreated DESC, PatientStudyID,
          VisitDate, VisitNumber) AS rownum, ID, PatientStudyID, VisitNumber, VisitDate, AppointmentType, DateCreated
          FROM [SSD_GOLMePsA].[dbo].[tblAppointment]) AS A
		  WHERE rownum = 1
)

SELECT 

	   CAST (B.[PatientStudyID] AS INT) AS PatientStudyID
      ,CASE 
      		WHEN B.VisitNumber = '1 - SCR' THEN 1
      		WHEN B.VisitNumber = '2 - BSL' THEN 2
			 WHEN B.VisitNumber = '3 - WK 4' THEN 3
      		WHEN B.VisitNumber = '4 - WK 8' THEN 4
			WHEN B.VisitNumber = '5 - WK 12' THEN 5
      		WHEN B.VisitNumber = '6 - WK 16' THEN 6
			WHEN B.VisitNumber = '7 - WK 20' THEN 7
      		WHEN B.VisitNumber = '8 - WK 24' THEN 8
      		WHEN B.VisitNumber = '9 - WK 28' THEN 9
      		WHEN B.VisitNumber = '10 - WK 36' THEN 10
      		WHEN B.VisitNumber = '11- WK 52' THEN 11
      		WHEN B.VisitNumber = '98 - Ex' THEN 98
      		WHEN B.VisitNumber = '99 - W' THEN 99
      		      		
			ELSE NULL END AS VisitNumber
	
	  ,B.[VisitDate]
      ,B.[AppointmentType]
   
      ,C.[Question1]
      ,C.[Question2]
      ,C.[Question3a]
      ,C.[Question3b]
      ,C.[Question3c]
      ,C.[Question3d]
      ,C.[Question3e]
      ,C.[Question3f]
      ,C.[Question3g]
      ,C.[Question3h]
      ,C.[Question3i]
      ,C.[Question3j]
      ,C.[Question4a]
      ,C.[Question4b]
      ,C.[Question4c]
      ,C.[Question4d]
      ,C.[Question5a]
      ,C.[Question5b]
      ,C.[Question5c]
      ,C.[Question6]
      ,C.[Question7]
      ,C.[Question8]
      ,C.[Question9a]
      ,C.[Question9b]
      ,C.[Question9c]
      ,C.[Question9d]
      ,C.[Question9e]
      ,C.[Question9f]
      ,C.[Question9g]
      ,C.[Question9h]
      ,C.[Question9i]
      ,C.[Question10]
      ,C.[Question11a]
      ,C.[Question11b]
      ,C.[Question11c]
     
  FROM 
  Max_ver AS A LEFT JOIN [SSD_GOLMePsA].[dbo].[tblAppointment] AS B ON A.ID = B.ID RIGHT JOIN 
  [SSD_GOLMePsA].[dbo].[tblPatientSF36] AS C ON B.ID = C.AppointmentID
  
  WHERE B.AppointmentType = 'Patient'
  
  ORDER BY [PatientStudyID], [VisitNumber], VisitDate, AppointmentType



