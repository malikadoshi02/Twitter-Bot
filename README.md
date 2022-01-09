

import sys
import time
import simple_twit

# Project 04 Exercises
    
    # Exercise 1 - Get and print 10 tweets from your home timeline
    
    # Exercise 2 - Get and print 10 tweets from another user's timeline
    
    # Exercise 3 - Post 1 tweet to your timeline.
    
    # Exercise 4 - Post 1 media tweet to your timeline.
    
    

def main():
    # This call to simple_twit.create_api will create the api object that
    # Tweepy needs in order to make authenticated requests to Twitter's API.
    # Do not remove or change this function call.
    # Pass the variable "api" holding this Tweepy API object as the first
    # argument to simple_twit functions.
    api = simple_twit.create_api()
    simple_twit.version()

    print()

    x = simple_twit.send_tweet(api, "Hi")
    print(type(x))

    y = simple_twit.send_media_tweet(api, "Hey", "mag-field_1024.jpg")
    print(type(y))

    theytweets = simple_twit.get_user_timeline (api, "business", 10)
    for t in theytweets:
        print(t.id)
        print(type (t.user))
        print(t.author.name)
        print(t.user.name)
        print(t.full_text)
        print()
    
    mytweets = simple_twit.get_home_timeline (api, 10)
    print(len(mytweets))
    print(type(mytweets))
    print(type(mytweets[0]))
    print()
    for t in mytweets:
        print(t.id)
        print(type (t.user))
        print(t.author.name)
        print(t.user.name)
        print(t.full_text)
        print()
    
        
    # YOUR BOT CODE BEGINS HERE
    while True:
        list_phrases = ["Make your bed", "Do a 15 min workout", "Drink water",
                    "Get some work done; try to be productive :)",
                    "Make sure your sitting up straight", "Drink some more water and get a snack :)",
                    "Walk around a little", "Get some mental rest and have a goodnight's sleep", "Are you still up?",
                    "It's really late. Home you are getting that REM with good dreams", "stretch",
                    "I hope you slept well", "I guess the early bird catches the worm"]
        for i in range(0, len(list_phrases)):
            res = simple_twit.send_tweet(api, list_phrases[i])
            print(type(res))
            time.sleep(7200)
            i+=1
   
        
    
    

    # end def main()

if __name__ == "__main__":
       main()

