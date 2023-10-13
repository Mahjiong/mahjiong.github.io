images

所谓强化学习(Reinforcement Learning，简称RL)，是指基于智能体在复杂、不确定的环境中最大化它能获得的奖励，从而达到自主决策的目的。



经典的强化学习模型可以总结为下图的形式（你可以理解为任何强化学习都包含这几个基本部分：智能体、行为、环境、状态、奖励）：

<img src="assets/e8fc39f9f7f291dc8b121858a201545b.png" style="zoom: 50%;" />





mathematics



**奖励函数**：某个状态 s 的奖励 R(s)，是指转移到该状态时可以获得奖励的期望，有$R(s) = E[R_{t+1}|S_t = s]$。

- 注意，有的书上奖励函数 $R_{t+1}$ 的下标 t+1 写为 t。其实严格来说，先有 t 时刻的状态/动作之后才有 t+1 时刻的奖励，这里统一为 t+1。

**回报**：实际中，因为一个状态可以得到的奖励是持久的，所有==奖励的衰减之和称==为回报。奖励的影响会随着时间衰减，因此添加**折扣因子** $\gamma$。

注意：这里的reward计算是**从未来开始计算**的。
$$
\begin{aligned}G_t &= R_{t+1} + \gamma \cdot R_{t+2}+ \gamma ^2\cdot R_{t+3} + \gamma ^3\cdot R_{t+4}+\cdots \\&= R_{t+1} + \gamma (R_{t+2}+ \gamma \cdot R_{t+3} + \gamma ^2\cdot R_{t+4}+\cdots) \\&= R_{t+1} + \gamma G_{t+1} \end{aligned}
$$
在马尔可夫过程的基础上加入奖励函数 R 和折扣因子$\gamma$，就可以得到**马尔可夫奖励过程**(Markov reward process，MRP)。