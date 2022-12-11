FROM mcr.microsoft.com/dotnet/runtime:6.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["Snake Game/Snake Game.csproj", "Snake Game/"]
RUN dotnet restore "Snake Game/Snake Game.csproj"
COPY . .
WORKDIR "/src/Snake Game"
RUN dotnet build "Snake Game.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Snake Game.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Snake Game.dll"]
