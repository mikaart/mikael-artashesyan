# Blog 3

Welcome to new series of Blogs. **Here** is a quick summary of things I've learned this week.

## My Craigslist script

Being around people who buy and sell cars for living gave me the interest in this project, as its main goal is to find and report on cars that you find yourself interested in. Its functionality resides around scraping the resources of Craigslist (which is not completely in terms complient) and check for cars that fit the right characteristics input by the user such as make, model, price range. These are the main attributes we want in a search, as the whole purpose is to find a car at a price lower than market's average and report on it to a user as soon as possible increasing user chances of scalping a good deal.

### Functionality 


Type triglav.py following keywoards of cars you're looking for. It is important to know that the Python code is written in python3, so it has to be specified unless user is running python3 by default. For example:
```
1. python 3 triglav.py mercedes e350 e500
2. python3 triglav.py bmw m3 m5 m235i e46
```
![Image](https://github.com/mikaart/mikael-artashesyan/blob/master/triglav.input.png)

Program will then prompt for sleep time, which characterizes the time break between scans the program will do in seconds. The shorter the time the more chance you got to find a good deal before anyone else, however it will also report you on it quite often. 

![Image](https://github.com/mikaart/mikael-artashesyan/blob/master/triglav.running.png)

Once this is done, the program goes into scanning the pages of url's provided inside the program itself. These url's can be customly adjusted, but they are usually set to front page of the website with cars tagged under "Posted today". That said, other filters can be enabled as well depending on personal preferences. 


![Image](https://github.com/mikaart/mikael-artashesyan/blob/master/triglav.email.png)

After above steps are completed, program will send an email with matches that it came up with. It creates a report on the name of the ad, price tag, and link to the ad. So far the program does not recognize unique links which is something we'll talk about later.

### What's ahead

There is still work that needs to be done around the script. I wrote down a few things that need to be fixed:
```
1. Recognize repeting ads
2. Format the output in a user-friendly format
3. Integrate phone message instead of email
4. Integrate price scale
```


In the next blog we will talk about libraries this code uses and what solutions to previous problems I've came up with. 




