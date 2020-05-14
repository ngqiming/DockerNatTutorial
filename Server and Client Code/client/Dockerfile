FROM mcr.microsoft.com/windows/servercore

WORKDIR /clientApp 

COPY MyClient.exe /clientApp

ENV dest Windows/System32

RUN Powershell.exe -Command \
$ErrorActionPreference = 'Stop'; \
$ProgressPreference = 'SilentlyContinue'; \
Invoke-WebRequest https://download.microsoft.com/download/9/3/F/93FCF1E7-E6A4-478B-96E7-D4B285925B00/vc_redist.x86.exe \
-OutFile 'c:\vc_redist.x86.exe' ; \
Start-Process c:\vc_redist.x86.exe -ArgumentList '/quiet' -RedirectStandardOutput 'c:\Windows\System32' -Wait ; \
Remove-Item c:\vc_redist.x86.exe -Force 

EXPOSE 3456

ENTRYPOINT [ "cmd" ]
