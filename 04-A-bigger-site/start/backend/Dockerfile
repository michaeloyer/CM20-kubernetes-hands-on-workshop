FROM mcr.microsoft.com/dotnet/core/sdk:3.1-alpine AS build


WORKDIR /src

COPY backend.csproj .

RUN dotnet restore

COPY . .
RUN dotnet build -c Release
RUN dotnet publish -c Release -o /app

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-alpine

ENV ASPNETCORE_URLS http://+:5000
EXPOSE 5000

WORKDIR /app

COPY --from=build /app .


CMD ["dotnet", "backend.dll"]
