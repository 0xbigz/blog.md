INSURANCE FUND PRIMER
---

insurance funds (IF) are method to avoid having participant(s) pays off another's bad debt (either through a social loss (explicit) or inflation (implicit) event)

bad debt: is a liability without enough assets

in defi protocol's:
1. traders pay portion of fees when positions get altered to insurance fund (taker fee, liquidations fee, can depend upon level of leverage, undercollateralized agreements) 
2. insurance assets sit idle
3. when bad debt occurs, gets bailed out by the insurance fund

or health insurance:
1. members pays a monthly rent/tax to insurance fund
2. the insurance company negotiates price improvement with supplier, in exchange flow from their consumer monopoly (in-network)
3. members have option to pay improved prices with perform pulls from insurance fund to cover percentage

or like teacher's union:
1. teachers pays union dues to union fund
2. union leaders negotiate salary for their teacher monopoly
3. teachers acquire union salary (to pay more union dues)

or the general "real world" case:
1. users pays a rent/tax for service
2. the insurance org requests referral bonus for flow from their users
3. users recieve surplus to pay more rent/tax


notice defi example differs from real world example:
- most examples in spot, levered users are margin trading and paying continuous borrow cost
- but most examples in perps, levered users only pay the "leverage fee" iff they dont control their risk to avoid liquidation, rather than upfront.
  - this is probably useful from a demand acquisition prespective (buy now, no money down!)
- the insurance fund *sits idle* and doesnt work to get any form of negotiated improvement for its users
  - perhaps its mere existence instills confidence for a market makers to offer any liquidity and competitive pricing
- an overcollateralized user in the defi protocol bares the burden of bad debt


COMMON DEFI FUND STRATEGIES:
----
IDO??:
a strategy is the sale of the token to hold the quote currency in the insurance fund.
depending on the token supply percentages (if the sale was for all the supply) it makes sense, but for a limited supply probably not


STAKING?? 🥩:

protocol token:
one common design is to stake the protocol's governance token as the insurance fund, which when sold can cover the quote asset debt. 
however when a tail event hits this leads to cascading price event similar to the luna/ust depegging. 

quote asset debt:
staking the quote debt (e.g. usdc) for usdc works better, but is still not productive most of the time. as in above, there needs to be friction to exit otherwise it will be a run for the door once any risk is estimated.

"the only way to avoid the depeg is to be the peg"
- ShibuLuvr4



no-IF (:
----

Insurance funds just collect rent, sit there waiting for bad stuff to happen, and cant negogiate. ideas to have external staking make the rent extraction worse in good times and availablity low in bad times. 

so lets get rid of them!

Introducing no-if:
- users with high leverage contineously pay users with low leverage
- users with the lowest leverage are basically staked
- when theres bad debt, its a social loss event and every participants pay pro-rata share (by either 1. the capital allocated to their position or 2. the base size of their position)


notes:
- "contineously pay" should also not be unix_timestamp/slot based, but more volatility based. (vol is time)
- the rate the users pay and recieve should be based on current leverage distribution: highest for high leverage, lowest for low leverage
- two users with the same position, one with higher leverage one with lower leverage have different payoffs
- the following is very difficult to pull off in cross margin system, its an open problem to calculate online the user's leverage within one market

shape of -x^3 as fund flow distribution, where x=z-score of user leverage and y=rate
![image](https://user-images.githubusercontent.com/83473873/183895658-6aa3da26-0808-4c20-8cb0-5ab0d8c6d17f.png)






