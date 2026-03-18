# ---------- Build stage ----------
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS builder
WORKDIR /usr/src/app

# Copy csproj and restore dependencies
COPY hello-world-dotnet.csproj .
RUN dotnet restore

# Copy source and build
COPY . .
RUN dotnet publish -c Release -o /app/publish

# ---------- Runtime stage ----------
FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /usr/src/app

# Copy published output
COPY --from=builder /app/publish .

# ASP.NET Core listens on port 80 inside container
EXPOSE 80

ENTRYPOINT ["dotnet", "hello-world-dotnet.dll"]
``
