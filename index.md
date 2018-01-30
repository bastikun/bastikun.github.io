## Welcome to bastikun's reference

```markdown
--------------------------------------------------------------------
## * * * LINUX * * *
--------------------------------------------------------------------
# Crontab
sudo apt-get update
sudo apt-get install cron
sudo gedit /etc/crontab
/var/spool/cron/crontabs
#shutdown daily at 16:30
30 16 * * * /sbin/poweroff # JOB_ID_1 or 30 16 * * * root poweroff

# Install TAR.GZ file
cd Downloads/
tar zxvf anyconnect-predeploy-linux-64-4.3.05017-k9.tar.gz
cd anyconnect-predeploy-linux-64-4.3.05017-k9in/vpn/
sudo ./vpn_install.sh

# Install .DEB file
sudo dpkg -i stride_amd64.deb

# Install Audacity and VLC
sudo apt-get update
sudo apt-get install audacity
sudo apt-get install vlc browser-plugin-vlc

# Install Stride online
sudo sh -c 'echo "deb https://packages.atlassian.com/debian/stride-apt-client $(lsb_release -c -s) main" > /etc/apt/sources.list.d/atlassian-stride.list'
wget -O - https://packages.atlassian.com/api/gpg/key/public | sudo apt-key add -
sudo apt-get update
sudo apt-get install stride

# Install Chromium
sudo apt-get install chromium-browser

# Uninstall
sudo apt-get remove complexshutdown
--------------------------------------------------------------------

--------------------------------------------------------------------
# *** WINDOWS ***
--------------------------------------------------------------------

# IIS
*********************************************
IIS
net stop WAS
net start W3SVC
*********************************************

# Delete Windows Service
tasklist
taskkill /pid #

# RUN AS
*********************************************
runas /netonly /user:domain\username "C:\Program Files (x86)\Microsoft SQL Server\130\Tools\Binn\ManagementStudio\ssms.exe"
*********************************************

# *** Entity Framework ***
******************************************************************************************
https://coding.abel.nu/2012/03/ef-migrations-command-reference/
--steps in EF GXOnline
1. enable-migrations -projectname:gxonline.data -contexttypename:gxcontext
2. add-migration -projectname:gxonline.data initialcreate
"The Designer Code for this migration file includes a snapshot of your current Code First model. This snapshot is used to calculate the changes to your model when you scaffold the next migration. If you make additional changes to your model that you want to include in this migration, then you can re-scaffold it by running 'Add-Migration gx' again."
A previous migration called 'gx' was already applied to the target database. If you meant to re-scaffold 'gx', revert it by running 'Update-Database -TargetMigration 201707040736086_initialcreate', then delete '201707060409089_gx.cs' and run 'Add-Migration gx' again.
3. update-database -projectname:gxonline.data
******************************************************************************************

# *** Boostrap DateTime Picker ***
*********************************************
http://eonasdan.github.io/bootstrap-datetimepicker/Installing
<div class="row">
      <div class="form-horizontal">
          <div class="form-group">
              <label class="col-sm-3 control-label">
                  Date From:
              </label>
              <div class="form-inline">
                  <div class="col-sm-2">
                      <div class="input-group date" id="divStartDate">
                          @Html.TextBoxFor(m => m.StartDate, new { @class = "form-control", autocomplete = "off" })
                          <span class="input-group-addon">
                              <span class="fa fa-calendar"></span>
                          </span>
                      <div>
                </div>
            </div>
        </div>
  </div>
<div>
<script type="text/javascript" src="~/scripts/moment.min.js"></script>
<script type="text/javascript" src="~/scripts/bootstrap-datetimepicker.min.js"></script>
$("#divStartDate, #StartDate").datetimepicker({ format: 'DD-MMM-YYYY' });
*********************************************

# *** SQL Server common commands ***
*********************************************
--Describe table
exec sp_columns MyTable

--Show SP content
sp_helptext

--Seek SP
select * from  sys.procedures 
where name like '%name_of_proc%'

--Check where SP resided
EXEC sp_msforeachdb 
'if exists(select 1 from [?].sys.objects where name=''siriussp_rsReleaseHolds'')
select ''?'' as FoundInDb from [?].sys.objects where name=''siriussp_rsReleaseHolds'''

--Seek content in SP
SELECT ROUTINE_NAME, ROUTINE_DEFINITION
FROM INFORMATION_SCHEMA.ROUTINES 
WHERE ROUTINE_DEFINITION LIKE '%Foo%' 
AND ROUTINE_TYPE='PROCEDURE'

--Dead Locks
  SELECT cntr_value AS NumOfDeadLocks
  FROM sys.dm_os_performance_counters
  WHERE object_name = 'SQLServer:Locks'
  AND counter_name = 'Number of Deadlocks/sec'
  AND instance_name = '_Total'

--Rename DB
USE [master];
GO
ALTER DATABASE foo SET SINGLE_USER WITH ROLLBACK IMMEDIATE;
GO
--EXEC sys.sp_renamedb @dbname = N'foo', @newname = N'bar';
ALTER DATABASE foo MODIFY NAME = bar; -- preferred way
GO
ALTER DATABASE bar SET MULTI_USER;

--Back up table
select * into Table_New
FROM Table_Old

-- DECLARE
declare @ID INT
set @ID=251

-- Having
select ID, count(*) from Table
group by ID
having count(*) > 1

-- Cursor
USE [dbName];
GO
SET ANSI_NULLS ON;
GO
SET QUOTED_IDENTIFIER ON;
GO

IF OBJECT_ID('tempdb..#temp') IS NOT NULL
DROP TABLE #temp
create table #temp 
--create test table
(
  SourceExperienceID int,
  SourceSectionName NVARCHAR(100),
  NewSectionName NVARCHAR(100)
)

--add values to test table
INSERT INTO #temp
SELECT 251, 'Presale', 'Presale_TEST1'

INSERT INTO #temp
SELECT 253, 'Mysection', 'Mysection_TEST1'

--create cursor
DECLARE @SourceExperienceID as INT;
DECLARE @SourceSectionName as NVARCHAR(100);
DECLARE @NewSectionName as NVARCHAR(100);
 
DECLARE @MyCursor as CURSOR;
 
SET @MyCursor = CURSOR FOR
SELECT * FROM #temp
 
OPEN @MyCursor;
FETCH NEXT FROM @MyCursor INTO @SourceExperienceID, @SourceSectionName, @NewSectionName;
 
WHILE @@FETCH_STATUS = 0
BEGIN
  SELECT @SourceExperienceID, @SourceSectionName, @NewSectionName;

  FETCH NEXT FROM @MyCursor INTO @SourceExperienceId, @SourceSectionName, @NewSectionName;
END
 
CLOSE @MyCursor;
DEALLOCATE @MyCursor;

-- CREATE STORED PROCEDURE
USE [dbName];
GO
SET ANSI_NULLS ON;
GO
SET QUOTED_IDENTIFIER ON;
GO
IF EXISTS(SELECT * FROM sys.objects WHERE object_id=OBJECT_ID(N'[dbo].[spName]') AND type IN (N'P', N'PC'))
 DROP PROCEDURE [dbo].spName
GO
CREATE PROCEDURE [dbo].[spName]
AS
  SELECT C.Index, CD.Description
  FROM Category AS C
  JOIN CategoryDescription AS CD ON C.Index = CD.CategoryId
  WHERE IsParent = 1
  ORDER BY CD.CategoryDescription
GO

-- CREATE TABLE
USE [dbName]
GO
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
IF NOT EXISTS(SELECT * FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA = 'dbo' AND TABLE_CATALOG='dbName' AND TABLE_NAME = 'tableName')
BEGIN
  CREATE TABLE [dbo].[tableName](
  	[Index] [int] IDENTITY(1,1) NOT NULL,
  	[DescriptionNumber] [int] NOT NULL UNIQUE,
  	[Description] [varchar](500) NULL,
   CONSTRAINT [pk_tableName] PRIMARY KEY CLUSTERED 
  (
  	[Index] ASC
  )WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
  ) ON [PRIMARY]
END
GO

-- Copy table with different columns
INSERT INTO TableB (b1, b2, b3)
SELECT a1, a2, a3
FROM   TableA
WHERE <some condition>;
*********************************************

```
