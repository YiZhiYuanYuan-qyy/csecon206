# # Title Problem Set 1
## Project information
- **Author**: Yiyuan Qin, Data Science, 2023, Duke Kunshan University
- **Instructor**: Prof. Luyao Zhang, Duke Kunshan University
- **Disclaimer**: Submissions to the Problem Set No. or Final Project for [COMPSCI/ECON 206 Computational Microeconomics, 2023 Spring (Seven Week - Second)](https://ce.pubpub.org/) instructed by Prof. Luyao Zhang at Duke Kunshan University.
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

> | Constant | My setting |Original Value|
| :-----| ----: |----: |
| NUM_ROUNDS | 5 | 1 |
| ENDOWMENT | 10 | 100 |
| MULTIPLIER | 100 | 3 |

Reasons: the one-shot game is easy to guess because the player doesn't have to think about the relationship at the end of the round. This is similar to going to some tourist attractions and finding that the products sold are very expensive because most customers will not visit a tourist attraction many times in a short time. The transaction between the merchant and the customer is one-time, and since it is one-time, it can only consider the interests of the moment. Thus, I design the multiple rounds game to see the cooperative behavior in the game. In the first game, whether two players will choose to Engage and Cooperate because there will be a second and more cooperation, which will bring them more benefit if they choose Engage and Cooperate, respectively. 

Also, I reduced the original endowment and increased the multiplier. This is because player 1 was unwilling to take a high risk on whether or not player 2 would cooperate, considering that the endowment was already high. If the principal is low and the leverage is high, is player1 going to bet on the decision of player2?


- Strategic plays
- Equilibruim Evaluations: e.g., belief, strategy, and payoffs
- oTree Experimental Code 


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

Berg, Joyce, John Dickhaut, and Kevin McCabe. 1995. “Trust, Reciprocity, and Social History.” Games and Economic Behavior 10 (1): 122–42. doi:10.1006/game.1995.1027. 

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
```

