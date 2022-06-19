#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["aspEx2/aspEx2.csproj", "aspEx2/"]
RUN dotnet restore "aspEx2/aspEx2.csproj"
COPY . .
WORKDIR "/src/aspEx2"
RUN dotnet build "aspEx2.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "aspEx2.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "aspEx2.dll"]