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
 
 - Formalization of MEV, local MEV and permisionless MEV.
 - Formalization of MEV games in different domains.
 - Compute the set of Nash equilibrium for common knowledge MEV opportunities (searchers have the same potential value $v$ to extract) for different domains such as Ethereum pre-timestamp tie breaker, Ethereum post-timestamp tie breaker, Ethereum post Flashbots, Polygon, etc.
 - We prove that domains with public domains with proof of work mechanisms induce to cooperative equilibrium among searchers, minimizing the profits of  validators. 
 - Taxonomy of Domains by the MEV game that induce.
 - Compute the Price of MEV (with blockspace) for different domains. We compare the negative externalities generated by different auction/ordering mechanisms.
 - Proof the statement mentioned in [incompatibility of public bids and permissionless relaying](https://github.com/flashbots/mev-boost/issues/231).
 - Introduction to zero-sum searcher games.
 - We proof mathematically and empirically the posiblity of making Polygon bots to DDoS the network at very low cost.
 - We introduce the fake bidding strategy. This strategy breaks the efficiency of Flashbots proof of work builder (v.0.6) to maximize the reveneu obtanied by searchers. This makes the builder weak against sybils and induce all the profits to the searcher executing the strategy. We provide a formalizatin of the strategy and an empirical proof.
 
 ## MEV games formalization and taxonomy.
 
 ## Nash equilibrium and Price of MEV.
 
 ## MEV-boost and public Bids.
 
 ## Zero sum searcher games.
 
 ### Fake bidding strategy.
 
 
 # Conclusions
 
 # Acknowledgements
 
