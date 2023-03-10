FROM mcr.microsoft.com/dotnet/sdk:8.0.100-preview.1-alpine3.17-amd64 AS build
## Install GE Root Certificate (Only needed if built locally)
ADD /BuildRootCertificates/ge_external_root_2.1.crt /usr/local/share/ca-certificates/ge_external_root_2.1.crt
RUN chmod 644 /usr/local/share/ca-certificates/ge_external_root_2.1.crt && update-ca-certificates

RUN dotnet nuget --version
RUN dotnet --version

WORKDIR /src
COPY ["Directory.Packages.props", "."]
COPY ["nuget.config", "."]
COPY ["Source/src/spc/SpcService/SpcService.csproj", "Source/src/spc/SpcService/"]

RUN dotnet restore -v diag "Source/src/spc/SpcService/SpcService.csproj"
#RUN ls /root/.nuget/packages
