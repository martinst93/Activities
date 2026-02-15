# Activities Project Repository

This app is built using .Net 9 and React 19

# Running the project

1. .Net SDK v9
2. NodeJS (at least version 18+ or 20+)
3. git (to be able to clone the project repo)

Once you have these then you can do the following: 
1. Clone the project in a User folder on your computer by running:

```bash
# you will of course need git installed to run this
git clone https://github.com/martinst93/Activities.git
cd Reactivities
```
2. Restore the packages by running:

```bash
# From the solution folder (Reactivities)
dotnet restore

# Change directory to client to run the npm install.  Only necessary if you want to run
# the react app in development mode using the Vite dev server
cd client
npm install
```

3.  Run the command to use the DB from docker 
```# docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=Password@1" -p 1433:1433 --name sqlserver -d mcr.microsoft.com/mssql/server:2022-latest```

If you do not want to use docker the uncoment the other DefaultConnection in the appsettings.Development.json. When you start the service the DB will be created and populated.
``#"DefaultConnection": "Server=localhost;Database=reactivities;Trusted_Connection=True;TrustServerCertificate=True"``


4. If you wish for the photo upload to work create a file called appsettings.json in the Reactivities/API folder and copy/paste the following configuration.

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "CloudinarySettings": {
    "CloudName": "REPLACEME",
    "ApiKey": "REPLACEME",
    "ApiSecret": "REPLACEME"
  },
  "AllowedHosts": "*"
}
```

5. You can then run the app and browse to it locally by running:

```bash
# run this from the API folder in one terminal/command prompt
cd API
dotnet run

# open another terminal/command prompt tab and run the following
cd client
npm run dev

```

7. You can then browse to the app on https://localhost:3000 and login with either of the test users:

    email: bob@test.com or tom@test.com or jane@test.com
    
    password: Pa$$w0rd
	
NOTE: if you are unale to login with any of these account you need to run the following querry in the db UPDATE AspNetUsers SET EmailConfirmed = 1;