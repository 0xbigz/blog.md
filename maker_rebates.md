On-chain market making dilemma
----

Makers suffer from adverse selection since they give takers an option. The goal for any maker is to try to earn enough in spreads + rebate to compensate them for writing options. On-chain the speed and reliability to specify multiple orders for a maker is more complex versus a taker's more binary decision (assuming here that maker compute (lots of bids/asks, more frequent updating) >> taker compute (single take, less frequent)). One could then argue the advantage is on the taker's side on-chain even more so than off-chain.

Rather than a flat fee to try overcome a variable adverse selection cost, Drift protocol rebates makers according to their adverse selection (currently capped up to 5 bps (.005%)). 

Because all the trades against the vAMM are sequenced, this is reasonable to calculate.


example
--
Imagine the price of SOL-PERP is 100 and a maker posts a large limit sell order @ 100.05. 

Then imagine this sequence: if 1) a taker takes againist the vAMM up to 100.10 (100.00->100.10, avg price ~100.05), 2) if the "maker" user then did a take againist the vAMM up to their limit (100.05), then they would fill @ ~100.075 (linear approx of integrating curve from 100.10 -> 100.05).

This price improvement from taking would normally require paying a taker fee. BUT, since the maker already committed to the order before the price action occured, Drift can reasonably drop the taker fee.

within the protocol, the operation is:
1. perform a swap, but adjust the quote amount to fill the maker at their the limit price (instead of the swap price)
2. compensate the filler/keeper (keeper could be maker running infra, in which case no keeper charge is taken/is redundant)
3. give the capped remainder (5 bps) of the would-be price improvement of taking liquidity (swap w/o a fee) as a rebate (add to maker's collateral account)

So in this example, the maker order is filled at 100.05 and recieves a rebate of ~.025 to their collateral account (the remainder after paying keeper small amount)


conclusion
--

Notice in the above example, the rebate is equivalent to giving the maker zero fee price improvement compared to their limit, which counter acts adverse selection proportionally. By altering the vAMM reserves, the maker is giving specific price liquidity to the next taker in the sequence rather than the previous (inline with asynchronous trading on AMMs). Additionally, liquidity a maker provides in excess of 5 bps is a surplus to the vAMM which can used to repeg or adjust k to provide further price improvement for all/net users in the pool.
