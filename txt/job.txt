@echo off
chcp 1251 > NUL
call restart.bat v82 10 no > "restart.txt" 2>&1
call restart.bat v83 10 yes >> "restart.txt" 2>&1