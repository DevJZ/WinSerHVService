FROM microsoft/dotnet-framework:3.5

RUN powershell Invoke-WebRequest -Uri "https://download.microsoft.com/download/D/D/3/DD35CC25-6E9C-484B-A746-C5BE0C923290/NDP47-KB3186497-x86-x64-AllOS-ENU.exe" -OutFile dotnet-framework-installer.exe & \
    .\dotnet-framework-installer.exe /q & \ 
    del .\dotnet-framework-installer.exe

ADD https://download.microsoft.com/download/9/0/1/901B684B-659E-4CBD-BEC8-B3F06967C2E7/NDP471-DevPack-ENU.exe C:\\Downloads\\NDP471-DevPack-ENU.exe

ADD https://download.microsoft.com/download/E/E/D/EEDF18A8-4AED-4CE0-BEBE-70A83094FC5A/BuildTools_Full.exe C:\\Downloads\\msbuild14tools_full.exe
RUN "C:\\Downloads\\NDP471-DevPack-ENU.exe" /q /norestart

RUN C:\\Downloads\\msbuild14tools_full.exe /Silent /Full
RUN powershell del c:\Downloads\*.*
