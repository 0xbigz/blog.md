The best reward for a protocol user who had paid fees is reimbursement. This post proposes a rebate program using a protocol's native token. 

primer
---
Many decentralized exchanges (DEX) and even many centralized exchanges offer fee discounts in return for staking the native token. Whatever the scheme, the most active/fee-paying user attempts to reach the configuration that pays the lowest fee (by acquiring the native token etc). Whether this fee paid is a means for more latent subsidies from other users of the protocol and how to detect this is out of the scope for this proposal.

A lot of protocols struggle in curiating token use cases. In fact, many protocols currently deployed don't really *need* tokens or goverenance, but will most likely opt to do so given natural demand and as a means to encouraging prolonged development and usage. Directly (or indirectly) paying token holders fees who don't bare any burden/risk has regulatory concerns and doesnt really benefit the users of the protocol who are responsible for the revenue.

some important rules around what constitutes rebates (in order to be a *true* rebate):
- a rebate must be issued in same token the user paid their fee with
- the max rebate must be the remaining *NET* fee paid from a user account (so if the user had $100 paid in fees and has recieved $50 in rebates, from any mechanism of protocol, they are only eligible for $50 more in rebate)


thesis
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

- for 1 native token over time interval t, from star price $0 to end price $X (where X = say .1% of the current revenue pool)
- if the auction isn't fulfilled by time t, it lingers at $X until there is a taker
- only users who have paid fees are eligible to be a taker
- once a taker hits, up to the max size of 1 native token, the auction price resets back to $0
- again, a user can only fill in size up to their net fee paid (so if 1 token was going for $100 but their net fee was $50 they could only fill for .5 of token)
