## 🍓 The Karma++ Services Api

#### By Asia Kaplanyan

#### An API specifically designed to be used in conjunction with the Karmaplusplus.Solution project in this repository

## Technologies Used

* C#
* .NET
* ASP.Net
* Entity Framework
* MySql

## Description

An API providing information for free services entered by Karma++ users.  

## How To Run This Project

### Install Tools

Install the tools that are introduced in [this series of lessons on LearnHowToProgram.com](https://www.learnhowtoprogram.com/c-and-net/getting-started-with-c).

If you have not already, install the `dotnet-ef` tool by running the following command in your terminal:

```
dotnet tool install --global dotnet-ef --version 6.0.0
```

### Set Up and Run Project

1. Clone this repo.
2. Open the terminal and navigate to this project's production directory called "Karmaplusplus".
3. Within the production directory "Karmaplusplus", create two new files: `appsettings.json` and `appsettings.Development.json`.
4. Within `appsettings.json`, put in the following code. Make sure to replacing the `uid` and `pwd` values in the MySQL database connection string with your own username and password for MySQL.

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Port=3306;database=karmaplusplus_api;uid=YOUR-USER-NAME-HERE;pwd=YOUR-PASSWORD-HERE;"
  }
}
```

5. Within `appsettings.Development.json`, add the following code:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Trace",
      "Microsoft.AspNetCore": "Information",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  }
}
```
6. Create the database using the migrations in the Karma++ API project. Open your shell (e.g., Terminal or GitBash) to the production directory "Karmaplusplus", and run `dotnet ef database update`. You may need to run this command for each of the branches in this repo. 
    - To optionally create a migration, run the command `dotnet ef migrations add MigrationName` where `MigrationName` is your custom name for the migration in UpperCamelCase. To learn more about migrations, visit the LHTP lesson [Code First Development and Migrations](https://www.learnhowtoprogram.com/c-and-net-part-time/many-to-many-relationships/code-first-development-and-migrations).
7. Within the production directory "Karmaplusplus", run `dotnet watch run --launch-profile "Karmaplusplus-Production"` in the command line to start the project in production mode with a watcher. 
8. To optionally further build out this project in development mode, start the project with `dotnet watch run` in the production directory "Karmaplusplus".
9. Use your program of choice to make API calls. In your API calls, use the domain _http://localhost:5000_. Keep reading to learn about all of the available endpoints.

## Testing the API Endpoints

You are welcome to test this API via [Postman](https://www.postman.com/) or [curl](https://curl.se/).

### Available Endpoints

```
GET https://localhost:7225/api/Services/
GET http://localhost:7225/api/Services/{id}
POST http://localhost:7225/api/Services/
PUT http://localhost:7225/api/Services/{id}
DELETE http://localhost:7225/api/Services/{id}
```

Note: `{id}` is a variable and it should be replaced with the id number of the service you want to GET, PUT, or DELETE.

#### Optional Query String Parameters for GET Request

GET requests to `http://localhost:5000/api/services/` can optionally include query strings to filter or search backyards. For example:

| Parameter   | Type        |  Required    | Description |
| ----------- | ----------- | -----------  | ----------- |
| service     | String      | not required | Returns services with a matching service value |




The following query will return all services of "lesson":

```
GET http://localhost:5000/api/services?service=lesson
```


#### Additional Requirements for POST Request

When making a POST request to `http://localhost:5000/api/services/`, you need to include a **body**. Here's an example body in JSON:

```json
{
  "service": "lesson",
  "description": "Free English lessons",
  "email": "english.lessons@gmail.com",
  "zip code": "98052"
}
```

#### Additional Requirements for PUT Request

When making a PUT request to `http://localhost:5000/api/services/{id}`, you need to include a **body** that includes the service's `serviceId` property. Here's an example body in JSON:

```json
{
  "serviceId": 1,
  "service": "lesson",
  "description": "Free English lessons",
  "email": "english.lessons@gmail.com",
  "zip code": "98052"
}
```

And here's the PUT request we would send the previous body to:

```
http://localhost:5000/api/services/1
```

Notice that the value of `serviceId` needs to match the id number in the URL. In this example, they are both 1.

## Known Bugs

* No known issues.

## License
Enjoy the site!

[MIT](https://github.com/git/git-scm.com/blob/main/MIT-LICENSE.txt)

Copyright (c) 2023 Asia Kaplanyan