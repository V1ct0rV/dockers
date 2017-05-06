# escape=`
FROM microsoft/windowsservercore

# Configure default shell
SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';"]

# Download and extract nginx
RUN Invoke-WebRequest -Uri http://nginx.org/download/nginx-1.13.0.zip -OutFile 'c:\nginx.zip'
RUN Expand-Archive c:\nginx.zip -Dest c:\nginx

WORKDIR C:\\nginx\\nginx-1.13.0
CMD [".\\nginx"]