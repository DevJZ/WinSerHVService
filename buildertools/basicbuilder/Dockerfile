ARG tagarg=3.5-windowsservercore-1709
FROM microsoft/dotnet-framework:${tagarg} AS installednuget

ADD https://dist.nuget.org/win-x86-commandline/v4.4.1/nuget.exe C:\\nuget\\v4.4.1\\nuget.exe
RUN SETX /M NUGET441_BIN_PaTH "C:\nuget\v4.4.1"
RUN SETX /M Path "%Path%;%NUGET441_BIN_PaTH%"

FROM installednuget AS msbuild15
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\\msbuild15\\vs_buildtools.exe
RUN C:\msbuild15\vs_buildtools.exe --add Microsoft.Component.MSBuild --add Microsoft.VisualStudio.Component.CoreBuildTools --add Microsoft.VisualStudio.Component.Roslyn.Compiler \
--add Microsoft.VisualStudio.Component.NuGet.BuildTools --add Microsoft.Net.Component.3.5.DeveloperTools --add Microsoft.Net.Component.4.TargetingPack --add Microsoft.Net.Component.4.5.TargetingPack \
--add Microsoft.Net.Component.4.5.1.TargetingPack --add Microsoft.Net.Component.4.5.2.TargetingPack --add Microsoft.Net.Component.4.6.TargetingPack --add Microsoft.Net.Component.4.6.1.TargetingPack \
--add Microsoft.Net.Component.4.6.2.TargetingPack --add Microsoft.Net.Component.4.7.TargetingPack --layout C:\msbuild15\ --lang en-US --passive --wait

RUN powershell Import-PfxCertificate -FilePath C:\msbuild15\certificates\manifestCounterSignCertificates.p12 -CertStoreLocation Cert:\LocalMachine\Root
RUN powershell Import-PfxCertificate -FilePath C:\msbuild15\certificates\manifestSignCertificates.p12 -CertStoreLocation Cert:\LocalMachine\Root
RUN powershell Import-PfxCertificate -FilePath C:\msbuild15\certificates\vs_installer_opc.SignCertificates.p12 -CertStoreLocation Cert:\LocalMachine\Root

RUN C:\msbuild15\vs_setup.exe --noweb --passive --norestart --wait 
RUN powershell Remove-Item C:\msbuild15 -Recurse -Force

RUN SETX /M BuildTools_COMMON7_Path "C:\Program Files (x86)\Microsoft Visual Studio\2017\BuildTools\Common7"
RUN SETX /M BuildTools_TOOL_Path "C:\Program Files (x86)\Microsoft Visual Studio\2017\BuildTools\Common7\Tools"
RUN SETX /M MSBuild_Bin_Path "C:\Program Files (x86)\Microsoft Visual Studio\2017\BuildTools\MSBuild\15.0\Bin"
RUN SETX /M Path "%Path%;%BuildTools_COMMON7_Path%;%MSBuild_Bin_Path%;%BuildTools_TOOL_Path%"
RUN SETX /M DisableOutOfProcTaskHost 1

CMD ["cmd", "/k vsdevcmd.bat"]