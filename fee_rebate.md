thesis
---
The best reward for a protocol user who had paid fees from the protocol treasury is reimbursement. 

This post proposes a rebate program involving the protocol's native token. 

primer
---
Many cryptocurrency exchanges offer fee discounts on trades for user stakes of the native token. Whatever the scheme, the most active/fee-paying user attempts to reach the configuration that pays the lowest total fee (by acquiring the native token etc). Whether this fee paid is access to more latent subsidies from other users of the protocol and how to detect this is out of the scope for this proposal.

Many deployed protocols lack a clear use case for their tokens or governance mechanisms, but may still choose to implement them due to market demand and to incentivize ongoing development and adoption. However, compensating token holders for fees without any associated burden or risk raises regulatory concerns and does not necessarily benefit the protocol's users, who are responsible for generating revenue.

some important rules around what constitutes rebates (in order to be a *true* rebate):
- a rebate must be issued in same token the user paid their fee with
- the max rebate must be the remaining *NET* fee paid from a user account (so if the user had $100 paid in fees and has recieved $50 in rebates, from any mechanism of protocol, they are only eligible for $50 more in rebate)


design
---
user can redeem the native token for rebate on their fees paid

the question then arises: how much should swapping 1 native token be in rebate?

methods include
- best offer
- external oracle price
- auction


auction
---
one method to determine rebate amount is a dutch auction 

- for 1 native token over time interval t, from start price $0 to end price $X (where X = say .1% of the current revenue pool)
- if the auction isn't fulfilled by time t, it lingers at $X until there is a taker
- only users who have paid net fees are eligible to be a taker
- once a taker hits, up to the max size of 1 native token, the auction price resets back to $0
- again, a user can only fill in size up to their net fee paid (so if 1 token was going for $100 but their net fee was $50 they could only fill for .5 of token)


risks
---
if a user created three accounts to wash trade. one collects a fractional maker rebate, one collects the filler reward, and the last pays taker fees, they'll have `net fee = taker fee` on one account, but only have net paid `taker-(maker+filler) fee`.

even so, the token can only be *redeemed* for the net fee. so unless the user was for instance earning a sufficient amount of tokens by doing these trades, the attack vector is minimal.


conclusion
---
this proposal is only one component of a tokenomic design. it answers the question: where/how does the protocol accrue more of its native token? some users who are less interest in governance etc may want to see their fees paid rebated to them.