@echo off
chcp 1251 > NUL
setlocal enabledelayedexpansion

rem =--параметры запуска--=
SET VER1C=%1
SET WAITING=%2
SET STOPONLY=%3

rem =--объявление переменных--=
SET V82SERVICE=WTabletServicePro
SET V83SERVICE=AdobeARMservice

echo =========================================
echo ============ SCRIPT START ===============
echo =========================================
echo %date% %time%  Restarting job start
echo "PARAMS: "
echo "VER1C=%VER1C%" 
echo "WAITING=%WAITING%"
echo "STOPONLY=%STOPONLY%"

IF "%VER1C%"=="v82" (
	SET VERACTION=!V82SERVICE!
)
IF "%VER1C%"=="v83" (
	SET VERACTION=!V83SERVICE!
)


echo %date% %time% Stoping... %VERACTION%
net stop %VERACTION%

IF "%STOPONLY%"=="yes" (goto finish)

:startserv
echo %date% %time% Starting... %VERACTION%
net start %VERACTION%


:finish
echo %date% %time%  Finish
echo ============ SCRIPT STOP ================
echo =========================================

 
