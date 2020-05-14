#Import base image ms windows server core
FROM mcr.microsoft.com/windows/servercore

#Create a working dir to run server.exe
WORKDIR  /serverApp

#Copy MyServer.exe to curre
COPY MyServer.exe /serverApp

#Create a dest to store all dll. 
ENV dest Windows/System32

#Add in the required dependencies for MyServer.exe
#MSVCP140.dll
#ADD https://download.microsoft.com/download/9/3/F/93FCF1E7-E6A4-478B-96E7-D4B285925B00/vc_redist.x86.exe /vc_redist.x86.exe
#RUN Powershell.exe -Command Start-Process c:\vc_redist.x86.exe -ArgumentList '/quiet' -Wait

RUN Powershell.exe -Command \
$ErrorActionPreference = 'Stop'; \
$ProgressPreference = 'SilentlyContinue'; \
Invoke-WebRequest https://download.microsoft.com/download/9/3/F/93FCF1E7-E6A4-478B-96E7-D4B285925B00/vc_redist.x86.exe \
-OutFile 'c:\vc_redist.x86.exe' ; \
Start-Process c:\vc_redist.x86.exe -ArgumentList '/passive' \
-RedirectStandardOutput 'c:\Windows\System32' -Wait ; \
Remove-Item c:\vc_redist.x86.exe -Force

#expose port for communication 
EXPOSE 3456

#RUN Command prompt
ENTRYPOINT ["cmd"]