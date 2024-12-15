'''NBA Stats Predictor
CPS - 109
REQUIREMENTS:
For this script to run I have attached the requirements.txt file, I used lxml and pandas for this assignment
Problem:
Inventing my own problem
	The Nba has tasked you to create a software that can predict performance for players (points, assists, rebounds) to show
 on tv channel overlays while games are live. This can be done manually by inputting player scores into your python script, 
 but this will not work when you need up to date data instantly, and you need data for EVERY NBA player so that there is no 
 confusion when finding predictions. For the “prediction” model, you will need to find the mean of the players stats in the 
 regular season, then the mean of the players stats in the last 5 games. For more up to date predictions the last 5 games should 
 be weighted higher in the final prediction than the regular season stats. 

	Problems you will face: Since the data should already be stored and be up to date, you will need to scrape this data off 
 of a website that holds this data for you. This can be done by importing a library that is in python called “Pandas”. Use Pandas 
 documentation to effectively learn how you can pull the data from this website and implement it into your script. Other than 
 learning a new python library, this should be a simple task.

	Make sure to showcase effective error handling and make sure to utilize everything you have learned in CPS 109 and more.


How I Solved The Problem
	This problem was solved in these steps: First Created the function that scrapes both of my website urls, doing it this way 
 I can call my function whenever a url needs to be scraped, making it more effective since I have 2 urls. Next, I noticed that 
 in order to get the data of the last 5 games, I would need a new link for each player I am trying to search. This part was very 
 difficult for me as I did not know how to effectively accomplish this. After going through what I already knew, and documentation 
 and resources on Pandas, I decided to splice the user inputted name of the player and implement it to a new link each time a player 
 is searched for. Pandas is not fully new to me, but a lot of what I used couldn't be done without the documentation.I could do this 
 since I noticed in a certain part of the link, the only thing that changed was the first 5 letters of the players surname, and the 
 first 2 letters of their first name. This was possible with pythons .split function along with splices the player name that I split.
 Next for the most important parts of the code, searching for the players data in both links. I did this in 2 different functions, one 
 for the regular season and the other for the last 5 games. In the regular season link I first had to find the name of the player in a 
 very large data table. One thing to note is that standardizing  names throughout the code will help to avoid error (with the use of
 .lower, .strip, etc). Next I had to select all the rows in the data table where the player column matches the player name inputted 
 by the user (.loc[] in pandas helped me select the rows/columns that I needed in the data table. Then when I retrieve the data I need,
 I convert it into numeric values so there are no issues processing the mean of each of the stats. Next I do the same for the last 5 
 games url, but here the link is case sensitive to the player, therefore I did not need to look for the player name. Next I created a 
 simple “predictor” function that weighs the last 5 games of the player at a value of 0.70(70%) and regular season at 0.30(30%). 
 I used .index to iterate over the labels I needed in the data table (this would refer to points, assists, total rebounds) since I 
 need the average of all three of those stats separately and not together as one number. Lastly the numbers for the stats are rounded 
 to 2 decimal places and returned. Finally I constructed the main function that makes the final code work together. The input from the 
 user is added as a name in the input.txt file, and then the youtube will have the predicted stats.


	This was a great but tough learning experience for me as I knew the basics of Pandas before starting, but not all, so most of 
 the coding process was just trying to figure out what the errors were in my code and how I could fix them. A lot of this was looking 
 through python and Pandas documentation and using trial and error based on the usable functions listed in each document. Pandas 
 documentation was helpful as it had examples and showed me how to implement what i needed into my code.

	What I can improve: The code I've written is relatively simple apart from the fact I used the Pandas library, but for complexity
 I can add more things. I plan on adding a double-double predictor to this code in the future. This was too difficult for me to accomplish
 without any further external help since I would need to iterate through 5 different stats columns and then check for a 2 digit number in
 at least 2 of the stats. This was out of my comfort zone for this assignment as the deadline was closing and I did not have enough time 
 to learn how to do this or get it done.


* SMALL PROBLEM, DOES NOT WORK IN OFF SEASON (NO LAST 5 GAME LIVE STATS)*
'''
