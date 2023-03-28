# # Title Problem Set 1
## Project information
- **Author**: Yiyuan Qin, Data Science, 2023, Duke Kunshan University
- **Instructor**: Prof. Luyao Zhang, Duke Kunshan University
- **Disclaimer**: Submissions to the Problem Set No. or Final Project for [COMPSCI/ECON 206 Computational Microeconomics, 2023 Spring (Seven Week - Second)](https://ce.pubpub.org/) instructed by Prof. Luyao Zhang at Duke Kunshan University.
- **Acknowledgments**: [How to Acknowledge?](https://www.scribbr.co.uk/thesis-dissertation/acknowledgements/)
[notes: please include all professors, students, and staff who have contributed to your completetion of the project.]
- **Project Summary**: 
  - [Summarize the Background/Motivation]
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
- Game Environment
	1. Players:  
	There are 2 players participating in the game [player 1 and player 2]. 
	2. Strategies:  
	The strategies can be given the following names: in the first stage player 1 chooses either to Exit or to Engage. If player 1 chooses Engage, then player 2 in the second stage chooses between Cooperate and Defect.
	3. Payoffs:
		- For player 1, the payoff is [ENDOWMENT － sent\_amount + sent\_back\_amount]
		- For player 2, the payofff is [sent\_amount * MULTIPLIER － sent\_back\_amount]
- Solution Concept  
	 ![Trust game](https://github.com/YiZhiYuanYuan-qyy/csecon206-HW1/blob/main/model/trust_game.png)  
	 In the figure above, the strategies are shown as tree. Assume the endowment is 5 and multiplier is 10. If player 1 doesn't Engage, it will gain 5 directly; if player 1 Engage, player 2 will choose to Defect or to Cooperate. If player 2 Defect player 1, it will gain 5 multiple 10, which is 50; if player 2 choose to Cooperate with player 1, it will give some back to player 1, which means the payoff of Cooperate is definitely less than that of Defect. I just write the (25, 25) to present this situation.   
	 
	 Backward induction checks the player 2 first. For player 2, 50 > 25, thus it will choose to Defect. For player 1, it knows that player 2 will choose Defect, then the payoff is 0 for it. However, if player 1 choose to Exit, then it will get 5, which is larger than 0.  
	 
	 The best strategies based on backward induction are drawn in the tree. The best strategy for player 1 (blue) is to Exit, while the best strategy for player 2 (purple) is to Defect.
- Evaluations: e.g. efficiency and fairness   
 	Backward induction is efficient because it is easy to illustrate and understand both by tree and by concept. There is no need to build complex model to find the best strategies. We just need to compare the several strategies and find the maximum. That is, backward induction can identify the efficient outcome of a game, which  maximizes the total payoffs of all players. It considers the entire game and all possible strategies of the players, which allows it to find the strategy that maximizes the overall outcome.   
 	
 	However, it might not fairness in some case. Backward induction assumes that all players are rational and have complete information about the game. In reality, players may have limited information, and their decisions may be influenced by factors such as emotions or social norms. Therefore, the outcome identified by backward induction may not always be achievable or desirable in practice. Also, for some game that might have more than one equilibria, backward indution can only find one outcome. It cannot give the all possible results of the game. 

### Code
- Game Environment
- Strategic plays
- Equilibruim Evaluations: e.g. belief, strategy, and payoffs
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

- Literature References in [Chicago Author-Date](https://www.chicagomanualofstyle.org/tools_citationguide/citation-guide-2.html) Style and [BibTex](https://scholar.google.com/) 

Levin, Dan, and Luyao Zhang. 2020. “Bridging Level-K to Nash Equilibrium.” *The Review of Economics and Statistics* 104 (6): 1329–40. https://doi.org/10.1162/rest_a_00990.

```
@article{levin2022bridging,
  title={Bridging level-k to nash equilibrium},
  author={Levin, Dan and Zhang, Luyao},
  journal={Review of Economics and Statistics},
  volume={104},
  number={6},
  pages={1329--1340},
  year={2022},
  publisher={MIT Press One Rogers Street, Cambridge, MA 02142-1209, USA journals-info~…}
}
```

