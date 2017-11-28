#Build Stage
FROM microsoft/aspnetcore-build:2 AS build-env

WORKDIR /api

COPY api.csproj .
RUN dotnet restore

COPY . .
RUN dotnet publish -c Release -o /publish

# Runtime Image Stage
FROM microsoft/aspnetcore:2 AS runtime-env

WORKDIR /publish

COPY --from=build-env /publish .

ENTRYPOINT [ "dotnet", "api.dll" ]