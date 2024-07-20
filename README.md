 **Reinforcement Learning (RL)**<br/>
Reinforcement Learning (RL) is a type of Machine Learning that is based on feedback and enables an agent to learn how to interact with an environment through executing various actions and monitoring their outcomes. Rewards are provided for successful activities and penalties are imposed for unsuccessful ones, allowing the agent to learn from trial and error over time and thus become more competent in completing a given task.

![image](https://user-images.githubusercontent.com/96347878/215663658-f9d0339f-4ae1-4000-98ed-dc696fc805ac.png) ![alt text](Agent.png)

 **Elements of RL:**
 - Agent: The ability to interpret the environment and act on it.
 - Environment: Physical environment where the agent operates.
 - Action: Execution of actions by the agent.
 - State: The current state of the agent.
 - Reward: Feedback from the environment after the agent evaluates its actions.
 - Policy: The method by which the agent decides what action to take based on the current situation.
 - Value: The reward that an agent will receive for acting in a particular state.

 **Sequential Decision making:**
 - Goal: Select actions to maximize total future reward
 - Actions may have long-term consequences
 - Reward may be delayed
 - It may be better to sacrifice immediate reward to gain more long-term reward

 **Agent & Environment:**
 - At each step t, the agent:
   - Executes action $A_{t}$
   - Receives observation $O_{t}$
   - Receives scalar reward $R_{t}$
 - The environment:
   - Receives action $A_{t}$
   - Emits observation $O_{t+1}$
   - Emits scalar reward $R_{t+1}$
 -  t increments at the environment step

---
**Multi-armed bandit Problem:**<br/>
The multi-armed bandit problem is a classic example of reinforcement learning, in which there is a slot machine with n arms (bandits) that each has their own underlying probability distribution of success. Pulling any arm will result in either a stochastic reward of *R=+1* for success or *R=0* for failure. The objective of this problem is to maximize the total reward collected, by pulling the arms one by one in sequential order, over the long run.<br/>
***Multi-armed bandit solutions:***
- ***ε-Greedy policy***:<br/>
Initialize, for a = 1 to k:<br/>
$Q(a) \leftarrow 0$<br/>
$N(a) \leftarrow 0$<br/>
Loop forever:<br/>
$A\leftarrow argmax_{a}$ $Q(a)$ with probability $1-\epsilon$ or a random action with probability $\epsilon$<br/>
$R\leftarrow$ bandit or environment ( $A$ ) <br/>
$N(A)\leftarrow N(A)+1$<br/>
$Q(A)\leftarrow Q(A)+\frac{R-Q(A)}{N(A)}$<br/>
where *N* is the counter for how many times action a (bandit) was chosen in the past, and *R* are the stochastic rewards for each time that bandit was chosen.<br/>
- ***Epsilon greedy Algorithm for N episode in stationary & non-stationary state:***<br/>
$Q(A) \leftarrow Q(A)+\frac{R-Q(A)}{N(A)}$; $N(A)\leftarrow$ *Average samples* <br/>
$Q(A) \leftarrow Q(A)+\alpha*({R-Q(A)})$; $\alpha\leftarrow$ *Constant alpha*
   - Exploration-Exploitation in Epsilon Greedy Algorithm:<br/>
*Exploitation* is when the agcanall his options and chooses the best option based on the previous success rates. Whereas *exploration* is the concept where the agent is unaware of his opportunities and tries to explore other options to better predict and earn rewards.<br/>
   - Epsilon Greedy Action Selection:** The epsilon greedy algorithm chooses between *exploration* and *exploitation* by estimating the highest rewards. It determines the optimal action. It takes advantage of previous knowledge to choose exploitation, look for new options, and select exploration.<br/>
   - Advantages of Epsilon Greedy Algorithm:<br/>The Epsilon greedy algorithm's significant advantage is that it is able to learn from past experiences, like other decision-making models, and explore new outcomes. The ability to explore new situations and have diverse knowledge leads to better decision-making.<br/>
   - Disadvantages of Epsilon Greedy Algorithm:<br/> A greedy algorithm such as Epsilon can sometimes explore new parameters and determine which user is dissatisfied. 
- ***Upper Confidence Bounds policy (UCB)***<br/>$A_{t} = argmax {\left\lbrack\ Q_{t} + c*\sqrt{log(t) \over N_{t}(a)} \right\rbrack}$<br/>
- ***Stochastic gradient ascent policy (SGA)***<br/>
    $Pr({A_{t}=a})$ = $e^{H_{t}(a)}\over{\sum_{b=1}^k e^{H_{t}(b)}}$ = $\pi_{t}(a)$
    $H_{t+1}(a) = H_t(a) + \alpha*(R_t - mean(R_t))(1_{\alpha=A_{t}} - \pi_{t}(a)$<br/>
    
![Greedy](https://user-images.githubusercontent.com/96347878/218325166-2ca3fc59-2827-4e4e-ae89-b553381896e3.JPG) ![E-Greedy](https://user-images.githubusercontent.com/96347878/218325170-dc26f020-fa57-4837-86d7-ad7ff1bde2b5.JPG)![E-greedy_AvgSample](https://user-images.githubusercontent.com/96347878/218325177-cb3cccd9-b090-443d-8861-0348b9d54730.JPG)![UCB](https://user-images.githubusercontent.com/96347878/218325182-3f522904-3f0e-41f9-b56e-5e368daaa9c0.JPG) ![SGA](https://user-images.githubusercontent.com/96347878/218325187-1fa3acd0-b6b2-4ea0-9f8a-418ce883ef0f.JPG)

---
**Reinforcement learning algorithms:**<br/>

>***Dynamic Programming:***<br/>
>>***Iterative Policy Evaluation, for estimating*** $V \approx \nu_\pi$ :<br/>
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
>>***Policy Iteration (using iterative policy evaluation) for estimating*** $\pi \approx \pi_.$ :<br/>
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
>>***Value Iteration, for estimating*** $\pi \approx \pi_.$ :<br/>
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
>![Iterative policy; gamma(0 99)](https://user-images.githubusercontent.com/96347878/218334995-ea0afe07-512d-48a6-855e-5f8bc287b6bf.gif)![Policy iteration; gamma(0 13)](https://user-images.githubusercontent.com/96347878/218335010-f32e0415-3487-4dfa-ac6e-93f7064c7183.gif) ![Value iteration; gamma(0 3)](https://user-images.githubusercontent.com/96347878/218335023-5727e22d-1f90-4d3c-934b-af6dee8e801e.gif)
![Iterative policy; gamma(0 999)](https://user-images.githubusercontent.com/96347878/218335026-3c77e03c-fbb5-476b-bdae-7b64704ec744.gif) ![Policy iteration; gamma(0 15)](https://user-images.githubusercontent.com/96347878/218335029-c36a2afd-d9fb-4ba7-b76c-05d91cb55b98.gif) ![Value iteration; gamma(0 35)](https://user-images.githubusercontent.com/96347878/218335035-89ec86ad-b5b7-4416-a955-289963a11413.gif)
>
>***Monte Carlo Methods:***<br/>
>>***First-visit MC prediction, for estimating*** $V \approx \nu_\pi$ :<br/>
>*Input: a policy* $\pi$ *to be evaluated*<br/>
>*Initialize:*<br/>
>   $V(s)\epsilon R$, *arbitrarily, for all* $s\epsilon S$<br/>
>   *Returns(s)* $\leftarrow$ *an empty list, for all* $s\epsilon S$<br/>
>*Loop (for each episode):*<br/>
>*Generate an episode following* $\pi: S_0, A_0, R_1, S_1, A_1, R_2,..., S_{T-1}, A_{T-1}, R_T$<br/>
>$G \leftarrow 0$<br/>
>*Loop for each of episode, t=T-1, T-2, ... 0:*<br/>
>$G \leftarrow \lambda G+R_{t+1}$<br/>
>*Unless* $S_t$ *appears in* $S_0, S_1, ..., S_{t-1}:$<br/>
>*Append G to Retuens* $(S_t)$<br/>
>$V(S_t) \leftarrow$ average(Retuens $(S_t))$<br/>
>
>>***Monte Carlo ES (Exploring Starts), for estimating*** $\pi \approx \pi_.$ :<br/>
>*Initialize:*<br/>
>$\pi(s)\epsilon A(s)$, *arbitrarily, for all* $s\epsilon S$<br/>
>$Q(s,a)\epsilon R$, *arbitrarily, for all* $s\epsilon S, a\epsilon A(s)$<br/>
>*Returns(s,a)* $\leftarrow$ an empty list, for all $s\epsilon S, a\epsilon A(s)$<br/>
>*Loop (for each episode):*<br/>
>*Choose* $S_0\epsilon S, A_0\epsilon A(S_0)$ *randomly such that all pairs have probability > 0*<br/>
>*Generate an episode from* $S_0, A_0,$ *following* $\pi:S_0, A_0, R_1, S_1, A_1, R_2,..., S_{T-1}, A_{T-1}, R_T$<br/>
>$G \leftarrow 0$<br/>
>*Loop for each of episode, t=T-1, T-2, ... 0:*<br/>
>$G\leftarrow \lambda G+R_{t+1}$<br/>
>*Unless the pairs* $S_t, A_t$ *appears in* $S_0, S_1, A_1, ..., S_{t-1}, A_{t-1}:$<br/>
>*Append G to Retuens* $(S_t, A_t)$<br/>
>$Q(S_t, A_t)\leftarrow$ *average(Retuens*$(S_t, A_t))$<br/>
>$\pi(s) = argmax_a Q(s,a)$<br/>
>
>>***On-policy ﬁrst-visit MC control (for*** $\epsilon$***-soft policies), estimates*** $\pi \approx \pi_.$ :<br/>
>*Initialize:*<br/>
>   *small* $\epsilon > 0$<br/>
>   $\pi(s)\leftarrow$ *arbitrarily* $\epsilon-soft$ *policy*<br/>
>  $Q(s,a)\epsilon R$ *arbitrarily, for all* $s\epsilon S, a\epsilon A(s)$<br/>
>   *Returns(s,a)* $\leftarrow$ *empty list, for all* $s\epsilon S, a\epsilon A(s)$<br/>
>*Loop (for each episode):*<br/>
>*Generate an episode following* $\pi:S_0, A_0, R_1, S_1, A_1, R_2,..., S_{T-1}, A_{T-1}, R_T$<br/>
>$G \leftarrow 0$<br/>
>*Loop for each of episode, t=T-1, T-2, ... 0:*<br/>
>$G \leftarrow \lambda G+R_{t+1}$<br/>
>*Unless the pairs* $S_t, A_t$ *appears in* $S_0, S_1, A_1, ..., S_{t-1}, A_{t-1}:$<br/>
>*Append G to Retuens*$(S_t, A_t)$<br/>
>$Q(S_t, A_t)\leftarrow$ *average(Retuens*$(S_t, A_t))$<br/>
>$A^.\leftarrow argmax_a Q(S_t, a)$<br/>
>*For all* $a \epsilon A(S_t):$<br/>
>$\pi(a|S_t)\leftarrow 1-\epsilon+\epsilon/|A(S_t)|$ *if* $a=A^.$  *or* $\epsilon/|A(S_t)|$ *if* $a\neq A^.$
>
>![First-visit MC; gamma(0 999)](https://user-images.githubusercontent.com/96347878/218338749-ea0bf505-58b0-4e54-90a8-7da5e49aef23.gif)![Exploring Starts; gamma(0 99)](https://user-images.githubusercontent.com/96347878/218341503-6baa2c11-02dc-422f-b51d-39b948da7809.gif) ![On-policy; gamma(0 98)](https://user-images.githubusercontent.com/96347878/218342760-6664aef4-3ef0-475c-8790-5c52fab18a38.gif)![First-visit MC; gamma(0 99)](https://user-images.githubusercontent.com/96347878/218338754-6ff7a02f-9a6a-49c2-a540-3fef31e98c58.gif)![Exploring Starts; gamma(0 9999)](https://user-images.githubusercontent.com/96347878/218343028-c253c187-66b8-4df2-95f9-6441ea3a8ea9.gif)![On-policy; gamma(0 99)](https://user-images.githubusercontent.com/96347878/218342795-5d498a36-05cf-4c87-8c39-c010baadb865.gif)
>
>***Temporal Difference (TD) Learning***<br/>
>>***TD(0) algorithm:*** TD(0) is the simplest form of TD learning. This type of TD learning updates the value function with the value of each step along the way, and rewards along the way are obtained. After a sufficient number of samplings (in the limit of infinity), the observed reward is the key to keeping the algorithm grounded.<br/>
>***Tabular TD(0) for estimating*** $\nu_\pi$:<br/>
>*Input: the policy* $\pi$ *to be evaluated*<br/>
>*Algorithm parameter: step size* $\alpha \epsilon (0, 1]$<br/>
>*Initialize V(s), for all* $s \epsilon S^+$, *arbitrarily expect that V(terminal)=0*<br/>
>*Loop for each episode:*<br/>
>*Initialize S*<br/>
>*Loop for each step of the episode:*<br/>
>$A \leftarrow$ *action given by* $\pi$ *for S*<br/>
>*Take action A, observe R,* $S^.$<br/>
>$V(S) \leftarrow V(S) + \alpha[R+\lambda V(S^.)-V(S)]$<br/>
>$S \leftarrow S^.$<br/>
>*until S is terminal*<br/>
>
>>***Q-Learning:*** Q-learning uses the off-policy learning technique, where the agent learns the desired actions based on the previous states and awards. A greedy search improves an agent's learning by considering only the maximum reward received for a particular set of actions. Previous states and previous rewards are considered for newer states of operations.<br/>
>***Q-learning (off-policy TD control) for estimating*** $\pi \approx \pi_.$ :<br/>
>*Algorithm parameters: step size* $\alpha \epsilon (0, 1]$, *small* $\epsilon > 0$<br/>
>*Initialize Q(s,a), for all* $s \epsilon S^+, a\epsilon A(s)$, *arbitrarily expect that Q(terminal, .)=0*<br/>
>*Loop for each episode:*<br/>
>*Initialize S*<br/>
>*Loop for each step of the episode:*<br/>
>*Choose A from S using policy derived from Q(e.g., e-greedy)*<br/>
>*Take action A, observe R,* $S^.$<br/>
>*Choose* $A^.$ *from* $S^.$ *using policy derived from Q(e.g., e-greedy)*<br/>
>$Q(S,A) \leftarrow Q(S,A) + \alpha[R+\lambda max_a Q(S^., a)-Q(S, A)]$<br/>
>$S \leftarrow S^.$<br/>
>*until S is terminal*<br/>
>
>>***State Action Reward State Action (SARSA):*** The SARSA algorithm uses the On-policy for learning, in which the agent learns from the current set of actions in the current state and the target policy. Previous states and previous rewards are not considered for newer states of operation.<br/> 
>***Sarsa (on-policy TD control) for estimating*** $Q \approx q_0$ :<br/>
>*Algorithm parameters: step size* $\alpha \epsilon (0, 1]$, *small* $\epsilon > 0$<br/>
>*Initialize Q(s,a), for all* $s \epsilon S^+, a\epsilon A(s)$, *arbitrarily expect that Q(terminal, .)=0*<br/>
>*Loop for each episode:*<br/>
>*Initialize S*<br/>
>*Choose A from S using policy derived from Q(e.g., e-greedy)*<br/>
>*Loop for each step of the episode:*<br/>
>  *Take action A, observe R,* $S^.$<br/>
>  *Choose* $A^.$ *from* $S^.$ *using policy derived from Q(e.g., e-greedy)*<br/>
>  $Q(S,A) \leftarrow Q(S,A) + \alpha[R+\lambda Q(S^., A^.)-Q(S, A)]$<br/>
>$S \leftarrow S^.; A\leftarrow A^.$<br/>
>*until S is terminal*<br/>
>
>>***Deep Q Neural Network (DQN):*** DQN, is Q learning with the help of neural networks. Defining and updating a Q-table in a large state space environment is a daunting task. To solve this very issue, we use the DQN algorithm to approximate Q values for every action and state.<br/>
>
> ![TD(0); gamma(0 99)](https://user-images.githubusercontent.com/96347878/218345072-eb1ea875-9561-401a-a935-0a73d0f8ce4d.gif) ![Q_learning; gamma(0 5)](https://user-images.githubusercontent.com/96347878/218345254-1dd553e9-b0e2-493f-8b85-ce9e17fd5f80.gif) ![TD(0); gamma(0 999)](https://user-images.githubusercontent.com/96347878/218345065-3749543d-4b53-467e-9e7a-149c3456171f.gif) ![Q_learning; gamma(0 6)](https://user-images.githubusercontent.com/96347878/218345159-dc2ebb11-171f-4fb5-8f76-39a316cb479a.gif)
