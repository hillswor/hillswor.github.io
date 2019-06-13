---
layout: post
title:      "Sportify CLI"
date:       2019-06-13 17:17:30 -0400
permalink:  sportify_cli
---


In deciding the direction to go with my CLI Data Scraper, I wanted to go with something that interested me and was data heavy.  What better to fulfill those two requirements than sports? Once I decided on some kind of sports scraper, the name came to me immediately and I chose to go with Sportify.  Ultimately, I wanted to make an application that provided rosters, statistics, schedules, etc for the four major American sports leagues(NFL, NBA, MLB, NHL).  However, I quickly realized that this was overly ambitious and went well beyond the scope of the project requirements.  I settled on just scraping the MLB site for data but did design my application to be flexible so that I can easily add to it in the future.  In fact, in turned out that simply scraping the names of each MLB team along with the rosters and numbers for each player more than fulfilled the requirements.  It turned out that sports are on the extreme end of data collection and there are almost endless possibilities to what could be added to my application.  

I started by figuring out how I wanted Sportify to flow.  If I were to have multiple leagues, I would have a greeting and list out each league to let the user choose which one they wanted information in.  However, for the current version of the application I decided on having a welcome menu that lists all the MLB teams and asks the user which team they would like information on. 

![](https://i.imgur.com/2S2N75B.png)

I also wanted maintain separation of concerns and ensure that the code for my user interface only handles that aspect and has no responsibility for scraping data or putting that data into presentable form.  Maintaining separation of concerns is important to give the application flexibility if I decide to expand it in the future.  To do so, I created three classes each in their own directory: CLI, MLBteams, and MLBscraper.  All three of these classes inherit from a separate sportify module that requires the environment file so I can share dependencies among all the classes without reusing the same code.  

![](https://i.imgur.com/hLhab0c.png)
![](https://i.imgur.com/oQ0hXuo.png)
![](https://i.imgur.com/b6p0YN6.png)

The first menu is created using a scraper and then transmitting that data to the MLBteams class to make that data presentable.  There is a base url that listed all the teams along with their team site urls.  This was a perfect starting point for my scraper branch out from so I saved it as a class variable.  The teams are scraped from that root url and pushed into an empty array using the teams instance method for the MLBscraper class.  Likewise, each team's unique url is also scraped and saved into an empty array using the team_urls instance method.

![](https://i.imgur.com/pHO7pOW.png)

I then compile the teams so that they can be accessed through the CLI in the MLBteams class.  I combine them by using the zip method on both the team array and team_url array returned by a new instance of the MLBscraper class.  When I zip them together, I save each team as a hash with a team_name key and a team_url key.  These hashes are then sorted alphabetically via the team name.

![](https://i.imgur.com/OI9foU9.png)

The CLI class then initializes a new instance of the MLBteams class and iterates over each team for the main menu.

![](https://i.imgur.com/RFtED7D.png)

This takes us to collecting and interpreting the input from the user.  I did want to provide a way to exit the application from each menu so it has to decide whether the input is picking a specific team, requesting to exit or is invalid.  I did this using a conditional statement.

![](https://i.imgur.com/sfvtcEn.png)
![](https://i.imgur.com/oWEbiuV.png)
![](https://i.imgur.com/RxswNAd.png)
![](https://i.imgur.com/hk055vR.png)

If the user's input is valid and they pick a team, they are then sent to the team_menu method in the CLI class that gives the user three new options.

![](https://i.imgur.com/aSvonb6.png)
![](https://i.imgur.com/wCLOYWW.png)

This menu requires that we once again validate the user input.  In this case, since the input options are far more limited, I decided to use a case statement instead of a conditional statement.  The case statement reads much cleaner.

![](https://i.imgur.com/EsubkOV.png)

If the user chooses the active roster option, the CLI class will then call on it's MLBteams instance which will call on it's MLBscraper instance to provide player names and numbers.

![](https://i.imgur.com/pW6adry.png)
![](https://i.imgur.com/l4qFCqg.png)
![](https://i.imgur.com/rKIkwkL.png)

The major hurdle to accessing the roster was getting to a separate url.  That url was able to be scraped from team_url that was scraped from the @@root_url.

![](https://i.imgur.com/eTICtUJ.png)

There was a slight hiccup in obtaining the roster url's because three of the thirty teams followed a different pattern.  While I would prefer to have done it differently, the most expedient option at this point was for me to use a conditional statement within the scraper.  The player names and numbers also had to be zipped together similar to how I did the team names and team url's.    Ultimately, this leads us to the end goal of the app which is listing the roster of each MLB team.

![](https://i.imgur.com/cxNmLy7.png)
