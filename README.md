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


#### Starting Simple

Let's just look at the expected value per toss. We can get at this by just doing 1,000,000 simulations of 2 random dice throws (random int of 1 to 6) and then applying the rules over these. Note: This does not include the case of snake eyes on a 0 resulting in -50. 

As you can see the most common outcome is 0 with over 30% of tosses ending up in a 0. There are some less frequent very large values (16, 20, 24) due to the doubles rule. Overall the expected value per toss is 6.67.

<img width="416" alt="Screen Shot 2019-06-25 at 9 52 51 PM" src="https://user-images.githubusercontent.com/38504767/60147602-b0943380-9793-11e9-9f69-f67ab20b69c6.png">                      <img width="198" alt="Screen Shot 2019-06-25 at 9 54 44 PM" src="https://user-images.githubusercontent.com/38504767/60147650-ea653a00-9793-11e9-819c-21fe839f0a13.png">




