 **Reinforcement Learning (RL)**<br/>
Reinforcement Learning (RL) is a type of Machine Learning which is based on feedback and enables an agent to learn how to interact with an environment through executing various actions and monitoring their outcomes. Rewards are provided for successful activities and penalties imposed for unsuccessful ones, allowing the agent to learn from trial and error over time and thus become more competent in completing a given task.

![image](https://user-images.githubusercontent.com/96347878/215663658-f9d0339f-4ae1-4000-98ed-dc696fc805ac.png)


 
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

---
**Multi-armed bandit Problem:**<br/>
The multi-armed bandit problem is a classic example of reinforcement learning, in which there is a slot machine with n arms (bandits) that each have their own underlying probability distribution of success. Pulling any arm will result in either a stochastic reward of *R=+1* for success or *R=0* for failure. The objective of this problem is to maximize the total reward collected, by pulling the arms one-by-one in sequential order, over the long run.<br/>
***Multi-armed bandit solutions:***
- ε-Greedy policy:<br/>
Initialize, for a = 1 to k:<br/>
$Q(a) \leftarrow 0$<br/>
$N(a) \leftarrow 0$<br/>
Loop forever:<br/>
$A\leftarrow argmax_{a}$ $Q(a)$ with probability $1-\epsilon$ or a random action with probability $\epsilon$<br/>
$R\leftarrow$ bandit or environment ( $A$ ) <br/>
$N(A)\leftarrow N(A)+1$<br/>
$Q(A)\leftarrow Q(A)+\frac{R-Q(A)}{N(A)}$<br/>
where *N* is the counter for how many times action a (bandit) was chosen in the past, and *R* are the stochastic rewards for each time that bandit was chosen.<br/>
$Q(A) \leftarrow Q(A)+\frac{R-Q(A)}{N(A)}$; $N(A)\leftarrow$ *Average samples* <br/>
$Q(A) \leftarrow Q(A)+\alpha*({R-Q(A)})$; $\alpha\leftarrow$ *Constant alpha*
   - Exploration-Exploitation in Epsilon Greedy Algorithm:<br/>
*Exploitation* is when the agent knows all his options and chooses the best option based on the previous success rates. Whereas *exploration* is the concept where the agent is unaware of his opportunities and tries to explore other options to better predict and earn rewards.<br/>
   - Epsilon Greedy Action Selection:** The epsilon greedy algorithm chooses between *exploration* and *exploitation* by estimating the highest rewards. It determines the optimal action. It takes advantage of previous knowledge to choose exploitation, looks for new options, and select exploration.<br/>
   - Advantages of Epsilon Greedy Algorithm:<br/>The epsilon greedy algorithm's significant advantage is that it is able to learn from past experiences, like other decision-making models, and explore new outcomes. The ability to explore new situations and have diverse knowledge leads to better decision-making.<br/>
   - Disadvantages of Epsilon Greedy Algorithm:<br/> A greedy algorithm such as Epsilon can sometimes explore new parameters and determine which user is dissatisfied. 

- Upper Confidence Bounds policy<br/>$A_{t} = argmax {\left\lbrack\ Q_{t} + c*\sqrt{log(t) \over N_{t}(a)} \right\rbrack}$
- Stochastic gradient ascent policy<br/>
$Pr({A_{t}=a})$ = $e^{H_{t}(a)}\over{\sum_{b=1}^k e^{H_{t}(b)}}$ = $\pi_{t}(a)$<br/>
$H_{t+1}(a) = H_t(a) + \alpha*(R_t - mean(R_t))(1_{\alpha=A_{t}} - \pi_{t}(a)$

![combine_images-min](https://user-images.githubusercontent.com/96347878/215682825-eb8806d5-d5ef-46af-b0a6-ef396c6f0458.jpg)


---
**Reinforcement learning algorithms:**<br/>


>***Dynamic Programming:***<br/>
>>***Iterative policy evaluation (Stochastic policy evaluation)***<br/>
>   Input $\pi$, the policy to be evaluated<br/>
>  Algorithm parameter: a small threshold $\theta > 0$ determining accuracy of estimation<br/>
>  Initialize V(s), for all $s\epsilon S^+$, arbitrarily expect that $V(terminal) = 0$<br/>
>  Loop:<br/>
>    $\Delta \leftarrow 0$<br/>
>    Loop for each $s\epsilon S$<br/>
>    $\nu \leftarrow V(s)$<br/>
>    $V(s) \leftarrow \sum_{a}\pi(a|s).\sum_{s^.,r}p(s^.,r|s,a)[r+\lambda V_{\pi}(s^.)]\Rightarrow$ Bellman equation for the State-value function           
>    $\Delta \leftarrow max(\Delta,|\nu-V(s)|)$<br/>
>    until $\Delta < \theta$<br/>
>
>>***Deterministic policy evaluation***<br/>
>$\pi_0$  $\underrightarrow{E}$  $\nu_{\pi_0}$  $\underrightarrow{I}$  $\pi_1$ $\underrightarrow{E} ... \underrightarrow{I}$ $\pi_.$  $\underrightarrow{E}$  $\nu_.$<br/>
>*1. Initialization:*<br/>
>$V(s)\epsilon R$ and $\pi(s) \epsilon A(s)$ arbitrarily for all $s \epsilon S$<br/>
>*2. Policy Evaluation:*<br/>
>Loop:<br/>
>  $\Delta \leftarrow 0$<br/>
>  Loop for each $s\epsilon S$<br/>
>  $\nu \leftarrow V(s)$<br/>
>  $V(s) \leftarrow \sum_{s^.,r}p(s^.,r|s,\pi(s))[r+\lambda V_{\pi}(s^.)]$<br/>
>  $\Delta \leftarrow max(\Delta,|\nu-V(s)|)$<br/>
>  until $\Delta < \theta$ (a small positive number determining the accuracy of estimation)<br/>
>*3. Policy Improvement:*<br/>
>policy_stable $\leftarrow$ true(1)<br/>
>For each $s \epsilon S$:<br/>
>   old_action $\leftarrow \pi(s)$<br/>
>   $\pi(s) \leftarrow argmax_a \sum_{s^.,r}p(s^.,r|s,a)[r+\lambda V_{\pi}(s^.)]$<br/>
>   If old_action $\neq \pi(s)$, then policy_stable $\leftarrow$ false(0)<br/>
>If policy_stable, then stop and return $V \approx \nu_.$  and  $\pi \approx \pi_.$; else go to 2<br/>
>
>>***Value Iteration***<br/>
>*Algorithm parameter:* a small threshold $\theta > 0$ determining accuracy of estimation<br/>
>Initialize V(s), for all $s\epsilon S^+$, arbitrarily expect that $V(terminal) = 0$<br/>
>Loop:<br/>
>  $\Delta \leftarrow 0$<br/>
> Loop for each $s\epsilon S$<br/>
>  $\nu \leftarrow V(s)$<br/>
>  $V(s) \leftarrow max_a \sum_{s^.,r}p(s^.,r|s,a)[r+\lambda V(s^.)]$<br/>
>  $\Delta \leftarrow max(\Delta,|\nu-V(s)|)$<br/>
>  until $\Delta < \theta$<br/>
>  Output a deterministic policy, $\pi \approx \pi_.$, such that<br/>
>  $\pi(s) = argmax_a \sum_{s^.,r}p(s^.,r|s,a)[r+\lambda V(s^.)]$<br/>
>
>![Stochastic policy evaluation; gamma is 0 9](https://user-images.githubusercontent.com/96347878/216980725-64787936-3f04-4b45-b695-c4a6a937afb0.gif) ![Deterministic >policy evaluation; gamma is 0 2](https://user-images.githubusercontent.com/96347878/216985490-97f8356b-2ec8-41f5-9667-fb7eda45ed11.gif) ![Value Iteration; gamma is 0 >55](https://user-images.githubusercontent.com/96347878/216986152-a645bd57-fe06-4ae0-bacd-2bf94b7913b3.gif)<br/> 
>![Stochastic policy evaluation; gamma is 0 99](https://user-images.githubusercontent.com/96347878/216980750-04fc11b1-89ab-41ea-bf4d-7e0d6a8294e9.gif) ![Deterministic >policy evaluation; gamma is 0 25](https://user-images.githubusercontent.com/96347878/216986033-8fe527f7-dc0e-4683-95ff-e894a6c38cf7.gif) ![Value Iteration; gamma is 0 >6](https://user-images.githubusercontent.com/96347878/216986101-28a2a1da-be3f-424a-bf58-ce8086e90853.gif)

- Monte Carlo Approach<br/>
>***Temporal Difference (TD) Learning***<br/>
>>***TD(0):*** TD(0) is the simplest form of TD learning. This type of TD learning updates the value function with the value of each step along the way, and rewards along the way are obtained. After a sufficient number of samplings (in the limit of infinity), the observed reward is the key to keeping the algorithm grounded.<br/>
>**TD(0) algorithm:**<br/>
>*Input: the policy* $\pi$ *to be evaluated*<br/>
>*Algorithm parameter: step size* $\alpha \epsilon (0, 1]$<br/>
>*Initialize V(s), for all* $s \epsilon S^+$, *arbitrarily expect that V(terminal)=0*<br/>
>*Loop for each episode:*<br/>
>*Initialize S*<br/>
>*Loop for each step of episode:*<br/>
>$A \leftarrow$ *action given by* $\pi$ *for S*<br/>
>*Take action A, observe R,* $S^.$<br/>
>$V(S) \leftarrow V(S) + \alpha[R+\lambda V(S^.)-V(S)]$<br/>
>$S \leftarrow S^.$<br/>
>*untile S is terminal*<br/>
>
>>***Q-Learning:*** Q-learning uses the off-policy learning technique, where the agent learns the desired actions based on the previous states and awards. A greedy search improves an agent's learning by considering only the maximum reward received for a particular set of actions. Previous states and previous rewards are considered for newer states of operations.<br/>
>***Q-Learning algorithm:***<br/>
>*Algorithm parameters: step size* $\alpha \epsilon (0, 1]$, *small* $\epsilon > 0$<br/>
>*Initialize Q(s,a), for all* $s \epsilon S^+, a\epsilon A(s)$, *arbitrarily expect that Q(terminal, .)=0*<br/>
>*Loop for each episode:*<br/>
>*Initialize S*<br/>
>*Loop for each step of episode:*<br/>
>*Choose A from S using policy derived from Q(e.g., e-greedy)*<br/>
>*Take action A, observe R,* $S^.$<br/>
>*Choose* $A^.$ *from* $S^.$ *using policy derived from Q(e.g., e-greedy)*<br/>
>$Q(S,A) \leftarrow Q(S,A) + \alpha[R+\lambda max_a Q(S^., a)-Q(S, A)]$<br/>
>$S \leftarrow S^.$<br/>
>*until S is terminal*<br/>
>
>>***State Action Reward State Action (SARSA):*** The SARSA algorithm uses the On-policy for learning, in which the agent learns from the current set of actions in the current state and the target policy. Previous states and previous rewards are not considered for newer states of operation.<br/> 
>***SARSA algorithm:***<br/>
>*Algorithm parameters: step size* $\alpha \epsilon (0, 1]$, *small* $\epsilon > 0$<br/>
>*Initialize Q(s,a), for all* $s \epsilon S^+, a\epsilon A(s)$, *arbitrarily expect that Q(terminal, .)=0*<br/>
>*Loop for each episode:*<br/>
>*Initialize S*<br/>
>*Choose A from S using policy derived from Q(e.g., e-greedy)*<br/>
>*Loop for each step of episode:*<br/>
>  *Take action A, observe R,* $S^.$<br/>
>  *Choose* $A^.$ *from* $S^.$ *using policy derived from Q(e.g., e-greedy)*<br/>
>  $Q(S,A) \leftarrow Q(S,A) + \alpha[R+\lambda Q(S^., A^.)-Q(S, A)]$<br/>
>$S \leftarrow S^.; A\leftarrow A^.$<br/>
>*until S is terminal*<br/>
>
>>***Deep Q Neural Network (DQN):*** DQN, is Q learning with the help of neural networks. Defining and updating a Q-table in a large state space environment is a daunting task. To solve this very issue, we use the DQN algorithm to approximate Q values for every action and state.
