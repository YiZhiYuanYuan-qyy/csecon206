# ECON 206
## Project information
- **Author**: Yiyuan Qin, Data Science, 2023, Duke Kunshan University
- **Instructor**: Prof. Luyao Zhang, Duke Kunshan University
- **Disclaimer**: Submissions to the Problem Set No.2 for [COMPSCI/ECON 206 Computational Microeconomics, 2023 Spring (Seven Week - Second)](https://ce.pubpub.org/) instructed by Prof. Luyao Zhang at Duke Kunshan University.

## Table of Contents

- latex problem
- colab problem
- spotlight
- more about the author
- references

### Latex Problem
In this part, I introduce the history of game theory with reference. Then I give a brief definition of Nash Equilibrium. Finally, I create a Glossary of game theory, which includes many professional keywords. It includes two parts, the concept part, and the game types part.
Here is the pdf link: [here](https://github.com/YiZhiYuanYuan-qyy/csecon206/blob/main/Problem%20Set%202/Latex%20Problem/CSECON206_ProblemSet2_Spring2023_Yiyuan.pdf)

### Colab Problem
I use [nashpy](https://nashpy.readthedocs.io/en/stable/) to analyze two games: A public good game with 2 players and the ultimatum game. 

A [public goods](https://www.jstor.org/stable/1925895) game is a type of game theory scenario where individuals must choose whether or not to contribute resources (e.g., time, money, effort) to a common pool or public good. The benefits of the public good are shared among all individuals, regardless of whether they contributed or not. This creates a dilemma where individuals face a trade-off between their own self-interest and the collective interest of the group. My game is a 2 players public good game where Player A and Player B have an endowment k initially. They can choose to contribute (they can also choose how much they want to contribute as long as the amount is less than k) to the public pool or keep the endowment for themselves. The amount in the public pool will be multiplied by a multiplier m and equally divided between the two players. My analysis reflects a dilemma: only when two people jointly choose to contribute, both parties benefit the most; when one person wants to contribute, the other's benefit is smaller than that of the free rider. So both people want to be free riders, but their mutual benefit is minimal.
 
 
An [ultimatum game](https://www.sciencedirect.com/science/article/abs/pii/0167268182900117) is an extensive game, which involves two players, a proposer and a responder, who is presented with a sum of money (say, $6). The proposer must offer a division of the money between themselves and the responder (for example, $4 to the proposer and $2 to the responder). The responder can then choose to accept or reject the offer. If the responder accepts, the money is divided as proposed. If the responder rejects, neither player receives any money. This game may seem like a first-hand advantage, but in practice, when a proposer makes an unfair or unsatisfactory offer to the responder, both parties will lose, taking into account psychological reasons.

### Spotlight  
In the code part, I use [Plotly](https://plotly.com/?utm_source=google&utm_medium=cpc&gclid=Cj0KCQjwi46iBhDyARIsAE3nVrYKOB7vu0tlr1_BEgysmy9NzofUSCPxlU59NEg0hQu8YiDwtCiNehcaAlshEALw_wcB)(if the code does not work, please 
```!pip install plotly```) 


to draw the 3D figure of the payoff result, which can show the equilibrium more directly and give the changing rules with the different parameters.  
<img src = "https://github.com/YiZhiYuanYuan-qyy/csecon206/blob/main/Problem%20Set%202/Colab%20code/3d.png" width = 50%, height=50%><br/> 

In the latex part, I create a glossary from concept and game-type perspectives. I also give the example of different game types.  
<img src = "https://github.com/YiZhiYuanYuan-qyy/csecon206/blob/main/Problem%20Set%202/Latex%20Problem/glossary.png" width = 50%, height=50%><br/>

<img src = "https://github.com/YiZhiYuanYuan-qyy/csecon206/blob/main/Problem%20Set%202/Latex%20Problem/example.png" width = 30%, height=30%><br/> 

### More about the Author
- headshot  
	<img src = "https://github.com/YiZhiYuanYuan-qyy/csecon206/blob/main/Problem%20Set%201/spotlight/headshot.jpg" width = 10%, height=10%><br/> 
- DKU'23 Data Science

### References
[“The Pure Theory of Public Expenditure - JSTOR.” 2023. Accessed April 23. https://www.jstor.org/stable/pdf/1925895.pdf.](https://www.jstor.org/stable/1925895)

[Author links open overlay panelWerner Güth ∗, ∗, AbstractThere are many experimental studies of bargaining behavior, L.E. Fouraker, W. Güth, J.C. Harsanyi, and W. Krelle. 2002. “An Experimental Analysis of Ultimatum Bargaining.” Journal of Economic Behavior &amp; Organization. North-Holland. April 1. https://www.sciencedirect.com/science/article/abs/pii/0167268182900117. ](https://www.sciencedirect.com/science/article/abs/pii/0167268182900117)



```
@article{samuelson1954pure,
  title={The pure theory of public expenditure},
  author={Samuelson, Paul A},
  journal={The review of economics and statistics},
  pages={387--389},
  year={1954},
  publisher={JSTOR}
}
@article{guth1982experimental,
  title={An experimental analysis of ultimatum bargaining},
  author={G{\"u}th, Werner and Schmittberger, Rolf and Schwarze, Bernd},
  journal={Journal of economic behavior \& organization},
  volume={3},
  number={4},
  pages={367--388},
  year={1982},
  publisher={Elsevier}
}
```