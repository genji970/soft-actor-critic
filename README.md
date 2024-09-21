SAC is based on entropy regularization. By controlling entropy(rewards - alpha * log(policy)) model do not easily fall into overfitting hole. 
alpha is sometimes constant but you can make deep learning model to adjust ratio between exploration and exploitation.

critic_loss = q_t - (reward + gamma(q_t+1 - log(policy_t+1)))
By this, q_t learns current reward and next step's q value
By soft Bellman operator(contraction stuff), q_t slowly converges to appropriate q_value

problem in Bellman operator is that if environment is complicated so it is hard for agent to act which has better reward(meaning it is in local minimum),
you have to do some exploration by adding new code. In this sac, it is alpha*log(policy) but also you can use some greedy things

q_t - alpha * log(policy) -> -(q_t - alpha * log(policy)) to do gradient descent
This loss function means that q_t always influenced much by reward(can go to local min), but by decreasing value of policy(prob of correspond action), entropy increases


In DDPG, to calculate temporal correlated exploration, using Ornstein-Uhlenbeck noise
