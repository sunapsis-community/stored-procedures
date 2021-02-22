# stored-procedures
Custom stored procedures for sunapsis

Stored procedures can be used to create custom tasks in sunapsis under Programmability in the data base.  This process is described in the Tech Workshop and details can most recently be found on page 12-13 and module 9 of the 2019 manual and is found in Happy Fox here: https://sunapsis.happyfox.com/kb/article/1303-technical-workshop-materials/.

Please note: 
1. All custom tasks should be tagged with the suffix C (not a T for the sunapsis built in tasks!)
2. Because these tasks are configured to be run with the data feed, you must grant execute permissions in order for your custom component to be run (one time only when creating the stored procedure--can also be added when altering the procedure in case you forget).
    Example:  GRANT EXECUTE ON dbo.checklistTaskExtensionC015 TO [InternationalServices-User];
              GO
3. All custom tasks must be added to codeChecklistOfficeTaskType to be configurable for use in checklists.
4. Recommendation: Name the custom task with your institution identifier to clearly mark it as a custom task. For example: task C015 is your institution's 15th custom task.  It involves tagging a SEVIS transfer record and the description inserted into codeChecklistOfficeTaskType starts with your institution identifier "UCD Transfer Release Status"
  Sample insert statement:  
    --INSERT INTO dbo.codeChecklistOfficeTaskType (
	   code
	   , description
	   ,groupDesc
	   ,documentation
    )
    VALUES (
	   N'C015', N'NAME of TASK HERE','','HTML DESCRIPTION HERE--use built in sunapsis tasks for Examples'
    );
