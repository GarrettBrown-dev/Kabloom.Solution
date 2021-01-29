# _Kabloom: The Ultimate Plant Tracker!_

<p align="center">
    <br>
        <a href="https://github.com/ebezjian">
        <img style="border-radius: 100%; height: 50px; width: auto" src="https://avatars.githubusercontent.com/u/49379604?s=460&u=28a995564e8709eb7ba2d8f7a4e0165562a37cd3&v=4">
    </a>
        <br>
        <a href="https://github.com/SarahGilbert064">
        <img style="border-radius: 100%; height: 50px; width: auto" src="https://avatars.githubusercontent.com/u/72630313?s=460&u=12fb92750dc134aacbae9ad21fc39442a9dc19ee&v=4">
    </a>
        <br>
        <a href="https://github.com/grand-scheme">
        <img style="border-radius: 100%; height: 50px; width: auto" src="https://avatars.githubusercontent.com/u/72650879?s=460&u=8ecf4ccb9ac936e6108d17da3e725ad2bae185a2&v=4">
    </a>
    <br>
        <a href="https://github.com/GarrettBrown-dev">
        <img style="border-radius: 100%; height: 50px; width: auto" src="https://avatars1.githubusercontent.com/u/69095640?s=460&u=eefe493b85312d332eedc271ee24a39d586446ae&v=4">
    </a>
</p>

<p align="center">
  <small>Last Updated: January 28th, 2021</small>
</p>

-----

## 🧑‍💻 Contributors

| Name                                                            | GitHub Profile                                          |
| --------------------------------------------------------------- | ------------------------------------------------------- |
| [Ellie Lambert](https://www.linkedin.com/in/eleanor-p-lambert/) | [ebezjian](https://github.com/ebezjian)                 |
| [Sarah Gilbert](https://www.linkedin.com/in/sarahgilbertpdx/)   | [SarahGilbert064](https://github.com/SarahGilbert064)   |
| [Shannon Grantski](https://www.linkedin.com/in/grand-scheme/)   | [grand-scheme](https://github.com/grand-scheme)         |
| [Garrett Brown](https://www.linkedin.com/in/garrett-brown-d/)   | [GarrettBrown-dev](https://github.com/GarrettBrown-dev) |

## Description

Welcome to Kabloom! This application was created for all plant lovers and growers. Once on the home page, the user will be able to register an account with Kabloom for future use. Once the user has logged into their personal account, they will gain access to the Trefle API, which will provide them with 1,000's of plants to (one day) add to their garden!

## Stretch Goals

- Allow user to add specific plants from the Trefle API to their account to personalize their "garden".
- Allow users to add information to each plant in their garden, such as watering times, date of planting and harvest dates.
- Create another database to hold each user's plants information such as watering times, date of planting, and harvest dates.
- Allow the user to search through the "Locations" database and add their region/area's garden shops to their account.

---

# 💾 Installation Requirements

Software Requirements

- An internet browser of your choice
- A code editor
- .NET Core
- MySQL
- MySQL Workbench
- Postman
- API keys for Trefle and FourSquare -- instructions for these can be found below. 

## 🖥️ Copying the Project to your Local System

### Downloading or Cloning:

#### Cloning:
- Using a preferred terminal (such as GitBash), navigate to the folder where you want to store this project.
- Input the command: `$ git clone https://github.com/SarahGilbert064/Kabloom.Solution`
  - If you would like to rename this directory, use: `$ git clone https://github.com/SarahGilbert064/Kabloom.Solution NAME-OF-YOUR-CHOICE`

#### Downloading:
- On the GitHub website for this repository, click the green **CODE** button near the top of the page.
- Click _Download ZIP_.
- Save this file to your computer.
- Extract this ZIP.
-----
## Updating and Creating Necessary Files

### AppSettings.JSON
\
In the file `KabloomClient\appsettings.json`, you will find the following code:
```JSON
{
    "Logging": {
        "LogLevel": {
            "Default": "Warning"
        }
    },

    "AllowedHosts": "*",
    "ConnectionStrings": {
        "DefaultConnection": "Server=localhost;Port=3306;database=kabloomTrefleApi;uid=USER;pwd=PASSWORD;"
    }
}
```
Replace "USER" and "PASSWORD" with the username and password associated with your local MySql settings. You may also need to update `Server=localhost` or `Port=3306` to match your local settings.


### EnvironmentVariables.CS, and Finding Your Keys
\
This project utilizes connections to APIs provided by [Trefle](https://trefle.io/) and [FourSquare](https://foursquare.com/). Each of these products will require unique credentials, which you will need to acquire before running this product.

1. To sign up for a Trefle API Key, select **Get Started** on [their website](https://trefle.io/). Once you fully create and complete your account, you will receive an API key. Keep this handy.

2. To sign up for a FourSquare API key, sign up at their [Developer's website](https://developer.foursquare.com/) with the link to **Places API**. This is a 'freemium' product -- while you should not need to spend any money to use this API for the scope of this project, you may need to provide a credit card number to prevent query abuses. You will receive a Client ID and a Client Secret. Keep both of these handy.

3. In the folder `KabloomClient\Models`, create a file called `EnvironmentVariables.cs` In this file, input the following code:

```C#
namespace KabloomClient.Models
{
    public static class EnvironmentVariables
    {
        public static string ApiKey = "YOUR-TREFLE-KEY-HERE";
        public static string FourSquareId = "YOUR-FOURSQUARE-CLIENT-ID-HERE";
        public static string FourSquareSecret = "YOUR-FOURSQUARE-CLIENT-SECRET-HERE";
    }
}
```

4. Insert your Trefle Key, FourSquare Client ID, and FourSquare Client Secret in the labeled places.
----
## Launching the Project

In your terminal, navigate to `KabloomClient`, and run the following commands. Wait for each command to complete before moving to the next step.
```
$ dotnet restore
$ dotnet ef database update
$ dotnet build
$ dotnet run
```

In your browser, navigate to _https://localhost:5001_. This is the project!


## 🛰️ API Documentation

We decided to sign up and obtain an Api Key for the free Trefle API, which gives you access to over 20,000 plants worldwide. Please check out their documentation at [Trefle: A Global Plant API](https://trefle.io/)

#### Sample JSON Response

```JSON
{
    "id": 678281,
    "common-name": "Evergreen Oak",
    "scientific_name": "Quercus rotundifolia",
    "family_common_name": "Beech Family",
}
```

We are also utilizing the [FourSquare Places API](https://developer.foursquare.com/docs/places-api/), which allows for access to data for millions of businesses around the world. We are filtering based on the business _categoryId_ for Garden Center, and query by city name.

#### Sample JSON response:
```JSON
{ // For location query: Seattle, WA //
    "meta": {
        "code": 200,
        "requestId": " [ ... ] "
    },
    "response": {
        "venues": [
            {
                "id": "5cd87b45947c05002cd5dcbf",
                "name": "Fred Meyer Garden Center",
                "location": {
                    [ ... ]
                    "formattedAddress": [
                        "915 NW 45th St",
                        "Seattle, WA 98107",
                        "United States"
                    ]
                },
                [ ... ]
            },
            [ ... ]
        ]
        [ ... ]
    }
}

```

# 🪲 Bugs / Issues

- Launching the project sometimes reroutes to _https://localhost:5001/index.html_ instead of _https://localhost:5001/_. index.html is not a valid page.
- The registration page occasionally (but not always) re-routes to a broken page after creating a new account.

# ☎️ Support / Contact Details

- Please feel free to reach out to:

| Name             | Engineer/Designer         |
| ---------------- | ------------------------- |
| Sarah Gilbert    | sarahgilbert064@gmail.com |
| Garrett Brown    | gman9mm@live.com          |
| Shannon Grantski | grantski@pm.me            |
| Ellie Lambert    | ebezjian@gmail.com        |

# ⚙️ Technologies Used

<details>
  <summary>Expand Tech/tools</summary>

- [Bootstrap Components](https://getbootstrap.com/docs/3.3/components/)
- C#
- JavaScript
- Razor
- Entity Framework Core
- Identity
- MySql
- MySql Workbench
- Postman
- VSCode
- Webflow
- Trefle
- FourSquare

</details>

# ©️ License & Copyright

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Copyright (c) 2021 **_{Ellie Lambert}_**, **_{Sarah Gilbert}_**, **_{Shannon Grantski}_** and **_{Garrett Brown}_**
