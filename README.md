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

<img width="859" alt="Screen Shot 2019-07-13 at 8 01 04 PM" src="https://user-images.githubusercontent.com/38504767/61177675-ff6e0580-a5a8-11e9-998d-ce4737b11d5a.png">

#### Average number of turns to win the game 
<img width="405" alt="Screen Shot 2019-07-13 at 8 03 53 PM" src="https://user-images.githubusercontent.com/38504767/61177702-5d9ae880-a5a9-11e9-81ca-ccc804e4daba.png">

If we're just looking at the expected number of turns it would take to win the game, the 2 roll strategy win with an average of ___ turns is the best. After that the average expected number of turns increases and becomes a worse strategy by this metric. 

#### Percent of games won in under 10 turns 
<img width="393" alt="Screen Shot 2019-07-13 at 8 06 11 PM" src="https://user-images.githubusercontent.com/38504767/61177729-b2d6fa00-a5a9-11e9-8fac-4f2e8bf4176b.png">

However, this game is the _first_ to get over 100. I argue it's much better to look at the speed in which you win with a strategy, not the average number of turns to win. Rolling 3 times per turn will win the game in under 10 turns __ percent of the time, making it the best strategy by this metric. 

#### Percent of games won in under 5 turns 
<img width="394" alt="Screen Shot 2019-07-13 at 8 07 54 PM" src="https://user-images.githubusercontent.com/38504767/61177748-152ffa80-a5aa-11e9-87f5-96793b6f8977.png">

While this may be aggressive, a 6 roll turn will win you the most games in under 5 turns with _ percent of games won under 5 turns.  

## Roll until you hit x 
Similar to the rolling n amount of times per turn, this strategy looks at rolling until you hit a certain number of points. For example "keep rolling until you have a score of 25 and then end your turn." I think this strategy is most representative of how people play the game because even if you only roll once but you hit double 6's and get a total of 24 points most people lock that in. 

#### Average number of turns to win 
<img width="397" alt="Screen Shot 2019-07-13 at 9 01 39 PM" src="https://user-images.githubusercontent.com/38504767/61178039-bcfcf680-a5b1-11e9-94b1-cfffbf84bf50.png">



#### Percent of games won in under 10 turns 
<img width="405" alt="Screen Shot 2019-07-13 at 9 01 25 PM" src="https://user-images.githubusercontent.com/38504767/61178024-6db6c600-a5b1-11e9-8231-a7443f56067c.png">



#### Percent of games won in under 5 turns 
<img width="399" alt="Screen Shot 2019-07-13 at 9 01 33 PM" src="https://user-images.githubusercontent.com/38504767/61178035-a22a8200-a5b1-11e9-8376-81c265b5c0e7.png">



