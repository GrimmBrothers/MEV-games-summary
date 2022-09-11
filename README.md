# MEV-games-summary

# Introduction

Miner or Maximal extractable value known as MEV usually refers to the extra value that **privileged** players can extract through strategically order, censor and place transactions in a domain. While every domain has its own consensus, ordering and block-creation mechanisms, each one of them arise different optimal strategies to extract the value. This strategical behavior played by rational players (searchers) arise have different impact and externalities in each domain. In the paper, we formalize the games that arises from common knowledge MEV opportunities. First, we introduce the MEV game, the game played by searchers to extract the MEV. Moreover, to study the negative externalities of the MEV games, we define the price of MEV (the price of anarchy of MEV games) with different cost functions given special emphasis to the block-space misusage. We compute the Nash equilibrium for these games and their respective block space price of MEV. We use real data of different domains such as Ethereum, Polygon and Binance smart chain to test the theoretical results obtained and compute the estimated gas misused in the MEV games. Furthermore, we introduce the zero-sum searcher strategies, the category of zero-sum MEV games induced by bots to abuse other bots design. These strategies can lead to different consequences. The most common one is draining other bots funds. However, other more involved strategies can lead to use the bots funds to DDoS the network without costs for the attacker. Finally, we introduce a more abstract definition of MEV without assuming symmetric monotone utilities over players balance. We claim that this definition provides a more insightful way of understanding the existence and the arising of MEV opportunities in decentralized domains. Providing a better framework for MEV mitigation solutions.

# Contents

- Formalization of MEV, local MEV, $\mathcal C$ -permissionless MEV and Price of MEV.
- Taxonomy of MEV games => Mempool privacy, ordering mechanism, time for block production, etc.
- Formalization of front-running and back-running in PGA domains (continuation of [Flashboys 2.0.](https://arxiv.org/abs/1904.05234)), Flashbots game and latency game.
- Study of Price of MEV of the games.
- Formalization of MEV-Boost as an MEV game among builders. Proof of statement [incompatibility of public bids and permissionless relaying](https://github.com/flashbots/mev-boost/issues/231).
- Estimation of Price of MEV in different domains.
- Introduction to Zero-sum searcher games:
  - Salmonella (Well-known)
  - Hamelin strategy.
  - Hansel and Gretel strategy.
  - Fake bidding strategy/Red strategy.
  
  
 # Relevant terms.
 
   - **Local MEV**: Refers to the extra value that a players can extract through strategically order, censor and place transactions in a domain. This is defined through a optimization problem, where the constraints are given by the player software and mempool pool limitations.
 - **Permisionless MEV**: Is the minimum local MEV that can be extracted by a set of players with an specific set of constraints.
 - **Price of MEV**: Is the Price of Anarchy of the games played by searchers in an specific game. That is, is the ratio of the Cost induced by the worst Nash equilibrium and the most optimal MEV extraction. The cost functions is not determined and can measure the cost of centralization, the block-space misusage, etc.
 - **Ordering Mechanism**: Is the algorithm used by domains clients (e.g. geth, bor, bsc-geth, Flashbots builder, etc) to order transactions and construct a block.
  - **Auction Mechanism**: Is the algorithm that determinates the alloaction of the MEV opportunity and the payments induced to the searchers.
 - **MEV game**: Is the Game played among players in an specific domain. The game is determinated by the gossip-network (modeled by a weighted directed graph), the block production random variable (models the time of block production), the gross value $v$ of the MEV opportunity and the auction mechanism induced by the ordering mechanism and the players extraction efficiencies.
 - **Zero-sum searcher games**: Are the set of games played among searchers to extract value from each other (e.g. salmonella, posion tokens, etc)
 # Main contributions.
 
 ## MEV games formalization and taxonomy.
 
We model the MEV game as a sequential game among a set of $n$ searchers $P_1,...,P_n$ who can send bundles to obtain an MEV opportunity. We assume that all players compete for the same MEV opportunity and have sufficient capital to extract it. When a specific player wins the MEV opportunity, it reaches a null MEV state for all players. In the paper, we provide a list of points that will define the MEV game. This game will take into account the latency of the players, the duration of the blocks, the mechanism of transaction inclusion (ordering mechanism), the costs of improving software, node location, etc.
 
 ![MEV games taxonomy](https://i.imgur.com/VSMlS98.png)
 
 - **PGA** = Priority gas auction
 - **R.O** = Random ordering
 - **FSS** = Fair sequencing service (FIFO)

 ## Nash equilibrium and Price of MEV.
 
- **Theorem 1**: Proof of Work+ Public mempool $\Rightarrow$ Nash equilibrium were all the profits are shared by the searchers. Moreover, this equilibrium can be twisted to be sybil resistant.
- **Thereom 2**: Private mempool (players do not see each others bid) and enough symmetry among searchers (players share the same gas costs) $\Rightarrow$ unique Nash equilibrium, everything is payed to the miner. If reverted transactions are executed, the price of MEV is $\Omega(n)$. Otherwise, (Flashbots auction), the price of MEV $\Omega(1)$.
- **Theorem 3**: Low latency chains (no time to react to other players bids)+ random ordering (e.g. Polygon) $\Rightarrow$ Not all profits are payed to the validator and the price of MEV is $\Omega(\sqrt{ev})$.
- **Theorem 4**: Meta-data ordering rules and latency games $\Rightarrow$ High centralization, payment goes to other parties (AWS, energy companies) and the price of MEV is $\Omega(n)$.
 
 
 ## MEV-boost and public Bids.
 
 We formalize the MEV-boost as an MEV game between builders. We prove that public bids are incompatible with the MEV-boost decentralziation goals.
 With the theorems about MEV games and Price of MEV, we deduce that builders do not have incentives to include reverted transactions. We suspect that running Combinatorial auction is a dominant strategy (however, this also depends on users actions).
 
 ## Zero sum searcher strategies.
 
 We introduce the Zero-sum searcher strategies. Strategies that consist of stealing, exploit, slow down or push an specific behaviour of other bots/builders. A popular examples of this strategy is [Salmonella](https://github.com/Defi-Cartel/salmonella).
 
 ### Little red riding hood (Fake bidding strategy)
 
Flashbots relayer can simulate bundles in order to construct the most proftible bundles. However, there is a there is a potential difference between the simulation and the execution payoff. Since Flashbots can not predict the special variables of next block, it can not ensure the exactly payoff of each bundle, and so, the payoff of the block. Fake bidding is the strategy used by adversarial searchers to fake bids in order to outbid competidors in the FB block simulation. This, would in expectancy increase their revenue. This strategy can be used after boosting their address reputation to increse its impact. Moreover,fake bidding strategy can be generalized with multiple accounts, to ensure wining the bundle and minimizing the payment with high probability. More details in the report and [Fake bidding github](https://github.com/GrimmBrothers/flashbots-fake-bidding).

 ### Hamelin
 
The strategy creates visible arbitrage opportunities in the mempool to incentivise MEV bots to spam arbitrage transactions. Manipulation of account nonces and the properties of bor client transaction propagation is used to prevent MEV bots from actually extracting the arbitrage opportunity, rather the trade reverses at no cost to the strategy user except for gas fees. This allows an adversary to create a large number of on-chain spam transactions for minimal cost. In other words, the strategy bribes MEV bots to fill Polygon PoS blocks with spam transactions, without actually paying the bribe. More details in the report and [Hamelin github](https://github.com/GrimmBrothers/Hamelin/blob/main/README.md).
 
 ### Hansel and Gretel
 
 # Code
 
 - Computation of Price of MEV.
 - Fake-bidding strategy
 - Hamelin strategy
 
 # Conclusions
 
 # Acknowledgements
 
 - [Flashbots](https://www.flashbots.net/).
 - [wintermute](https://www.wintermute.com/)
 - @barnabemonnot and @nikete

 # References
 
- [Flash Boys 2.0: Frontrunning, Transaction Reordering, and Consensus Instability in Decentralized Exchanges](https://arxiv.org/abs/1904.05234), 2019 [[Video]](https://www.youtube.com/watch?v=vR1v7AQ8i3k)
- [Maximizing Extractable Value from Automated Market Makers](https://arxiv.org/pdf/2106.01870.pdf), 2021
- [Price of MEV: Towards a Game Theoretical Approach to MEV](https://arxiv.org/abs/2208.13464), 2022
- [MEV-Boost: Merge ready Flashbots Architecture](https://ethresear.ch/t/mev-boost-merge-ready-flashbots-architecture/11177), 2021
