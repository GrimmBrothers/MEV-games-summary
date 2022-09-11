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
 
 - **MEV**:
 - **Local MEV**
 - **Permisionless MEV**:
 - **Price of MEV**:
 - **Auction Mechanism**:
 - **Ordering Mechanism**:
 - **MEV game**
 - **Zero-sum searcher games**:
 
 # Main contributions.
 
 ## MEV games formalization and taxonomy.
 
 ## Nash equilibrium and Price of MEV.
 
- **Theorem 1**: Proof of Work+ Public mempool $\Rightarrow$ Nash equilibrium were all the profits are shared by the searchers. Moreover, this equilibrium can be twisted to be sybil resistant.
- **Thereom 2**: Private mempool (players do not see each others bid) and enough symmetry among searchers (players share the same gas costs) $\Rightarrow$ unique Nash equilibrium, everything is payed to the miner. If reverted transactions are executed, the price of MEV is $\Omega(n)$. Otherwise, (Flashbots auction), the price of MEV $\Omega(1)$.
- **Theorem 3**: Low latency chains (no time to react to other players bids)+ random ordering (e.g. Polygon) $\Rightarrow$ Not all profits are payed to the validator and the price of MEV is $\Omega(\sqrt{ev})$.
- **Theorem 4**: Meta-data ordering rules and latency games $\Rightarrow$ High centralization, payment goes to other parties (AWS, energy companies) and the price of MEV is $\Omega(n)$.
 
 
 ## MEV-boost and public Bids.
 
 ## Zero sum searcher games.
 
 ### Fake bidding strategy.
 
 
 # Conclusions
 
 # Acknowledgements
 
