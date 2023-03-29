# # Title Problem Set 1
## Project information
- **Author**: Yiyuan Qin, Data Science, 2023, Duke Kunshan University
- **Instructor**: Prof. Luyao Zhang, Duke Kunshan University
- **Disclaimer**: Submissions to the Problem Set No.1 for [COMPSCI/ECON 206 Computational Microeconomics, 2023 Spring (Seven Week - Second)](https://ce.pubpub.org/) instructed by Prof. Luyao Zhang at Duke Kunshan University.
- **Acknowledgments**: [How to Acknowledge?](https://www.scribbr.co.uk/thesis-dissertation/acknowledgements/)
[notes: please include all professors, students, and staff who have contributed to your completetion of the project.]
- **Project Summary**: 
  - This is the first homework for ECON 206
  - [Research Questions]
  - [Application Scenario]
  - [Methodology]
  - [Results]
  - [Intellectual Merits and Practical impacts of your project.]
  
   
Note: please insert the screenshot of the answers to your research question by ChatGPT. The methodology that you use to address the research questions must be more innovative than both the current literature and ChatGPT. 

## Table of Contents

- model
- code
- spotlight
- more about the author
- references

### Model
- Game Environment (Berg et al., 1995)
	1. Players:  
	There are 2 players participating in the game [player 1 and player 2]. 
	2. Strategies:  
	The strategies can be given the following names: in the first stage player 1 chooses either to Exit or to Engage. If player 1 chooses Engage, then player 2 in the second stage chooses between Cooperate and Defect.
	3. Payoffs:
		- For player 1, the payoff is [ENDOWMENT － sent\_amount + sent\_back\_amount]
		- For player 2, the payoff is [sent\_amount * MULTIPLIER － sent\_back\_amount]
- Solution Concept  
	 ![Trust game](https://github.com/YiZhiYuanYuan-qyy/csecon206-HW1/blob/main/model/trust_game.png)  
	 In the figure above, the strategies are shown as a tree. Assume the endowment is 5 and the multiplier is 10. If player 1 doesn't Engage, it will gain 5 directly; if player 1 Engage, player 2 will choose to Defect or to Cooperate. If player 2 Defect player 1, it will gain 5 multiple 10, which is 50; if player 2 chooses to Cooperate with player 1, it will give some back to player 1, which means the payoff of Cooperate is definitely less than that of Defect. I just write the (25, 25) to present this situation.   
	 
	 Backward induction checks player 2 first. For player 2, 50 > 25, thus, it will choose to Defect. For player 1, it knows that player 2 will choose Defect, then the payoff is 0 for it. However, if player 1 chooses to Exit, then it will get 5, which is larger than 0.  
	 
	 The best strategies based on backward induction are drawn in the tree. The best strategy for player 1 (blue) is to Exit, while the best strategy for player 2 (purple) is to Defect.
- Evaluations: e.g., efficiency and fairness   
 	Backward induction is efficient because it is easy to illustrate and understand both by the tree and by the concept. There is no need to build a complex model to find the best strategies. We just need to compare the several strategies and find the maximum. That is, backward induction can identify the efficient outcome of a game, which maximizes the total payoffs of all players. It considers the entire game and all possible strategies of the players, which allows it to find the strategy that maximizes the overall outcome.   
 	
 	However, it might not fairness in some cases. Backward induction assumes that all players are rational and have complete information about the game. In reality, players may have limited information, and their decisions may be influenced by factors such as emotions or social norms. Therefore, the outcome identified by backward induction may not always be achievable or desirable in practice. Also, for some games that might have more than one equilibrium, backward induction can only find one outcome. It cannot give all the possible results of the game. 

### Code
- Game Environment   
	1.  I change the rounds of the game from 1 to 5
	2.  I change the endowment from 100 to 10
	3. I change the multiplier from 3 to 100

 | Constant | Original Value |My setting|
| :-----:| :----: |:----: |
| NUM_ROUNDS | 1 | 5 |
| ENDOWMENT | 100 | 10 |
| MULTIPLIER | 3 | 100 |

Reasons: the one-shot game is easy to guess because the player doesn't have to think about the relationship at the end of the round. This is similar to going to some tourist attractions and finding that the products sold are very expensive because most customers will not visit a tourist attraction many times in a short time. The transaction between the merchant and the customer is one-time, and since it is one-time, it can only consider the interests of the moment. Thus, I design the multiple rounds game to see the cooperative behavior in the game. In the first game, whether two players will choose to Engage and Cooperate because there will be a second and more cooperation, which will bring them more benefit if they choose Engage and Cooperate, respectively. 

Also, I reduced the original endowment and increased the multiplier. This is because player 1 was unwilling to take a high risk on whether or not player 2 would cooperate, considering that the endowment was already high. If the principal is low and the leverage is high, is player1 going to bet on the decision of player2?


- Strategic plays
- Equilibrium Evaluations: e.g., belief, strategy, and payoffs  
 
This five-round game is a centipede game (Rosenthal, 1981). It just repeats the game above five times, and for each time, the best choices are the same: Exit and Defect. This is also the Nash equilibrium for the game. However, in the real game, people are not rational and want to take certain risks to bet on the more significant payoff. 

Player 1 knows that they will play more rounds, it may think, "I only have 10 now, but if I give 10 to player 2, it will get 1000! I have already given my sincerity. Also, if player 2 wants more payoff, which means player 2 definitely wants to play more rounds! So, player 2 will give me a payoff to make sure I will Engage in the game in round 2. On the other hand, if player 2 Defect in the first round, I only lose 10, but if I bet successfully, I will get at least more than 10 (because if player 2 wants to make sure I will play more rounds, it will give me more than 10 to make me satisfied)."

Player 2 gets some money from player 1, and the money is multiplied by 100. It might think, "Player 1 trusts me or, in this round and the next few rounds, because it wants to cooperate with me to gain more based on the multiplier. If player 1 has this idea, I can share some benefits to keep going on playing this game, and in each round, I will gain. Then I will choose Cooperate!"

These are probably the thoughts of both players at the beginning of the game, as I reduce the principal and increase the leverage. Therefore, in the first round, player 1 will most likely want to gamble, while player 2 will feel player 1's sincerity and choose to cooperate. 

But the question arises, will the two players really cooperate until the last round?

There are a lot of situations that can happen, depending on the risk appetite of the two players and what counts as winning in their minds. For some people, maximizing their own payoff may be the best choice, while for others, the payoff of the game may be as long as their payoff is greater than the payoff of the other party. 


- oTree Experimental Code   
```
#!https://github.com/YiZhiYuanYuan-qyy/csecon206-HW1/blob/main/code/Trust.otreezip
```


### Spotlight
- Posters
- Figures
- Slides
- Presentations
- Review articles
- Media appearance

### More about the Author
- headshot
- self-introduction
- Final reflections 
  - intellectual growth
  - professional growth
  - living a purposeful life

### References

[Berg, Joyce, John Dickhaut, and Kevin McCabe. 1995. “Trust, Reciprocity, and Social History.” Games and Economic Behavior 10 (1): 122–42. doi:10.1006/game.1995.1027] (https://www.sciencedirect.com/science/article/abs/pii/S0899825685710275). 

[Rosenthal, Robert W. 1981. “Games of Perfect Information, Predatory Pricing and the Chain-Store Paradox.” Journal of Economic Theory 25 (1): 92–100. doi:10.1016/0022-0531(81)90018-1](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=a7552bd3302f6dee7c0b74dea6fc486f794db0b8). 

```
@article{berg1995trust,
  title={Trust, reciprocity, and social history},
  author={Berg, Joyce and Dickhaut, John and McCabe, Kevin},
  journal={Games and economic behavior},
  volume={10},
  number={1},
  pages={122--142},
  year={1995},
  publisher={Elsevier}
}
@article{rosenthal1981games,
  title={Games of perfect information, predatory pricing and the chain-store paradox},
  author={Rosenthal, Robert W},
  journal={Journal of Economic theory},
  volume={25},
  number={1},
  pages={92--100},
  year={1981},
  publisher={Citeseer}
}
```

