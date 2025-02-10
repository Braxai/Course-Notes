Markov Blanket : probability of proposition given evidence, simplifies evidence by removing anything that doesn't effcet the proposition 
* remove additional variables if everything in the markov blanket is present in evidence
* 

P(WG = T | S=T, C=T)
* Can't simplify with Markov Blanket since R isn't in evidence
* Product Rule Application : P(WG = T, S=T, C=T) / P(S=T, C=T)
* Calculate numerator and denominator with global semantic and marginalization
  * global semantic probability everything true (all 4 nodes in this case)
  * Marginalization :
    * numerator : P(WG = T, S=T, C=T, R=T) + P(WG = T, S=T, C=T, R=F)

X conditionally independent of Y given Z : Y may cause X but if we know Z we can ignore Y
* markov blanket, X conditonally indepdent of every node in the graph given parents, children, and parents of children

MCMC sampler : approximate probability

Sampler Limitations 
* Prior
  * waste time generating irrelevant samples (samples with evidence in query that doesn't match sample) 
  * stores irrelevant samples
* Rejection
  * rejects irrelevant samples, generates them but doesn't store
* Likelihood
  * gets rid of both limitations, weights samples based on probability of generating particular sample if sampling evidence
  * Two Use Cases
    * proposition to sample is in evidence : pretend to sample and multiple by probability of it being true (correction term)
    * proposition to sample is in proposition : regular prior sample

Hidden Markov Model 
* Two additions over regular belief network
  * temporal aspect
  * reason over propositions that we don't directly observe (latent propositions)
* Markov Assumption : state only depends on previous state
* P(X2,X3,X4 | e1,e2,e3) : product rule

AB Pruning 
* max goes first
* alpha/beta : lower/upper bound on NE if opponent behaves rationally
* most pruning when best move for player is first

A*
* open fringe sorted, state can occur multiple times in open fringe
* F(n) : path from start to F that costs at least n
