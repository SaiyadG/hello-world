USE [SSD_GOLMePsA]
GO 

SELECT 
	   [PatientStudyID] AS [Patient Study ID]
      ,B.[AppointmentType] AS [Workbook]
      ,C.[SOCCode] AS [SOC Code]
      ,CASE WHEN C.DateOfOnset IS NULL THEN C.[DateOfOnset_actual] 
            WHEN C.[DateOfOnset] IS NOT NULL THEN [DateofOnset] ELSE [DateOfOnset] END AS [Date of Onset]
      ,C.[Severity]
      ,C.[Expected]
      ,C.[SeriousAdverseEvent] AS [Serious Adverse Event]
      ,CASE WHEN [SeriousAdverseEvent] = 'No' THEN 'not req.' ELSE C.[SeriousAdverseEventReported] END AS [Serious Adverse Event Reported]
      ,C.[Description]
      ,C.[Status]
      ,CASE WHEN [Status] = 'Ongoing' THEN 'not applicable' 
            WHEN C.DateResolved IS NULL THEN C.[DateOResolved_actual] 
            WHEN C.[DateResolved] IS NOT NULL THEN [DateResolved] ELSE C.[DateResolved] END AS [Date Resolved]
      ,C.[StudyRelated] AS [Study Related] 
      ,C.[Reviewer]
      ,B.[DocID] AS [Sharepoint DOC ID]
      
  FROM 
  [SSD_GOLMePsA].[dbo].[tblAppointment] AS B LEFT JOIN 
  [SSD_GOLMePsA].[dbo].[tblAdverseEvents] AS C ON B.ID = C.AppointmentID
  
  WHERE PatientStudyID != '100000' AND AppointmentType = 'Adverse Events' 
  
  ORDER BY CAST ([PatientStudyID] AS INT)
  
--ALTER TABLE  [SSD_GOLMePsA].[dbo].[tblAdverseEvents]
 -- ALTER COLUMN [DateofOnset] nvarchar (50) NULL;
 --ADD [Date Resolved] nvarchar(50) NULL;

