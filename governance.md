overview
---
unless a protocol wants to be an immutable public utility, it will require some form of governance. given the overhead and friction of governance, most teams building a protocol iterate the design and find some product market fit first before any governance. once a protocol is established, governance is a way to divvy up the revenue and continue maintaining and adjusting the protocol. 

to move beyond a social club, governance for a protocol usually involves a big monetary. candidly speaking, the bigger the monetary pot, the more interested someone will be in participating in governance.

problems to solve
---
on-chain governance suffers from many issues:

1) either it is a loose veil for the original team to maintain full control or it is . the goal is to find a middle ground, where the original "founding fathers" can set a good direction and are investing in the mission while other good intention key leaders can emerge. 
2) low participation rates among those with small influence
...

some philsophies in governance include: governance minimization

solutions
---

proposal #1:
---
1) initiation process
2) stake to earn voting power
3) voting power per proposal has diminishing margin returns


details/features: (exact params tbd)

initiation
- must stake and wait to be let in
- existing members can expedite with a majority vote
- existing members can block by burning amount equal to stake (double burn)

explusion
- users below a certain threshold of participation can be slashed
- after certain number are removed from governance as well

proposals
- anyone can propose with a stake
- if proposal doesnt pass you lose portion of stake (half?)
- proposals require quorm to pass
- - quorm is a function of number of members AND percentage
- to vote in certain proposals may require protocol's user account to have certain stat (e.g. insurance fund stake)

opt in delegacy 
- (opt into representative democracy!), user can set (delegate authority, and optional expiry ts)
- once expiry ts is set, cannot revoke until that date (unless delegate absolves them of this lockup or they burn 50%) 
- goal of this is to show neutrality / signal [0]

[0] - https://jumpcrypto.com/token-delegation-with-lockups/

