On-chain market making dilemma
----

Makers suffer from adverse selection since they give takers an option. The goal for makers is to try to earn enough in spreads + rebate to compensate them.

Rather than a flat fee to try overcome a variable adverse selection cost, Drift protocol rebates makers according to their adverse selection (up to 5bps). 
Because all the trades against the vAMM are sequenced, this is reasonable to calculate.


example
--
Imagine the price of SOL-PERP is 100 and a maker posts a limit sell order at 100.05. 
If a taker takes againist the vAMM up to 100.10, if the maker did take up to their limit, then they would fill up to ~100.075 (linear approx of integrating curve from 100.10 -> 100.05).

This price improvement from taking would usually lead to a taker fee. BUT, since the maker already committed to the order before the price action, Drift can reasonably:
1. avoid charging a taker fee
2. fill the maker at their limit price (paying keeper)
3. give the would-be price improvement of taking liquidity, back to the maker's collateral account as a rebate.

So in this example, the maker order is filled at 100.05 and recieves a rebate of ~.025 to their collateral account (the remainder after paying keeper small amount)
