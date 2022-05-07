On-chain market making dilemma
----

Makers suffer from adverse selection since they give takers an option. The goal for any maker is to try to earn enough in spreads + rebate to compensate them for writing options. On-chain the speed and reliability of specify orders for a maker is more complex versus a taker's more binary decision (assuming here that maker compute (lots of bids/asks, more frequent updating) >> taker compute (single take, less frequent)). One could then argue the advantage is on the taker's side on-chain even more so than off-chain.

Rather than a flat fee to try overcome a variable adverse selection cost, Drift protocol rebates makers according to their adverse selection (currently capped up to 5bps). 
Because all the trades against the vAMM are sequenced, this is reasonable to calculate.


example
--
Imagine the price of SOL-PERP is 100 and a maker posts a large limit sell order @ 100.05. 

Then imagine this sequence: if 1) a taker takes againist the vAMM up to 100.10 (100.00->100.10, avg price ~100.05), 2) if the "maker" user did a take againist the vAMM up to their limit, then they would fill up to ~100.075 (linear approx of integrating curve from 100.10 -> 100.05).

This price improvement from taking would normally require paying a taker fee. BUT, since the maker already committed to the order before the price action occured, Drift can reasonably:
1. fill maker at their the limit price and drop the taker fee 
2. the keeper who did the fill/swap the maker at their limit price (keeper could be maker running infra, in which case no keeper charge is taken/is redundant)
3. give the would-be price improvement of taking liquidity (swap w/o a fee) as a rebate (add to maker's collateral account)

So in this example, the maker order is filled at 100.05 and recieves a rebate of ~.025 to their collateral account (the remainder after paying keeper small amount)
