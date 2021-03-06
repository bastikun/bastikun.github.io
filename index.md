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

#Google Chrome Freeze randomly
*Type "chrome://settings" in the URL bar, and then click "Advanced"
*Untick "use hardware acceleration when available"
*Go to "chrome://flags"
*Disable "GPU Rasterization"

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
--Check the apps list
dpkg --list
--unsintall
sudo apt-get remove complexshutdown
sudo apt-get --purge remove gimp

# Install Ubuntu Dark Theme
sudo -s
apt install -y gnome-tweaks
apt-get install gnome-tweak-tool
gnome-tweaks

# Skype
sudo apt-get remove skype
sudo apt-get purge skype
sudo apt-get update
wget https://go.skype.com/skypeforlinux-64.deb
sudo dpkg -i skypeforlinux-64.deb
--remove the file
rm skypeforlinux-64.deb
sudo apt-get -f install
--Run multiple account
skype --secondary &
--Update Skype
sudo apt install gdebi-core
wget https://repo.skype.com/latest/skypeforlinux-64.deb
sudo gdebi skypeforlinux-64.deb

#MS Teams
https://packages.microsoft.com/repos/ms-teams/pool/main/t/teams/
wget https://packages.microsoft.com/repos/ms-teams/pool/main/t/teams/teams_1.3.00.5153_amd64.deb
sudo dpkg -i teams_1.3.00.5153_amd64.deb
--Uninstall
dpkg -r teams

# Install Sublime
https://askubuntu.com/questions/828226/how-to-update-sublime-text-3-in-ubuntu-16-04

#Install Remmina RDP
-close
sudo killall remmina
-install
sudo apt-add-repository ppa:remmina-ppa-team/remmina-next
sudo apt update
sudo apt install remmina remmina-plugin-rdp remmina-plugin-secret

# Open System Monitor
gnome-system-monitor

# Maintenance and Tools
sudo apt-get install preload
sudo apt-get clean
sudo apt-get autoremove ->remove any unused packages and dependencies

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
# Install Windows Service
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe "C:\Source\Repos\ProjectName\bin\Debug\My.Service.exe"
# Debug Windows Service
1. Start the Service in services.msc
2. Attached the service in Debug menu VS Studio

# RUN AS
*********************************************
runas /netonly /user:domain\username "C:\Program Files (x86)\Microsoft SQL Server\130\Tools\Binn\ManagementStudio\ssms.exe"
*********************************************

# *** Entity Framework ***
******************************************************************************************
https://coding.abel.nu/2012/03/ef-migrations-command-reference/
--STEPS
1. enable-migrations -projectname:MyProject.data -contexttypename:mycontext
 --For multiple context
 1.1 enable-migrations -projectname:MyProject.data -contexttypename:mycontext -MigrationsDirectory DAL\Context1
2. add-migration -projectname:MyProject.data initialcreate
"The Designer Code for this migration file includes a snapshot of your current Code First model. This snapshot is used to calculate the changes to your model when you scaffold the next migration. If you make additional changes to your model that you want to include in this migration, then you can re-scaffold it by running 'Add-Migration gx' again."
A previous migration called 'gx' was already applied to the target database. If you meant to re-scaffold 'gx', revert it by running 'Update-Database -TargetMigration 201707040736086_initialcreate', then delete '201707060409089_gx.cs' and run 'Add-Migration gx' again.
3. update-database -projectname:MyProject.data
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
******************************************************************************************
	
# *** Boostrap Accordion ***
*********************************************
<div class="wrapper center-block">
<div class="panel-group" id="accordion" role="tablist" aria-multiselectable="true">
@{int headingId = 0; }
@foreach (var user in Model)https://packages.microsoft.com/repos/ms-teams/pool/main/t/teams/
{
headingId += 1;
<div class="panel panel-default">
<div class="panel-heading" role="tab" id="heading@(headingId)">
    <h4 class="panel-title">
	<a class="collapsed" role="button" data-toggle="collapse" data-parent="#accordion" href="#collapse@(headingId)" aria-expanded="false" aria-controls="collapse@(headingId)">
	    <span style="margin-left:20px" ;font-weight: bold;">Title @user.Group</span>
	</a>
    </h4>
</div>
<div id="collapse@(headingId)" class="panel-collapse collapse" role="tabpanel" aria-labelledby="heading@(headingId)">
    <div class="panel-body">
	//// your data here
    </div>
</div>
</div>
}
</div>
</div>
*** CSS ***
.panel-title > a, .panel-title > a:active {
    display: block;
    /*padding: 15px;*/
    color: #555;
    font-size: 16px;
    font-weight: bold;
    text-transform: uppercase;
    letter-spacing: 1px;
    word-spacing: 3px;
    text-decoration: none;
}

.panel-heading a.accordion:before {
    font-family: 'Glyphicons Halflings';
    content: "\e114";
    float: left;
    transition: all 0.5s;
    color: #007CE9;
}

.panel-heading.active a:before {
    -webkit-transform: rotate(180deg);
    -moz-transform: rotate(180deg);
    transform: rotate(180deg);
}
*** JS ***
$('.panel-collapse').on('show.bs.collapse', function () {
 $(this).siblings('.panel-heading').addClass('active');
});

$('.panel-collapse').on('hide.bs.collapse', function () {
$(this).siblings('.panel-heading').removeClass('active');
});

*********************************************
# jQuery
********************************************* 
function loadDropDownProducts() {
      if ('@Model.Products' !== null) {
          var opted = [];
          @foreach (var m in @Model.Products) {
              @:opted.push("@m.ProductCode");
          }
          for (x = 0; x < opted.length; x++) {
              if (opted[x] !== "") {
                  $("#ProductCode_" + x + ' option:selected').text(opted[x]);
                  $("#ProductsName_" + x).val($("#ProductCode_" + x + ' option:selected').text());
              }
              else {
                  $("#ProductCode_" + x).prop('selectedIndex', 0);
                  $("#ProductsName_" + x).val($("#ProductCode_" + x + ' option:selected').text());
              }
          };
      };
  }

-- Match Selector
$('td[name=tcol1]') // matches exactly 'tcol1'
$('td[name^=tcol]') // matches those that begin with 'tcol'
$('td[name$=tcol]') // matches those that end with 'tcol'
$('td[name*=tcol]') // matches those that contain 'tcol'
                                       
*********************************************
# *** SQL Server common commands ***
*********************************************
--SQL Server 2016 13.x
DROP TABLE [IF EXISTS] [database_name.][schema_name.]table_name;
DROP TABLE IF EXISTS dbo.TableName
--SQL Server 2016 13.x
							       
--Describe table
exec sp_columns MyTable
exec sp_fkeys MyTable

--Show SP content
sp_helptext

--Seek SP
select * from  sys.procedures 
where name like '%name_of_proc%'

--Check where SP resided
EXEC sp_msforeachdb 
'if exists(select 1 from [?].sys.objects where name=''siriussp_rsReleaseHolds'')
select ''?'' as FoundInDb from [?].sys.objects where name=''siriussp_rsReleaseHolds'''

--Check All connection Session
SELECT db_name(S.database_id) AS DatabaseName,
        ST.text
FROM   sys.dm_exec_connections AS C
       JOIN sys.dm_exec_sessions AS S ON S.session_id = C.session_id
       OUTER APPLY sys.dm_exec_sql_text(most_recent_sql_handle) AS ST
WHERE  C.session_id >=104;
                                       
--Kill session ID
DECLARE @kill varchar(8000) = '';  
SELECT @kill = @kill + 'kill ' + CONVERT(varchar(5), session_id) + ';'  
FROM sys.dm_exec_sessions
WHERE database_id  = db_id('dbName')
EXEC(@kill);
                                       
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

-- Update two tables
UPDATE A
SET A.NAME = B.NAME
FROM TableNameA A
INNER JOIN TableName B ON A.ID = B.ID
      
--Rename Table
exec sp_rename 'schema.old_table_name', 'new_table_name'
--Rename Column
IF EXISTS(SELECT * FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME='GXFuelCredits' AND COLUMN_NAME='ClaimDate')
BEGIN
   sp_rename 'table_name.old_column_name', 'new_column_name', 'COLUMN';
END
--Add Column

--Rename DB
USE [master];
GO
ALTER DATABASE foo SET SINGLE_USER WITH ROLLBACK IMMEDIATE;
GO
--EXEC sys.sp_renamedb @dbname = N'foo', @newname = N'bar';
ALTER DATABASE foo MODIFY NAME = bar; -- preferred way
GO
ALTER DATABASE bar SET MULTI_USER;

-- Add column
USE [DBName];
GO
SET ANSI_NULLS ON;
GO
SET QUOTED_IDENTIFIER ON;
GO
IF NOT EXISTS(SELECT * FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME='Table' AND COLUMN_NAME='Column')
   ALTER TABLE [dbo].[Table] ADD Column BIT NOT NULL DEFAULT 0
GO
	
-- Copy table
select * into Table_New
FROM Table_Old

-- Copy table with different columns
INSERT INTO TableB (b1, b2, b3)
SELECT a1, a2, a3
FROM   TableA
WHERE <some condition>;

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
 
-- Get the maximum column date in the other table
SELECT T1.Id,ISNULL(T2.AMT,0.0),T2.Date
	FROM Table1 as T1
	left join
	(SELECT Id,Date, AMT, FKey
	 FROM Table2 A
	 WHERE Date = (SELECT max(enddate) FROM Table2 B
			WHERE A.FKey = B.FKey)
			) T2 
	ON T1.Id=T2.FKey

**** Run all SQL files
@ECHO OFF
ECHO Running ALL scripts in DEVELOPMENT ENVIRONMENT
REM SET SQLCMD "C:\Program Files (x86)\Microsoft SQL Server\Client SDK\ODBC\130\Tools\Binn\SQLCMD.EXE"
SET PATH="C:\Users\user\SQL files"
SET SERVER="DEV-ENV"
SET DB="DBName"
SET LOGIN="sa"
SET PASSWORD="saPword"
SET OUTPUT="C:\Temp\OutputLog.txt"
CD %PATH%
ECHO %date% %time% > %OUTPUT%
for %%f in (*.sql) do (
"C:\Program Files\Microsoft SQL Server\110\Tools\Binn\SQLCMD.EXE" /S %SERVER% /d %DB% -U %LOGIN% -P %PASSWORD% -i %%~f >> %OUTPUT%
ECHO FILE : %%~f >> %OUTPUT%
IF ERRORLEVEL == 1 (
ECHO THERE WAS AN ERROR - to file >> %OUTPUT%
ECHO THERE WAS AN ERROR - on screen)
)
ECHO All Scripts ran successfully
pause

**** SP and Function
CREATE PROCEDURE IsValid_SP
@ID INT,
@IsValid BIT OUTPUT
AS
BEGIN
SELECT @IsValid = 1
SELECT @IsValid = [dbo].[VehicleDistanceValid](@ID)
END
GO
**** FUNCTION CALL
CREATE FUNCTION IsValid_FX (@ID int)  RETURNS bit AS 
BEGIN 
DECLARE @Valid bit, @ID int
SET @Valid = 1
IF @ID < 0
 SET @Valid=0
RETURN @Valid
**** CALLING THE SP-FX ****
Declare @Valid bit
EXEC IsValid_SP 2, @VehicleDistanceValid output
SELECT @Valid
								 
**** To speed up query
CREATE PROCEDURE [dbo].[SPName]
(            
    @TenantID INT = null,
    @DateFrom DATETIME,
    @DateTo DATETIME
)
AS
--Add these lines
DECLARE 
    @TenantID1 INT = @TenantID,
    @DateFrom1 DATETIME = @DateFrom,
    @DateTo1 DATETIME = @DateTo
BEGIN
END

*********************************************
.NET
*********************************************
Date Parse: DateTime.ParseExact(booking.BookingDate, "d/M/yyyy h:m:s tt", System.Globalization.CultureInfo.InvariantCulture).ToString("yyyy-MM-dd HH:mm:ss");

**** OAuth2 ****
var body = $"client_id={clientId}&grant_type={grantType}&client_secret={clientSecret}&scope={scope}";
var apiBasePath = System.Configuration.ConfigurationManager.AppSettings["APIBasePath"];
var apiRequest = new APIRequest
{
Data = body,
Method = HttpMethod.POST.ToString(),
URI = $"{apiBasePath}/Authorisation/Connect/Token"
};
var apiAccess = new APIAccess();
var response = apiAccess.GetOAuth2ClientToken(apiRequest);
return response.AccessToken;	  
------------------------------------------------------------------------------------------------------
var uri = new Uri(requestParameters.URI);
HttpWebRequest request = (HttpWebRequest)WebRequest.Create(uri);
request.Method = requestParameters.Method;
request.ContentType = "application/x-www-form-urlencoded";
if (requestParameters.Method != "GET")
{
    using (var requestWriter = new StreamWriter(request.GetRequestStream(), System.Text.Encoding.ASCII))
    {
	requestWriter.Write(requestParameters.Data);
    }
}
try
{
    var response = request.GetResponse() as HttpWebResponse;
    using (Stream responseStream = response.GetResponseStream())
    {
	using (var reader = new StreamReader(responseStream, System.Text.Encoding.UTF8))
	{
	    var json = reader.ReadToEnd();
	    var oAuth2Token = new OAuth2Token();
	    oAuth2Token = JsonConvert.DeserializeObject<OAuth2Token>(json);
	    apiResponse.AccessToken = oAuth2Token.access_token;
	}
    }
    return apiResponse;
}
	  
*********************************************
				     
#REGEX
--Remove numbers and dashes
System.Text.RegularExpressions.Regex.Replace(data, @"[\d-]", string.Empty)
--Email validation
function validateEmail(email) {
    var emailRegex = /[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}/igm;
    return emailRegex.test(email);
}
	  
*** TOOLS ***
AOMEI
https://www.voidtools.com/support/everything/
*************
* Copy website
sudo apt-get install httrack
usage: httrack <space> url

*************
Azure
sudo apt update
sudo apt install strongswan
sudo apt install strongswan-pki libstrongswan-extra-plugins network-manager-strongswan
							   
```
