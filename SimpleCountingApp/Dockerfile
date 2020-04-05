FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env
WORKDIR /app
COPY SimpleCounting.sln ./
COPY ./SimpleCounting ./SimpleCounting

RUN dotnet restore SimpleCounting.sln
RUN dotnet publish SimpleCounting\SimpleCounting.csproj --framework netcoreapp3.1 -c Release -o out /p:Version=1.0.0

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build-env /app/out .

ENTRYPOINT ["dotnet", "SimpleCounting.dll"]

