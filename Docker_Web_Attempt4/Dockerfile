
# Base Image from Microsoft
FROM mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:5.0-buster-slim AS build
WORKDIR /src
COPY ["Docker_Web_Attempt4.csproj", ""]
RUN dotnet restore "./Docker_Web_Attempt4.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "Docker_Web_Attempt4.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Docker_Web_Attempt4.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Docker_Web_Attempt4.dll"]