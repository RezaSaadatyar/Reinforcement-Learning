 **Reinforcement Learning (RL)**<br/>
 RL is a type of artifcial intelligence (AI) method and provides an agent to discover the environment through trial-and-error.
 
 **Elements of RL:**
 - Poicy:what to do
 - Reward: what is good. A reward $R_{t}$ is a scalar feedback signal and indicates how well agent is doing at step t
 - Value: what is good because it predicts reward
 - Model: what follows what
 
 The Q-learning (QL) method is a branch of RL that improves the path besides reducing computational time. During Q-learning, the target value is calculated using the max operator, which uses a greedy policy to update Q values
 
**Exploration-Exploitation in Epsilon Greedy Algorithm:**<br/>
***Exploitation*** is when the agent knows all his options and chooses the best option based on the previous success rates. Whereas ***exploration*** is the concept where the agent is unaware of his opportunities and tries to explore other options to better predict and earn rewards.

**Epsilon Greedy Action Selection:** The epsilon greedy algorithm chooses between *exploration* and *exploitation* by estimating the highest rewards. It determines the optimal action. It takes advantage of previous knowledge to choose exploitation, looks for new options, and select exploration.



