---
tags: defi, governance
---
# governance

overview
---
Unless a protocol wants to be an immutable public utility, it will require some form of governance. Given the overhead and friction of decentalized governance, most teams building a protocol iterate the design and find some product market fit first before any governance. Once a protocol has established, governance is a way to continue maintaining and adjusting the protocol in a decentralized manner. Maintaining can involve 1) divvy up revenue for contributors 2) fixing bugs and enhancing features the protocol offers.

To move beyond a social club, governance for a protocol usually involves some currency management. Candidly speaking, the bigger the currency pot to be governed, the more likely someone new would be interested in contributing to the protocol and thus participating in governance. Any governing/political structures stem from resource management and people are naturally drawn to any realtive resource surplus.

problems to solve
---
current on-chain governance suffers from many issues:

1) Either it is a loose veil for the original team to maintain full control or it is a gridlocked mess. Both are suspetible to hacks (including unintended hostile takeovers).
2) low participation rates, and little incentivet to among those with small influence
3) any variation to "one-token-one-vote" has sybil problem
...

A noble goal is to find a middle ground, where the original "founding fathers" can set a good direction/vision and are invested in the mission while other good intention key leaders can emerge. Active contributors who do helpful work are rewarded, while mercenaries and vultures aren't.

philsophies:
--
some philsophies in governance include: 
- governance minimization: 
  - > "Government is not the solution to our problem, government is the problem." 
  - can streamline and simplify decision-making but at the expense of more community involvement and future improvement work
- civic duty: 
  - > "Ask not what your country can do for you; ask what you can do for your country."
  - expecting civic duty in defi governance is challenging due to the prevailing culture of anonymity and hyper-capitalism, which prioritize financial gains over personal pride and community responsibility.




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
- after certain amount of low participation are slashed/removed from governance as well

proposals
- anyone can propose with a stake
- if proposal doesnt pass you lose portion of stake (half?)
- proposals require quorm to pass
- - quorm is a function of number of members AND percentage
- to vote in certain proposals may require protocol's user account to have certain stat (e.g. insurance fund stake)

opt in delegacy 
- (opt into representative democracy!), user can set (delegate authority, and optional expiry ts)
- once expiry ts is set, cannot revoke until that date (unless delegate absolves them of this lockup or doesnt participate, or original user burns 50% to expidite) 
- goal of this is to show neutrality / signal [0]

[0] - https://jumpcrypto.com/token-delegation-with-lockups/

[1] - https://www.reverie.ooo/post/experiments-in-dao-governance

[2] - https://jumpcrypto.com/token-design-for-serious-people/
