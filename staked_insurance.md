I encourage reading insurance for a primer on how i think about insurance in defi vs real world (and slyly pitch no-if).


No-IF has its problems, especially from a consumer demand stand point. 
in agg, people are risk-averse and will pay a premium from protection from tail events.


STAKED IF
----

- a protocol has revenue/expenses in a specific token (USDC, SOL, BTC, etc) that enter/exit a pool
- user who wants to be an insurance fund staker, stakes the same token in a pool and recieves shares 
  - the protocol also implicitly has shares of this pool as well
- like LP-ing, the staking user can swap some amount of their shares for a proportional token amount is the pool
  - if the pool grows from when they staked, they profit, if it shrinks they experience loss

this setup is simple, but allows active stakers to enter/exit freely when they anticipate revenue/expenses (respectively) in the pool.
the following constraints are in place to avoid adverse active behavior:

constraint #1: withdraw escrow period
  - can set time between an unstake request to unstake
  - from the start to end of the escrow period for a staker, all gains are omitted but losses can occur

the escrow period and rules, prevent a user from overly active staking strategy (the longer the period, the less likely). also, since all gains during the period are omitted from the unstaking user, the remaining stakers will recieve their would-be gains. assuming any revenue, this relatively improves a long term staker's rewards since they'll earn more based on enter/exit friction.


use cases:
---
drift's protocol-v2 code base utilizes this staked IF with the following params:
- 1 week escrow peroid
- 1 hour revenue settlement
