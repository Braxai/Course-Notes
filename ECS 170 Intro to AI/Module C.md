Search has a goal state in mind whereas reasoning has a set of facts it infers from

Bayesian Belief Networks : concise representation of the joint probability of distribution 
* direct acyclic graph
* relationships between propositions are not deterministic
  * nodes : propositions
  * links : dependencies
  * probabilities show uncertainty in propositions and dependencies
* reasoning by merging semantic models (graph) and evidence 

Types of Semantic Models 
* direct cause
* indirect cause
* common cause
* common effect

Three Types of Queries -- Query Form : P(Facts to Infer | Evidence/Facts we know)
* Predictive : P(Effect | Cause)
* Abductive/Inductive (diagnostic) : P(Cause | Effect)
* Inter-causal Reasoning : P(Cause2 | Effect, Cause1)

Conditional Independence Assumption : burglarly conditional dependent upon John calling given the alarm went off 

### --- Missed Lectures to Review Still ---
Reasoning Steps 
* markoff blanket - simplify query
* apply product rule to convert conditional prob to join prob divided by ratio
 * P(x and y true) / P(x true) --> P(x true | y true)
* global semantic : shrink joint property
 * caclulate probability all true, start with % root true, multiple children by chance to be true if parent is true and so on
### * marginalization 

Dynamic Belief Network : predict forward in time 
* latent proposition : doesn't exist but want it to exist

Basic to Complex Belief Network
* Fast Inference
* Dynamic Belief Network : reason over time
 * Predict from current position in time going forward and backwards as well
* Predict hidden variables (latent propositions)

* Markov Chain : generate many nodes and count how many meet conditions to determine probability
 * Matrix Like : graph with nodes that are also graphs (BN states) 

MCMC Samplers : type of randomized algorithm 
* Prior Sampler : range of values, have a probability cutoff, generate a random value and if it is <= to cutoff set to true otherwise false
 * Computational problem : calcualting way more nodes than needed

















