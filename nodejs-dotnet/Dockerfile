# escape=`
# Use windows server core as a build image, install node.js on it, then copy to nano server.
FROM microsoft/windowsservercore

# Install node.js
SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';"]

RUN iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1')); `
    choco install nodejs -Force -y; `
    refreshenv;

# Create a nano server image with nodejs and dotnet core sdk.
FROM microsoft/dotnet:nanoserver

# Update PATH environment variable
RUN Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Session Manager\Environment' `
    -Name PATH –Value $($env:Path + ';C:\Users\ContainerAdministrator\AppData\Roaming\npm')

COPY --from=0 ["C:/Program Files/nodejs", "/windows/system32"]
