INSURANCE FUND PRIMER
---

insurance funds (IF) are key way to avoid a social loss (pay off the debt) or inflation (make more debt!) event 

in defi protocol's:
1. traders pay fee to take on positions and when liquidated (level of leverage, undercollateralized agreements) 
2. insurance fund sits idle collecting fees 
3. bad debt (liabilities with no assets) gets bailed out by fund

or health insurance:
1. members pays a rent/tax to insurance fund
2. the insurance company negotiates price improvement for flow from their consumer monopoly (in-network)
3. members can pay improved prices and can perform pulls from insurance fund (which come from discount)

or like teacher's union:
1. teachers pays union dues to union fund
2. union leaders negotiate salary for their teacher monopoly
3. teachers acquire union salary (to pay more union dues)

or the general "real world" case:
1. users pays a rent/tax for service
2. the insurance org requests referral bonus for flow from their users
3. users recieve surplus to pay more rent/tax


notice defi differs from real world:
- levered users only pay the "leverage fee" iff they dont control their risk to avoid liquidation, rather than upfront.
  - this is probably useful from a demand acquisition prespective (buy now, no money down!)
- the insurance fund sits idle and doesnt get any negotiated improvement for its users
- an overcollateralized user in the defi protocol bares the burden of bad debt


COMMON DEFI FUND STRATEGIES:
----
IDO??:
a strategy is the sale of the token to hold the quote currency in the insurance fund.
depending on the token supply percentages (if the sale was for all the supply) it makes sense, but for a limited supply probably not


STAKING?? 🥩:
one common design is to stake the protocol's governance token as the insurance fund, which when sold can cover the quote asset debt. 
however when a tail event hits this leads to cascading price event similar to the luna/ust depegging. 

"the only way to avoid the depeg is to be the peg"
- ShibuLuvr4



no-IF (:
----

Insurance funds just collect rent, sit there waiting for bad stuff to happen, and cant negogiate. so lets get rid of them!

Introducing no-if:
- users with high leverage contineously pay users with low leverage
- users with the lowest leverage are basically staked
- when theres bad debt, its a social loss event and every pays equal share (either pro-rata the capital allocated to their position or the base size of their position)


notes:
- "contineously pay" should also not be unix_timestamp/slot based, but more volatility based. (vol is time)
- the rate the users pay and recieve should be based on current leverage distribution: highest for high leverage, lowest for low leverage
- two users with the same position, one with higher leverage one with lower leverage have different payoffs
- the following is very difficult to pull off in cross margin system, its an open problem to calculate online the user's leverage within one market

shape of -x^3 as fund flow distribution, where x=z-score of user leverage and y=rate
![image](https://user-images.githubusercontent.com/83473873/183895658-6aa3da26-0808-4c20-8cb0-5ab0d8c6d17f.png)






