---
tags: defi, governance
---
# governance

overview
---
Unless a protocol wants to be an immutable public utility, it will require some form of governance. Governance is essential for maintaining and improving any protocol. However, decentralized governance can be a cumbersome process that requires careful consideration before implementation. Therefore, most teams seek user validation of a protocol's design before diving into governance structures.

Once a protocol is established, governance becomes crucial to sustain its growth and development. This may involve revenue distribution for contributors, bug fixes, and the introduction of new features. However, governance cannot exist in a vacuum; it needs to be supported by some form of currency management. The more significant the currency pool, the more attractive the protocol becomes to potential contributors. This phenomenon is rooted in the human instinct to seek relative resource abundance.

A new token is often created to facilitate the governance process. This governance plays a critical role in bootstrapping this new cryptocurrency by establishing its legitimacy as a means of exchange and providing the necessary infrastructure to support its use in the economy.

problems to solve
---
Current on-chain governance suffers from several issues:

- suboptimal initial allocation of tokens among stakeholders
- potential for either loose control or gridlock susceptible to hacks
- low participation rates and limited incentive for those with small influence
- sybil problem with any variation to "one-token-one-vote"
- low transparency of individual agent preferences and potential for political manipulation
- limitations for agile and responsive governance during crisis situations
...

A goal is to strike a balance in on-chain governance between allowing the founding team to set a clear vision and mission, while also enabling new, well-intentioned leaders to emerge. Rewards should be given to active contributors who add value, while preventing malicious actors from taking advantage. Governance should be agile and responsive in critical situations, but deliberate and careful for important long-term decisions.


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

# proposal #1 [DRAFT]:
1) initiation process
2) stake to earn voting power
3) voting power per proposal has diminishing margin returns

## details/features: (exact params tbd)
high level notes:
- all DAO member net positive rewards are 'voluntary' (an individual has to opt-in to claim any net rewards accrued)
- Add costs for any process thats wastes time or requres attention

terminology:
- member: any 
- "good standing": member reputation > threshold
- faction: team of members who have fractional authority over a % of budget
- senator: a council member who has veto and emergency powers. elected by faction.

### initiation
- prospective member must stake to enter initiation queue
- prospective member who has waited the queueing period (X days) can join DAO as a member
  - after X/4 days, existing members can expedite a prospective member's queue time with a majority member or senate vote
  - after X/4 days, existing members can block with a "majority or tie" member or senate vote AND by burning amount equal to initiator's stake (this creates a double burn)

### factions
- to avoid excess federal bureaucracy, factions are like states within the governance
- members can create a faction (F_N) or opt to join an existing one (F_A, F_B, ...)
- each faction gets to elect up to two senators (senators hold "veto power" or "council seats" for the governance)
- all factions get to split X % the treasury at start of each quarter as that faction's budget (inspired by "sortition" [4]). each factions pro rata split is based on number of members, their reputation, and faction's total taxes paid.
- leaving factions after being member < X days old requires exit tax
- members can be removed by a faction's super-majority vote (66%)

### voting power
- voting power acrues in a user's account over time
- for T tokens staked: accrual rate for V voting power. is sqrt(V_max-V) per hour. thus total accrued is capped at V_max (e.g. 10 * T) and converges slowly toward the max. 
- for every vote, user can use voting power to increase their influence
- using X voting power, translates to sqrt(X) votes in a single proposal

### proposals
- anyone can submit a proposal, with an optional stake of X
- during the filibuster process (Y days), the proposal is discussed and cannot be voted on. other users must stake to N-X, to reaffirm / expedite it for voting
- proposals require quorm to pass
  - quorm is a function of number of members AND percentage
  - if the proposal is 'faction specific', it only allows members of the faction
  - yay, ney, and abstain are allowed (and doing so is considered participation)
- voting costs 'voting power' and a "sliver" of stake
- to vote in certain proposals (altering perp market) may require protocol's user account to have certain stat (e.g. USDC insurance fund stake)
- if proposal doesnt pass, stakers lose a portion (but users voting the "losing side" of proposal can reclaim their sliver of stake)
- a majority of senators must approve to execute (elected senators are defaulted to auto approve )
  - senators in other factions can veto faction-only proposals

### opt-in delegacy 
- (opt into representative democracy!), user can set (delegate authority, and optional expiry ts)
- once expiry ts is set, cannot revoke until that date (unless delegate absolves them of this lockup or doesnt participate, or original user burns 50% to expedite) 
- goal of this is to show neutrality / signal [0]

### taxation
- DAO will periodically taxes its members in the native token they have staked
- members, with above average token amounts staked, are taxed by governance
    - already a small consumption tax in proposing/voting 
    - simple flat percentage
- every faction is also taxed by governance
    - if there are more than two factions, the fixed cost is the `max(X% of total stakes, Y% the amount of the smallest faction)`. Note that should be case that X < Y.
    - factions can determine how they collect/pay this tax by placing funds in their vault. remaining funds not in faction's vault, is charged pro rata across its members.
- taxes can be redistribute based on reputation / peer review

### compliance
- utilize DVA (Default Value Accural), a low burden design recommendation to allow DAOs to collect protocol revenue for their treasury while discouraging / eliminating profit from illicit activity. [3]
- tracking individual user fees and earmarking funds from compliant users can help ensure that the DAO only receives clean funds, while any undetermined funds remain within the protocol.


### explusion
- members below a certain threshold of participation can be slashed
- after certain amount of low participation can be removed from governance as well
- explused members can rejoin again through initiation

```
GovernanceMember {

proposals_when_joined: u64, // number of proposals so far since they joined
join_ts: i64,
rank: Member | Senator,
faction: Pubkey,
status: Initiated | Expelled,
delegate: Pubkey,
delegate_expiry_ts: i64,
proposals_participated: u64, // number of proposals this member has participated in

// can use PDA to find IFStake Pubkey for any token


fn initiate()

fn propose(proposal: Proposal)

fn vote(voting_power: u64)

/* only if rank == Senator */
fn update_auto_approve

/* only if rank == Senator */
fn approve_proposal

/* only if rank == Senator */
fn deny_proposal

}

Faction {

vault: Pubkey, // for taxation
senator1: Pubkey,
senator1_elected_ts: i64,
senator2: Pubkey,
senator2_elected_ts: i64,

}


ProposalInstructions {
// protocol admin instructions
...

// can only be called once every 2 weeks
// max funds to request per instruction is 10% of program funds
// funds are transfered to DAO controlled IF Stake
fn request_program_funds

// typical IF stake management from 
...

// max funds to request per Quarter is 25% of DAO balance
fn request_dao_funds

// any updates to program require 
fn update_program

}

```


[0] - https://jumpcrypto.com/token-delegation-with-lockups/

[1] - https://www.reverie.ooo/post/experiments-in-dao-governance

[2] - https://jumpcrypto.com/token-design-for-serious-people/

[3] - https://a16zcrypto.com/regulate-web3-apps-not-protocols-part-iii-the-web3-dao-dilemma/

[4] - https://ethresear.ch/t/quadratic-voting-with-sortition/6065
