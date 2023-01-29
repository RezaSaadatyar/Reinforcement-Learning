 **Reinforcement Learning (RL)**<br/>
Reinforcement Learning (RL) is a type of Machine Learning which is based on feedback and enables an agent to learn how to interact with an environment through executing various actions and monitoring their outcomes. Rewards are provided for successful activities and penalties imposed for unsuccessful ones, allowing the agent to learn from trial and error over time and thus become more competent in completing a given task.

![RL system](https://user-images.githubusercontent.com/96347878/215255170-295c1e8a-54cb-40b9-a7c3-2ff1f66762ce.JPG)

 
 **Elements of RL:**
 - Agent: The ability to interpret the environment and act on it.
 - Environment: Physical environment where the agent operates.
 - Action: Execution of actions by the agent.
 - State: The current state of the agent.
 - Reward: Feedback from the environment after the agent evaluates its actions.
 - Policy: The method by which the agent decides what action to take based on the current situation.
 - Value: The reward that an agent will receive for performing an action in a particular state.
 
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
$Q_{t}(a)$=sum of rewards ( $R_i$ ) when a taken prior to t / number of times ( $A_i$ ) taken prior to t 



**Epsilon Greedy Action Selection:** The epsilon greedy algorithm chooses between *exploration* and *exploitation* by estimating the highest rewards. It determines the optimal action. It takes advantage of previous knowledge to choose exploitation, looks for new options, and select exploration.

**Advantages of Epsilon Greedy Algorithm:**<br/>
The epsilon greedy algorithm's significant advantage is that it is able to learn from past experiences, like other decision-making models, and explore new outcomes. The ability to explore new situations and have diverse knowledge leads to better decision-making.<br/>
**Disadvantages of Epsilon Greedy Algorithm:**<br/>
A greedy algorithm such as Epsilon can sometimes explore new parameters and determine which user is dissatisfied. 

**Multi-armed bandit Problem:**<br/>
- ε-Greedy policy
- Upper Confidence Bounds policy
- Stochastic gradient ascent policy


