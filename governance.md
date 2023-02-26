---
tags: defi, governance
---
# governance

overview
---
Unless a protocol wants to be an immutable public utility, it will require some form of governance. Given the overhead and friction of decentalized governance, most teams building a protocol iterate the design and find some product market fit first before any governance. Once a protocol has established, governance is a way to continue maintaining and adjusting the protocol in a decentralized manner. Maintaining can involve 1) divvy up revenue for contributors 2) fixing bugs and enhancing features the protocol offers.

To move beyond a social club, governance for a protocol usually involves some currency management. Candidly speaking, the bigger the currency pot to be governed, the more likely someone new would be interested in contributing to the protocol and thus participating in governance. Any governing/political structures stem from resource management and people are naturally drawn to any relative resource surplus.

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

# proposal #1 [DRAFT]:
1) initiation process
2) stake to earn voting power
3) voting power per proposal has diminishing margin returns

## details/features: (exact params tbd)
high level notes:
- all DAO member net positive rewards are 'voluntary' (an individual has to opt in to claim any net rewards accrued)

### initiation
- must stake and wait to be let in
- existing members can expedite with a majority vote
- existing members can block by burning amount equal to stake (double burn)

### explusion
- users below a certain threshold of participation can be slashed
- after certain amount of low participation can be slashed/removed from governance as well

### factions
- user can opt to join a faction (F_A, F_B) or create a new faction (F_C)
- each faction gets to elect up to two senators
- each faction has X% the treasury at start of quarter as budget (inspired by "sortition" [4])
- leaving factions for being member < X seconds old requires exit tax

### proposals
- anyone can propose with a stake of X
- during the filibuster process, the proposal is discussed and cannot be voted on. other users must stake to reaffirm / expedite it for voting
- proposals require quorm to pass
  - quorm is a function of number of members AND percentage
  - if the proposal is 'faction only', it only requires members of the faction
  - yay, ney, and abstain are allowed (and doing so is considered participation)
- voting costs 'voting power' and a "sliver" of stake
- to vote in certain proposals may require protocol's user account to have certain stat (e.g. insurance fund stake)
- if proposal doesnt pass, stakers lose a portion (but users voting the "losing side" of proposal can reclaim their sliver of stake)
- a majority of senators must approve to execute (elected senators are defaulted to auto approve )
  - senators in other factions can veto faction-only proposals

### opt-in delegacy 
- (opt into representative democracy!), user can set (delegate authority, and optional expiry ts)
- once expiry ts is set, cannot revoke until that date (unless delegate absolves them of this lockup or doesnt participate, or original user burns 50% to expedite) 
- goal of this is to show neutrality / signal [0]

### taxation
- all users are taxed by governance
    - already a small consumption tax in proposing/voting 
    - wealth percentage cost. larger stakes should pay moderately higher % than lower stakers
- all factions are taxed by governance
    - if there are more than two factions, the fixed cost is the max of X% of total stakes or Y% the amount of the smallest faction (where X < Y)
    - factions can determine how to collect/pay. factions that fill vault w/ taxes owed pay the rest pro rata across members.
- taxes can be redistribute based on reputation / peer review

### compliance
- utilize DVA (Default Value Accural), a low burden design recommendation to allow DAOs to collect protocol revenue for their treasury while discouraging / eliminating profit from illicit activity. [3]
- tracking individual user fees and earmarking funds from compliant users can help ensure that the DAO only receives clean funds, while any undetermined funds remain within the protocol.


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
