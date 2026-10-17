#Score Board

## Purpose Of the web application section 

** This is where the score board that tracks the user's hacking progress within the OWASP juice-shop** 



## Documentation 

I have taken refernce from OWASP Juice Shop documentation in order to follow through this challenge [Findng the Score Board](https://pwning.owasp-juice.shop/companion-guide/latest/part2/score-board.html).

## Considered Approaches

    * Guessing the URL.
    * Finding the URLs through the source code (main.js).

## Approach - Guessing the URL

Since most web applications follow predictable name schemes for their URLS i have tried several guesses. They are as follows. 

    * scoreboard
    * scoreBoard
    * Scoreboard
    * score-board

I was able to enter the score board by using "score-board" URL. This approach was much faster than inspecting the underlying codebase of the web application.

I chose this approach as my first approach due to low complexity of the objective and predictable naming formats followed by developers when it comes to URLs on a web application. 

## Additional Approaches 

### Aleternative Approach 1 - Scanning through the source code manually.

This approach is extremely time consuming and exhausting. the chance of finding the necessary information within a proper time is very slim. 

Necessary routing information can be found in main.js line 3799. 

### Alternative Approach 2 - Most robust approach using ffuf

Rather getting



 