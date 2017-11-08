FROM microsoft/dotnet-framework:3.5

ADD "https://download.microsoft.com/download/E/E/D/EEDF18A8-4AED-4CE0-BEBE-70A83094FC5A/BuildTools_Full.exe" C:\\Downloads\\msbuild14tools_full.exe
RUN C:\Downloads\msbuild14tools_full.exe /Silent /Full

RUN powershell Invoke-WebRequest -Uri "https://download.microsoft.com/download/9/E/6/9E63300C-0941-4B45-A0EC-0008F96DD480/NDP471-KB4033342-x86-x64-AllOS-ENU.exe" -OutFile dotnet-framework-installer.exe & \
    .\dotnet-framework-installer.exe /q & \ 
    del .\dotnet-framework-installer.exe
    
RUN powershell Invoke-WebRequest -Uri "https://download.microsoft.com/download/9/0/1/901B684B-659E-4CBD-BEC8-B3F06967C2E7/NDP471-DevPack-ENU.exe" -OutFile NDP471-DevPack-ENU.exe & \
    .\NDP471-DevPack-ENU.exe /q /norestart & \
    del .\NDP471-DevPack-ENU.exe