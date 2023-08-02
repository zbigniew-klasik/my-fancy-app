FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src

COPY *.csproj ./
RUN dotnet restore

COPY * ./
RUN dotnet publish -c release -o published --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app

COPY --from=build /src/published ./
ENTRYPOINT ["dotnet", "MyFancyService.dll"]