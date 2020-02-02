FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["lnd2020.csproj", "lnd2020/"]
RUN dotnet restore "lnd2020/lnd2020.csproj"
COPY . ./lnd2020
WORKDIR "/src/lnd2020"
RUN dotnet build "lnd2020.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "lnd2020.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "lnd2020.dll"]
