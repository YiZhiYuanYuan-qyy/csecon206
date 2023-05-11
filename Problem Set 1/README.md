# Problem Set 1
## Project information
- **Author**: Yiyuan Qin, Data Science, 2023, Duke Kunshan University
- **Instructor**: Prof. Luyao Zhang, Duke Kunshan University
- **Disclaimer**: Submissions to the Problem Set No.1 for [COMPSCI/ECON 206 Computational Microeconomics, 2023 Spring (Seven Week - Second)](https://ce.pubpub.org/) instructed by Prof. Luyao Zhang at Duke Kunshan University.
- **Acknowledgments**: Thanks Professor Zhang for giving us the opportunity to learn how to use Markdown, and this is very important to a coder
   
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
	There are two players participating in the game [Player 1 and Player 2]. 
	2. Strategies:  
	This is a centipede game for five rounds. For each round, the strategies can be given the following: player 1 chooses 0 to 10 units to give Player 2, and Player 2 will give the total amount, which is equal to the units from Player 1 multiplied by 100. Then it will choose how much to pay back the player 1.   
	To make it more specific, Player 1 strategies are [not give Player 2 anything] and [give Player 2 A units, where A is from 1 to 10] Player 2 strategies are [not give back to Player 1] and [return Player 1 B units, where B is from 1 to 100*A]
	
	3. Payoffs:
		- For player 1, the payoff is the sum of the five-round, and in each round (P1i): [P1i = ENDOWMENT － sent\_amount + sent\_back\_amount].   
		The final payoff is P1 = P11 + P12 + P13 + P14 + P15
		- For player 2, the payoff is the sum of the five-round, and in each round (P2i): [P2i = sent\_amount * 100 － sent\_back\_amount].   
		The final payoff is P2 = P21 + P22 + P23 + P24 + P25
- Solution Concept  
	 ![Trust game](https://github.com/YiZhiYuanYuan-qyy/csecon206/blob/main/Problem%20Set%201/model/tree.jpg)
	 
	 Each subgame (each round) is the simplest trust game and they are repeated, so the Nash equilibrium for the subgame is the Nash equilibrium for the whole game.   
	 For P2 in a single round, 100A is definitely larger than 100A - B, where B is larger than 0, so P2 must choose the strategy [Sent back 0] to make sure it gets the maximum benefit. Then for P1, 10 is bigger than 10 - A for sure, where A is larger than 0, so P1 must select the strategy [Sent 0]. Thus, for rational players, they will choose to stop the game at the very beginning. The payoff in each round should be (10, 0), where P1i = 10, P2i = 0. The final payoff should be (50, 0). For Player 1, payoff is P11 + P12 + P13 + P14 + P15 = 50; for Player 2, payoff is P21 + P22 + P23 + P24 + P25 = 0. 	 
	 
- Evaluations: e.g., efficiency and fairness   
 	Backward induction is efficient and fair in a completely ideal situation because it is easy to illustrate and understand both by the tree and by the concept. There is no need to build a complex model to find the best strategies. We just need to compare the several strategies and find the maximum. That is, backward induction can identify the efficient outcome of a game, which maximizes the total payoffs of all players. It considers the entire game and all possible strategies of the players, which allows it to find the strategy that maximizes the overall outcome.   
 	
 	However, it might not be fair and efficient in some cases. Backward induction assumes that all players are rational and have complete information about the game (Tadelis, 2013). In reality, players may have limited information, and their decisions may be influenced by factors such as emotions or social norms. Therefore, the outcome identified by backward induction may not always be achievable or desirable in practice. Also, for some games that might have more than one equilibrium, backward induction can only find one outcome (Myerson, 2007). It cannot give all the possible results of the game. 

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

Also, I reduced the original endowment and increased the multiplier. This is because Player 1 was unwilling to take a high risk on whether or not Player 2 would cooperate, considering that the endowment was already high. If the principal is low and the leverage is high, is player 1 going to bet on the decision of Player 2?


- Strategic plays  

This five-round game is a centipede game (Rosenthal, 1981). It just repeats the game above five times, and for each time, the best choices are the same: Exit and Defect. This is also the Nash equilibrium for the game. However, in the real game, people are not rational and want to take certain risks to bet on the more significant payoff.			

Player 1 knows that they will play more rounds, it may think, "I only have 10 now, but if I give 10 to player 2, it will get 1000! I have already given my sincerity. Also, if player 2 wants more payoff, which means player 2 definitely wants to play more rounds! So, player 2 will give me a payoff to make sure I will Engage in the game in round 2. On the other hand, if player 2 Defect in the first round, I only lose 10, but if I bet successfully, I will get at least more than 10 (because if player 2 wants to make sure I will play more rounds, it will give me more than 10 to make me satisfied)."

Player 2 gets some money from Player 1, and the money is multiplied by 100. It might think, "Player 1 trusts me or, in this round and the next few rounds, because it wants to cooperate with me to gain more based on the multiplier. If player 1 has this idea, I can share some benefits to keep going on playing this game, and in each round, I will gain. Then I will choose to Cooperate!"

These are probably the thoughts of both players at the beginning of the game, as I reduce the principal and increase the leverage. Therefore, in the first round, player 1 will most likely want to gamble, while Player 2 will feel Player 1's sincerity and choose to cooperate. 

But the question arises, will the two players really cooperate until the last round?

There are a lot of situations that can happen, depending on the risk appetite of the two players and what counts as winning in their minds. For some people, maximizing their own payoff may be the best choice, while for others, the payoff of the game may be as long as their payoff is greater than the payoff of the other party. 



- Equilibrium Evaluations: e.g., belief, strategy, and payoffs  
In this case, I set the endowment very small and the multiplier very big. The player 1 is most likely to take the risk that the Player 2 might not return any profit. Thus, the assumption is not like the Nash equilibrium that the players are all rational.   
	- Assumption: 
		- the endowment is small enough and the multiplier is big enough.
		- Players want to maximize their own profit, but in the last round, this might not be established.
		- There is no chance for the two players to exchange information and communicate with each other.  

	- Equilibrium:   
		- Case analysis: based on the result of the "Strategic plays" part, we know that there is a big likelihood that Player 1 Engage the game and Player 2 will return Player 1 in order to gain profit during the next several games. As long as the game continues, Player 2 will cooperate for this round. 
		- In the situation that 2 players cannot communicate and cooperate, the best way for them is to use the half-half method which means the profit taken by the multiplier is divided evenly.      
		 Profit Player 1 = Profit Player 2 (i<5)  
		 B - A = 100A - B
		 2B = 101A
		 B = 50.5A
		- I also give simple factors that influence A  
		 A = xc + yr where c means the confidence index for a person, which is from 0 to 1; r means the risk index for a person, which is from 0 to 1. x and y are parameters to adjust the model.   
			- i. confidence index: whether the player easily to trust others. This factor can be related to a player's past experience, such as whether they have been cheated on, as well as their personality, such as whether they are cheerful
			- ii. risk index: whether the player is willing to take the risk. This factor may relate to how much a player can afford to lose and what is the player's risk appetite
		- For the first 4 rounds, the payoff for Player 1 is (10 + 49.5A1) + (10 + 49.5A2) +...+ (10 + 49.5A4) = 40 + 49.5A1 + 49.5A2 +...+ 49.5A4, for Player 2 is 49.5A1 + 49.5A2 +...+ 49.5A4. 
		- Case analysis: In the last round, whether Player 1 chooses to participate depends on the confidence index and the risk index but the parameters might be different, because the Player 2 is more likely to defect, which means it's riskier to work together. Again, Player 1 has already got too much and only several units can bring a huge benefit, so it may want to engage the game. 
For Player 2, it might want to betray the Player 1 and it might be able to have good cooperation with Player 1 and choose to return Player 1 a little bit. 
			- The situation is very difficult to analyze. I bring an equilibrium that achieves the payoffs of each player are the maximum. In the last round, the two players still follow the half-half method. 
			- The total payoff for Player 1 is (10 + 49.5A1) + (10 + 49.5A2) +...+ (10 + 49.5A5) = 50 + 49.5A1 + 49.5A2 +...+ 49.5A5, for Player 2 is 49.5A1 + 49.5A2 +...+ 49.5A5. 

- oTree Experimental Code


``` python
<!--Constants-->
PLAYERS_PER_GROUP = 2
NUM_ROUNDS = 5
ENDOWMENT = cu(10)
MULTIPLIER = 100

<!--Group-->
sent_amount = models.CurrencyField(label="Please enter an amount from 0 to 10", min=0, max=C.ENDOWMENT)
sent_back_amount = models.CurrencyField(min=0)
def sent_back_amount_max(group):
	return group.sent_amount * C.MULTIPLIER
def set_payoffs(group):
	p1 = group.get_player_by_id(1)
	p2 = group.get_player_by_id(2)
	p1.payoff = C.ENDOWMENT - group.sent_amount + group.sent_back_amount
	p2.payoff = group.sent_amount * C.MULTIPLIER - group.sent_back_amount


<!--Player-->
Name = models.StringField(initial="Insert your name")
net_id = models.StringField(initial="Insert your net ID")
contributed = models.BooleanField()
Gender = models.StringField(choices=[["Female","Female"],["Male","Male"]
,["Other recognitions","Other recognitions"]])
Confidence = models.StringField(initial="Do you usually trust people easily？", choices=[["Most
 easily","Most easily"],["A little bit easily","A little bit easily"],["Rationale","Rationale"],
 ["Not very easily","Not very easily"],["Never trust others","Never trust others"]])

<!--Introduction-->
def is_displayed(player):
	return player.round_number == 1

##HTML
{{ include C.INSTRUCTIONS_TEMPLATE }}
{{formfields}}
{{ next_button }}

<!--Send-->
def is_displayed(player):
	return player.id_in_group == 1

##HTML
<p>
You are Participant A. Now you have {{C.ENDOWMENT}}. How much will you send to participant B?
</p>

{{ formfields }}
<p>
{{ next_button }}
</p>

{{ include C.INSTRUCTIONS_TEMPLATE }}

<!--SendBackWaitPage-->
Please waiting for the others to complete the game!

<!--SendBack-->
def is_displayed(player):
	return player.id_in_group == 2
def vars_for_template(player):
	group = player.group
	tripled_amount = group.sent_amount * C.MULTIPLIER
	return dict(tripled_amount=tripled_amount)
	
##HTML
<p>
    You are Participant B.
    Participant A sent you {{ group.sent_amount }} and you received {{ tripled_amount }}.
    Now you have {{ tripled_amount }}.
    How much will you send to participant A?
</p>

{{ formfields }}
<p>{{ next_button }}</p>
{{ include C.INSTRUCTIONS_TEMPLATE }}
	
<!--ResultsWaitPage-->	
Please waiting for the others to complete the game!

<!--Results-->
def vars_for_template(player):
	group = player.group
	ap = []
	C.NUM_ROUNDS
	for i in range(len(player.in_all_rounds())):
	    ap.append(player.in_all_rounds()[i].payoff)
	total_payoff = sum(ap)
	return dict(tripled_amount=group.sent_amount * C.MULTIPLIER,
	           all_payoff = ap,
	           total_payoff = total_payoff)

##HTML
{{ if player.id_in_group == 1 }}
    <p>
        You chose to send participant B {{ group.sent_amount }}.
        Participant B returned {{ group.sent_back_amount }}.
    </p>
    <p>
        You were initially endowed with {{ C.ENDOWMENT }},
        chose to send {{ group.sent_amount }},
        received {{ group.sent_back_amount }}
        thus you now have:
        {{ C.ENDOWMENT }}-{{ group.sent_amount }}+{{ group.sent_back_amount }}=<strong>{{ player.payoff }}</strong>
    </p>
    <ul>
    {% for payoff in all_payoff %}
        <li>The {{ forloop.counter }} round payoff is {{ payoff }}.</li>
    {% endfor %}
    </ul>
    {% if player.round_number == C.NUM_ROUNDS %}
        <p>Congratulations! You finish the game! Your total payoff during the five rounds game is {{total_payoff}}.</p>
    {% endif %}
{{ else }}
    <p>
        Participant A sent you {{ group.sent_amount }}.
        They were multipled by 100 so you received {{ tripled_amount }}.
        You chose to return {{ group.sent_back_amount }}.
    </p>
    <p>
        You received {{ tripled_amount }},
        chose to return {{ group.sent_back_amount }}
        thus you now have:
        ({{ tripled_amount }})-({{ group.sent_back_amount }})=<strong>{{ player.payoff }}</strong>
    </p>
    <ul>
    {% for payoff in all_payoff %}
        <li>The {{ forloop.counter }} round payoff is {{ payoff }}.</li>
    {% endfor %}
    </ul>.
    {% if player.round_number == C.NUM_ROUNDS %}
        <p>Congratulations! You finish the game! Your total payoff during the five rounds game is {{total_payoff}}.</p>
    {% endif %}
    
{{ endif }}

<p>{{ next_button }}</p>

{{ include C.INSTRUCTIONS_TEMPLATE }}
```
The interface of the beginning is shown below.   
<img src = "https://github.com/YiZhiYuanYuan-qyy/csecon206-HW1/blob/main/Problem%20Set%201/code/begin.png" width = 50%, height=50%><br/>
In this code, I also add the payoff received in each round at the bottom of the windows to make sure that each player knows what the gain is, which will help them to make a decision next round based on the other's behavior. In the end, I also give a clue to show the game is over.  
<img src = "https://github.com/YiZhiYuanYuan-qyy/csecon206-HW1/blob/main/Problem%20Set%201/code/result.png" width = 70%, height=70%><br/>

### Spotlight
- Behavioral experimental paper  
I looked at the paper [A study of dynamic information display and decision-making in abstract trust games (Schaffer et al., 2018)](https://www.sciencedirect.com/science/article/pii/S1071581918300028) in the International Journal of Human-Computer Studies, which impact factor is 4.866.
	- 1) What research question does the behavioral experimental research intended to address?   
	The research intended to address several research questions, including 
	
- i. To what extent can a UI improve SA? How are SA and cooperation related?
- ii. Can a UI be used to encourage or discourage human cooperative behavior?
- iii. Does the effect of a UI on human cooperative behavior change with the propensity of co-actors to exploit?
- iv. To what extent do co-actor behavior and UI support affect the performance of the individual decision-maker?

	- 2) How behavior in the experiments differ from backward induction?  
In this experiment, players were more likely to cooperate in the same trust game as UI was upgraded. In addition, trust in co-diners was impacted by co-diner forgiveness and betrayal parameters (Forgiveness and betrayal refer to the degree to which the co-diners would forgive defection and punish cooperation, respectively)[(Schaffer et al., 2018)](https://www.sciencedirect.com/science/article/pii/S1071581918300028)), Trust in co-diners was impacted by co-diner forgiveness and betrayal parameters, and participants who cooperated more reported higher trust in co-diners. Path analysis showed that forgiveness and betrayal had an effect on cooperation rate, and performance was affected by forgiveness, betrayal, situation awareness, and altruism. As a result of backward induction, rational players chose not to cooperate. In this experiment, the player makes different decisions depending on the situation.
	
	- 3) What is the behavioral (e.g., psychological, social) foundation that underpinning the observed behavior?  
	First, the observed behavior is likely influenced by trust propensity and risk-taking tendencies. If a player is consistently betrayed, he will tend not to cooperate later in the game and vice versa. This means that players' decisions are influenced by similar experiences in the past rather than completely separate games, although trust games are not repeated games. This is because past experience can affect forgiveness and betrayal parameters, which is also mentioned in the second question, and the player is not entirely rational. Second, the UI design plays a critical role in affecting these factors and ultimately shaping behavior. For example, the Level 1 UI may lead to lower situational awareness and less ability to keep track of co-diner behavior, potentially reducing trust and reciprocity.
On the other hand, the Level 3 UI with the projection panel may enhance the participant's ability to make long-term decisions and consider the impact of their actions on the group as a whole, potentially increasing cooperation and group outcomes. Additionally, the tendency to retaliate against defection and the reluctance to exploit forgiving co-diners suggest that participants may be motivated by social norms and fairness considerations.
	
	<img src = "https://github.com/YiZhiYuanYuan-qyy/csecon206/blob/main/Problem%20Set%201/spotlight/3typesUI.png" width = 70%, height=70%><br/> 
	[(Schaffer et al., 2018)](https://www.sciencedirect.com/science/article/pii/S1071581918300028)
	

- Reinforcement learning paper
  I found the paper [Dynamic trust game model between venture capitalists and entrepreneurs based on reinforcement learning theory ((Haiyan, 2018))](https://link.springer.com/article/10.1007/s10586-017-1666-x)
	- 1) What is the game environment and the learning algorithm?   
	The game environment in this study is a multi-stage game between venture capitalists (VCs) and entrepreneurs. The game is designed to simulate the dynamic nature of trust between VCs and entrepreneurs. The game environment consists of two players, a VC and an entrepreneur, who make decisions and take actions at different stages of the game. The game is played over several rounds, and the players can accumulate rewards or penalties in each round based on their decisions and actions. The game environment is characterized by uncertainty, as both players have limited information about each other and the market conditions. The game allows for dynamic changes in the trust levels of the players over time. The VC can invest in the entrepreneurs this round but quit investment next round; then the entrepreneurs may fail because they do not have any enough money. The investment to the entrepreneur is risky, but if the entrepreneur succeeds, it will return VC multiple times the benefit. For both parties, they will take care of whether the other side betrays or not. 
		The algorithm used is Q-learning [(Watkins & Dayan)](https://link.springer.com/content/pdf/10.1007/BF00992698.pdf). The agent selects the optimal strategy based on the maximum value of Q obtained from the current state, and the value of Q includes the instantaneous gain and expected future value
		
	- 2) How are the strategies from the reinforcement learning agents inspires you on trust building among humans?   
	This reinforcement learning article is actually very similar to the behavioral economics article above. Part of the results of the first article said that whether to trust others is related to previous experience; if a person is often betrayed and cheated, then he will be less likely to trust others; People who consistently work well with others are more likely to trust others than those in the former group.  
	While in the reinforcement paper, reinforcement learning agents continuously adjust their actions based on the rewarding signals they receive from their environment, and this allows them to learn and adapt to changing circumstances. Similarly, humans can adjust their behaviors based on feedback from their social interactions to build trust with others. For example, if a person receives positive feedback from their friend for being trustworthy, they are more likely to continue behaving in a trustworthy manner. On the other hand, if they receive negative feedback for being untrustworthy, they may adjust their behavior to become more trustworthy in the future. By constantly adapting our behavior based on feedback, we can improve our ability to build and maintain trust in our social relationships (Author links open overlay panelKarel Kreijns a et al., 2003). 
The two articles look different, but in fact, they are both feedback and adjustment made by human beings after receiving external information.   
This means that when building a trusting relationship, try not to betray the other person and give positive feedback when the other person trusts you. Similarly, if the other person betrays you first, there is a strategy to be worked out. This is very similar to the assumption made in the first article that interpersonal trust will change over time, so this article establishes a dynamic model.
	

### More about the Author
- headshot  
	<img src = "https://github.com/YiZhiYuanYuan-qyy/csecon206/blob/main/Problem%20Set%201/spotlight/headshot.jpg" width = 10%, height=10%><br/> 
- DKU'23 Data Science


### References

[Berg, Joyce, John Dickhaut, and Kevin McCabe. 1995. “Trust, Reciprocity, and Social History.” Games and Economic Behavior 10 (1): 122–42. doi:10.1006/game.1995.1027](https://www.sciencedirect.com/science/article/abs/pii/S0899825685710275). 

[Schaffer, James, John O’Donovan, Laura Marusich, Michael Yu, Cleotilde Gonzalez, and Tobias Höllerer. 2018. “A Study of Dynamic Information Display and Decision-Making in Abstract Trust Games.” International Journal of Human-Computer Studies 113: 1–14. doi:10.1016/j.ijhcs.2018.01.002. ](https://www.sciencedirect.com/science/article/pii/S1071581918300028)

[Haiyan, Li. 2018. “Dynamic Trust Game Model between Venture Capitalists and Entrepreneurs Based on Reinforcement Learning Theory.” Cluster Computing 22 (S3): 5893–5904. doi:10.1007/s10586-017-1666-x. ](https://link.springer.com/article/10.1007/s10586-017-1666-x)

[Watkins, Christopher J. C. H., and Peter Dayan. 2023. “Q-Learning - Machine Learning.” SpringerLink. Kluwer Academic Publishers. Accessed April 1. https://link.springer.com/article/10.1007/BF00992698.](https://link.springer.com/content/pdf/10.1007/BF00992698.pdf)

[Tadelis, Steve. 2013a. Game Theory: An Introduction. Princeton: Princeton University Press.](https://www.amazon.com/Game-Theory-Introduction-Steven-Tadelis/dp/0691129088)

[Myerson, Roger B. 2007. Game Theory: Analysis of Conflict. Cambridge, MA: Harvard Univ. Press.](https://www.jstor.org/stable/j.ctvjsf522)

[Author links open overlay panelKarel Kreijns a, a, b, AbstractComputer-mediated world-wide networks have enabled a shift from contiguous learning groups to asynchronous distributed learning groups utilizing computer-supported collaborative learning environments. Although these environments can support commun, C.H. Tu, A.P. Rovai, E. Aronson, et al. 2003. “Identifying the Pitfalls for Social Interaction in Computer-Supported Collaborative Learning Environments: A Review of the Research.” Computers in Human Behavior. Pergamon. January 16. https://www.sciencedirect.com/science/article/pii/S0747563202000572?casa_token=TizB-MeOfm4AAAAA%3AxBJ7d38-pZJ3C-muqG7z5f4NogKGUeJ6ew9UKpqFHOEfWBfcgyHYGKjzWqmkVnr28RNJHeY.](https://www.sciencedirect.com/science/article/pii/S0747563202000572?casa_token=TizB-MeOfm4AAAAA:xBJ7d38-pZJ3C-muqG7z5f4NogKGUeJ6ew9UKpqFHOEfWBfcgyHYGKjzWqmkVnr28RNJHeY)
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
@article{schaffer2018study,
  title={A study of dynamic information display and decision-making in abstract trust games},
  author={Schaffer, James and O’Donovan, John and Marusich, Laura and Yu, Michael and Gonzalez, Cleotilde and H{\"o}llerer, Tobias},
  journal={International Journal of Human-Computer Studies},
  volume={113},
  pages={1--14},
  year={2018},
  publisher={Elsevier}
}
@article{haiyan2019dynamic,
  title={Dynamic trust game model between venture capitalists and entrepreneurs based on reinforcement learning theory},
  author={Haiyan, Li},
  journal={Cluster Computing},
  volume={22},
  pages={5893--5904},
  year={2019},
  publisher={Springer}
}
@article{watkins1992q,
  title={Q-learning},
  author={Watkins, Christopher JCH and Dayan, Peter},
  journal={Machine learning},
  volume={8},
  pages={279--292},
  year={1992},
  publisher={Springer}
}
@book{tadelis2013game,
  title={Game theory: an introduction},
  author={Tadelis, Steven},
  year={2013},
  publisher={Princeton university press}
}
@book{myerson1991game,
  title={Game theory: analysis of conflict},
  author={Myerson, Roger B},
  year={1991},
  publisher={Harvard university press}
}
@article{kreijns2003identifying,
  title={Identifying the pitfalls for social interaction in computer-supported collaborative learning environments: a review of the research},
  author={Kreijns, Karel and Kirschner, Paul A and Jochems, Wim},
  journal={Computers in human behavior},
  volume={19},
  number={3},
  pages={335--353},
  year={2003},
  publisher={Elsevier}
}
```

