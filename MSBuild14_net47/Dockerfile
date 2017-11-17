FROM microsoft/windowsservercore as basemsbuild

ADD "https://download.microsoft.com/download/E/E/D/EEDF18A8-4AED-4CE0-BEBE-70A83094FC5A/BuildTools_Full.exe" C:\\Downloads\\msbuild14tools_full.exe
RUN C:\Downloads\msbuild14tools_full.exe /Silent /Full & \
    del C:\Downloads\msbuild14tools_full.exe
    
RUN powershell Invoke-WebRequest -Uri "https://download.microsoft.com/download/9/0/1/901B684B-659E-4CBD-BEC8-B3F06967C2E7/NDP471-DevPack-ENU.exe" -OutFile NDP471-DevPack-ENU.exe & \
    .\NDP471-DevPack-ENU.exe /q /norestart & \
    del .\NDP471-DevPack-ENU.exe



FROM basemsbuild as msbuild14

RUN SETX /M MSBUILD14_BIN   "C:\Program Files (x86)\MSBuild\14.0\bin"
RUN SETX /M Path "%Path%;%MSBUILD14_BIN%"