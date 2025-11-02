# Use official .NET SDK image for building
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src

# Copy everything and build the project
COPY . .
RUN dotnet publish -c Release -o /app/out

# Use ASP.NET runtime for final image
FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app/out .

# Expose port (Render will use this)
EXPOSE 8080

# Start the app
ENTRYPOINT ["dotnet", "DalilKalba.dll"]
