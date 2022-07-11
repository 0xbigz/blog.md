oracles
----

oracle networks create a common good, readable on-chain data. however, its hard to imagine publishing this data for free as being self sufficient in the long run.


presumably, the best oracle is the mid-point of a deeply liquid spot market. deeply liquid spot is expensive to create, especially if its a token from another chain (think BNB on solana). also, if the financial incentive to manipulate this spot market is higher than the derivative that it relies upon, it can break down. additionally, a spot market also doesn't really work for any abstract non tokenized information, like a prediction market.


another route is to make things not NEED oracles and be oracle-less for derivitive markets. a futures markets doesn't *need* an oracle price if its physically settled at expiry. but an oracle can help reduce the incentive for wicks to hunt out a user's liquidation/stop price. perps markets and/or cash settled need some reference price still.


derivative exchange based oracle
----

the exchange relies on the oracle, so why not take advantage of the work being done on an exchange to build an oracle network?

terms:
```
order = {
  side: BUY | SELL,
  size: float > 0,
  price: float > 0, 
  stake: float >=0, // sol amount willing to lose if they cancel
}

X = total SOL staked on sitting orders
OP = oracle pool, lost staked amount
LS = a maker's total loss in staking

oracle bid = weighted sum (weight = size*stake) of price divided by total of bids
oracle ask = weighted sum (weight = size*stake) of price divided by total of asks
=>
oracle price = (oracle ask + oracle bid) / 2
oracle confidence proxy = (oracle ask - oracle bid)
```

walkthrough:
1. market maker places an order with above parameters (lets say: BUY 100 SOL @ $30, stake 1.1 SOL)
2. if the maker cancels this order, they lose 1.1 SOL and its added to the `OP`
3. if other trader takes it and pays a taker fee, they'll earn (`sqrt(stake)/(sqrt(X+1))`)% of the taker fee,
also if this maker has lost SOL by canceling orders previously, LS, they can earn `min(stake/2, LS/2)` back with this fill

observations:
- this system encourages makers who are confident in their orders being filled to stake and earn a maker rebate. 
- even if a maker wash trades themselves to collect their stake, the exchange took portion of their funds to discourage it.
- a sufficiently large X is still encouraged with the sqrt in the reward function
- the oracle pool can be used to both punish and return the SOL staked in orders that were cancelled back to makers for successfully filling later
- the oracle pool reward can never give a user a profit or even ALL of the losses back (can only approach zero)
- the maker is incentivized to "earn it back" if they cancel and lose, so as to not be overly cautious with staked orders if prices move naturally
- if no orders are staked, oracle can be stale at last staked order price

information leak:
- if orders staked are only/more on one side (bids), makers could be less confident that asks will get filled. this leads to prices expected to go lower in the future
- normally makers quoting like this leads to negative funding rates (to encourage more buying from takers)






