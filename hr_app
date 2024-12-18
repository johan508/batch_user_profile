@ECHO OFF
REM User profile management system
REM by Han Zhang
REM 1895.01.01
REM Suppose your company's name is JMS, you can change any name as you like
REM Put this .bat file into D drive. Otherwise you'll need to change the path underneath
REM Default password is 1234, but you can change it
REM ------------------------------------------------------------------------------------


ECHO **********************************************
ECHO                WELCOME TO JMS!
ECHO **********************************************
PAUSE

:pass
SET /p pass=Please enter password:
IF NOT %pass%==1234 GOTO pass

IF EXIST JMS\HR (GOTO menu) ELSE (md JMS\HR)
IF EXIST JMS\Developing (GOTO menu) ELSE (md JMS\Developing)
IF EXIST JMS\Marketing (GOTO menu) ELSE (md JMS\Marketing)
IF EXIST JMS\Finance (GOTO menu) ELSE (md JMS\Finance)
IF EXIST JMS\IT (GOTO menu) ELSE (md JMS\IT)

:menu
CLS
ECHO ********************************************
ECHO 1. Create a profile
ECHO 2. Delete a profile
ECHO 3. Search an employee
ECHO 4. Show all employees' profile
ECHO 5. I hate my boss! (Delete all users' data)
ECHO 6. Exit
ECHO ********************************************
SET /p var=Please enter your option:
IF %var%==1 GOTO create
IF %var%==2 GOTO delete
IF %var%==3 GOTO search
IF %var%==4 GOTO show
IF %var%==5 GOTO delAll
IF %var%==6 GOTO end
ECHO INVALID INPUT!
GOTO menu


:create
CLS
SETLOCAL
SET /p name=Enter employee's name (LastName_FirstName):
SET /p age=Enter employee's age:
SET /p number=Enter phone number:
SET /p dep=Enter department name (HR, Developing, Marketing, Finance, IT):
ECHO Name:%name%>d:\JMS\%dep%\%name%.txt
ECHO Age:%age%>>d:\JMS\%dep%\%name%.txt
ECHO Contact number:%number%>>d:\JMS\%dep%\%name%.txt
ECHO Department:%dep%>>d:\JMS\%dep%\%name%.txt
ECHO %name%'S PROFILE WAS CREATED SUCCESSFULLY!
PAUSE
ENDLOCAL
GOTO menu


:delete
CLS
SETLOCAL
SET /p delName=Enter the name of employee:
FOR /f "delims=" %%b in ('dir /s /a-d /b %delName%.txt') do (
            if exist "%%b" del %%b 
	    ECHO %delName% WAS DELETED.
            PAUSE
            GOTO menu)
PAUSE
ENDLOCAL
GOTO menu


:search
CLS
SETLOCAL
SET /p searName=Enter the name of employee:
for /f "delims=" %%b in ('dir /s /a-d /b %searName%.txt') do (
            if exist "%%b" TYPE %%b
	    PAUSE
	    GOTO menu)
PAUSE
ENDLOCAL
GOTO menu

:show
CLS
SETLOCAL
FOR /r d:\JMS\ %%g IN (*.txt) DO (echo %%g)
PAUSE
ENDLOCAL
GOTO menu

:delAll
rd JMS /s /q
ECHO Your boss will cry now!
PAUSE
EXIT


:end
ECHO Thanks for using our HR system! Bye!
PAUSE
