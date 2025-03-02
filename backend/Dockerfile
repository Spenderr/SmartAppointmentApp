# Base image
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS base
WORKDIR /app
EXPOSE 80

# SDK image for build
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src
COPY ["SmartAppointmentSystem.csproj", "."]
RUN dotnet restore "SmartAppointmentSystem.csproj"
COPY . .
RUN dotnet build "SmartAppointmentSystem.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "SmartAppointmentSystem.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "SmartAppointmentSystem.dll"]
