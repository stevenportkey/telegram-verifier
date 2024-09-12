FROM mcr.microsoft.com/dotnet/sdk:7.0.306-jammy-amd64 AS base

ARG PROJ=TelegramServer.Auth.HttpApi.Host

WORKDIR /app

COPY [".", "/app"]

RUN set -x \
    && dotnet publish src/${PROJ}/${PROJ}.csproj -c Release -o /tmp/build

FROM mcr.microsoft.com/dotnet/sdk:7.0.306-jammy-amd64

WORKDIR /app

COPY --from=base /tmp/build .

ENTRYPOINT ["dotnet", "/app/TelegramServer.Auth.HttpApi.Host.dll"]