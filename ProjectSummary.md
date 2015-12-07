# Automated Bartender #

This project started out with a simple idea, create a device that could be placed in a home or anyplace where people would like to have a drink, but where this is no bartender to make them (although it could also serve as a tool to assist bartenders).  Through many design changes and careful considerations this idea has been materialized in the device that you see below:

<a href='http://imgur.com/exWBtlU'><img src='http://i.imgur.com/exWBtlU.jpg' title='Hosted by imgur.com' /></a>

# Features #

1) 6 bottle holders

2) 3 for different types of alcohol and 3 for different mixers

3) Easy keypad system for ordering drinks

4) Drinks of different strengths (1, 2, or 3 shots)

5) Ability to pour shots without mixing other drinks

6) Ability to pour only mixers if desired

7) Each drink is designed to fill up a solo cup

# How it Works #

There are two different codes I have made for controlling which drink is poured.  One is just a simple two number code for each drink possibility that has to be memorized (or read from a sheet) by  the user.  The other involves a 3 button combination where the first button specifies which alcohol to use, the second button specifies how many shots of that alcohol (up to 3), and the third button is which mixer to use.  When the desired drink combination is input, a servo connected to a valve is opened for a set amount of time to let a certain amount of liquid to flow into the cup.

# Video #

<a href='http://www.youtube.com/watch?feature=player_embedded&v=GtYL8eGFU4k' target='_blank'><img src='http://img.youtube.com/vi/GtYL8eGFU4k/0.jpg' width='425' height=344 /></a>

# Challenges #

During the creation of this project there were numerous challenges that came up, but the two major ones that took the most work to overcome were coming up with a design and stopping the leaks.  The first idea for the design was a box where all the bottles would placed upside down into and the valves and servos would be hidden inside with the tubes all going to a single location with the cup below.  I also had an idea to have a box of clear plastic around the bottles that I was going to have a thermoelectric cooler chill the bottles, but upon testing it, I found that the thermoelectric cooler did not have enough energy to chill six bottles.  The other problem with this design was that the box to house the valves and servos would have had to have been very large in order to allow everything to fit.  The last thing I wanted was to have a touchscreen instead of the 12 button keypad but with that I would have needed an Arduino Mega which together would have cost another $100. So I decided that the $4 keypad would have to do.  The problem of the leaks took a little less time to fix but was very important to the project.  Part of the problem was that if the liquor pourers were pushed in all the way the bottle would leak. I had to make sure to only push them in part way to get rid of this problem.  Another place where the leaks occurred was between the metal of the pourer and the plastic.  To fix this I applied silicone sealant all around the base.  Another thing I had to do to keep the bottles from leaking was to make sure the tubing fit perfectly inside each other and created a tight seal.  Although I did a lot to get rid of the leaks unfortunately I was not able to get rid of the leak with the broken valve because that would have involved replacing it and I did not have another valve.