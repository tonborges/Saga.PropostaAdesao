FROM mcr.microsoft.com/dotnet/runtime:6.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["Saga.PropostaAdesao.EntrevistaEnfermeiro.Driving.Commands/Saga.PropostaAdesao.EntrevistaEnfermeiro.Driving.Commands.csproj", "Saga.PropostaAdesao.EntrevistaEnfermeiro.Driving.Commands/"]
RUN dotnet restore "Saga.PropostaAdesao.EntrevistaEnfermeiro.Driving.Commands/Saga.PropostaAdesao.EntrevistaEnfermeiro.Driving.Commands.csproj"
COPY . .
WORKDIR "/src/Saga.PropostaAdesao.EntrevistaEnfermeiro.Driving.Commands"
RUN dotnet build "Saga.PropostaAdesao.EntrevistaEnfermeiro.Driving.Commands.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Saga.PropostaAdesao.EntrevistaEnfermeiro.Driving.Commands.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Saga.PropostaAdesao.EntrevistaEnfermeiro.Driving.Commands.dll"]
