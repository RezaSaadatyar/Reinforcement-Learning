 **Reinforcement Learning (RL)**<br/>
 RL is a type of artifcial intelligence (AI) method and provides an agent to discover the environment through trial-and-error.
 
 **Elements of RL:**
 - Poicy:what to do
 - Reward: what is good. A reward $R_{t}$ is a scalar feedback signal and indicates how well agent is doing at step t
 - Value: what is good because it predicts reward
 - Model: what follows what
 
 **Sequential Decision making:**
 - Goal: select actions to maximize total future reward
 - Actions may have long term consequences
 - Reward may be delayed
 - It may be better to sacrifice immediate reward to gain more long-term reward
 
 **Agent & Environment:**
 - At each step t,the agent:
   - Executes action $A_{t}$
   - Receives observation $O_{t}$
   - Receives scalar reward $R_{t}$
 - The environment:
   - Receives action $A_{t}$
   - Emits observation $O_{t+1}$
   - Emits scalar reward $R_{t+1}$
 -  t increments at environment step
 
 The Q-learning (QL) method is a branch of RL that improves the path besides reducing computational time. During Q-learning, the target value is calculated using the max operator, which uses a greedy policy to update Q values
 
**Exploration-Exploitation in Epsilon Greedy Algorithm:**<br/>
***Exploitation*** is when the agent knows all his options and chooses the best option based on the previous success rates. Whereas ***exploration*** is the concept where the agent is unaware of his opportunities and tries to explore other options to better predict and earn rewards.

$A_{t}=argmaxQ_{t}(a)$<br/>
$Q_{t}(a)$=sum of rewards when a taken prior to t / number of times a taken prior to t

**Epsilon Greedy Action Selection:** The epsilon greedy algorithm chooses between *exploration* and *exploitation* by estimating the highest rewards. It determines the optimal action. It takes advantage of previous knowledge to choose exploitation, looks for new options, and select exploration.



