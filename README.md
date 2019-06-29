# dice_game

So my friend introduced me to a dice game that goes as follows: 

Everyone sits in a circle and takes turns rolling two dice. 

- The number you roll is the score you get
- You can roll as many times as you want and you get to add the score of each roll to your total score
- If you roll doubles, you get 2x what you roll BUT you have to roll again 
- However, if you roll a 1 on either die you get a 0 for your turn and it is over
- If you roll two 1's your total score goes to 0, unless you're already at 0 in which case it goes to -50
- If you roll and your total score = 100 you go back down to 0
- Once one player gets above 100 everyone Venmo's her (winner's score - their score) * 5 cents 


I did terribly in this game which was mostly luck, but now I'm curious if there's a dominant strategy to it. I plan to try a few simple strategies using Monte Carlo simulations in this project. 


## Starting Simple

Let's just look at the expected value per toss. We can get at this by just doing 1,000,000 simulations of 2 random dice throws (random int of 1 to 6) and then applying the rules over these. Note: This does not include the case of snake eyes on a 0 resulting in -50. 

As you can see the most common outcome is 0 with over 30% of tosses ending up in a 0. (This makes sense because your probability of rolling a 1 is 1 - 5/6^2, or 30.55%) There are some less frequent very large values (16, 20, 24) due to the doubles rule. Overall the expected value per toss is 6.67.

<img width="416" alt="Screen Shot 2019-06-25 at 9 52 51 PM" src="https://user-images.githubusercontent.com/38504767/60147602-b0943380-9793-11e9-9f69-f67ab20b69c6.png">                      <img width="198" alt="Screen Shot 2019-06-25 at 9 54 44 PM" src="https://user-images.githubusercontent.com/38504767/60147650-ea653a00-9793-11e9-819c-21fe839f0a13.png">


## Never Stopping Your Turn

Next we'll check the simplest strategy: Rolling until you either hit a 1 and end your turn or get above 100 and win the game. 

With an average of 62.31 turns needed to win on a straight run, I defintiely don't recommend this strategy. It is iteresting to note that youre expected to win within 5 turns 7.97% of the time and under 10 turns 13.71% of the time which honestly isn't awful. Normally games last around 6 rounds so it's not as bad as it may seem at first. Plus if there are a lot of people playing in the game it may be worth it in some cases.  

<img width="432" alt="Screen Shot 2019-06-25 at 10 10 07 PM" src="https://user-images.githubusercontent.com/38504767/60148268-02d65400-9796-11e9-9b56-a4e65ddcc517.png">


## Rolling Only Once 

Next we'll check the strategy of only rolling one time and ending your turn. With an average of 23.37 turns to win the game, this strategy seems much better than never stopping your turn. However, the game is only won if you're the first person to score over 100. With this strategy, you only win in 5 turns 0.07% of the time and under 10 turns 2.86% of the time. 

<img width="406" alt="Screen Shot 2019-06-29 at 11 02 47 AM" src="https://user-images.githubusercontent.com/38504767/60385954-84133c80-9a5d-11e9-97dc-6b9b6e3f0003.png">


## Rolling Multiple Times a Turn

Most people who play the game will roll a few times and then stop once they're comfortable. For this sections lets look at strategies where you roll n times per turn and then end the turn. Below are the distributions of turns needed to win for a few multi-toss turns. They look generally the same except as the number of rolls per turn increases, the right tail grows longer.  

<img width="908" alt="Screen Shot 2019-06-29 at 11 14 40 AM" src="https://user-images.githubusercontent.com/38504767/60386119-2b44a380-9a5f-11e9-8844-7d2398e2c597.png">


<img width="399" alt="Screen Shot 2019-06-28 at 8 34 43 PM" src="https://user-images.githubusercontent.com/38504767/60386126-3ef00a00-9a5f-11e9-8f7f-36de0e4b202a.png">   <img width="389" alt="Screen Shot 2019-06-28 at 8 56 01 PM" src="https://user-images.githubusercontent.com/38504767/60386134-529b7080-9a5f-11e9-999d-33776d22f016.png">








