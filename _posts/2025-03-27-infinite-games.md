---
layout: default
title: "infinite-games"
date: 2025-03-27
---

# Infinite Games

> Communication is an infinite game.
>
> Consciousness is a peculiar form of communication that is distinguished by its ability to mediate the establishment of communication between different computational processes that share resources but that otherwise may have significantly different internal structure.

> My goal is to mathematically describe this process of reciprocal, open-ended communication.

**Outline**
- Introduction and heuristics
- Entropy: what Claude Shannon did and did not do; extension to open-ended case.
- Crooks' Fluctuation Theorem: Statistical Physics
- Active Inference
- Self, Subjectivity, and Intersubjectivity

## Introduction

To begin, I will sketch some intuitive characteristics of consciousness, viewed in this light as a medium to facilitate the establishment of communication channels beginning from shared data streams.

- **Function: Integration**. In brains, consciousness plays a functional role. Among other roles, it enables the recognition and response to a broad palette of novelty, to new newness, and perhaps even newly new newness, rather than mere difference.
  - This role is consistent with the interpretation of consciousness as integrative (e.g., a crucial characteristic shared by GWT and its inbred relative IIT); a more alert, more conscious being can compare any two given stimuli (of which it is consciously aware). This ability is remarkable, because it enables composisional generalization (the ability to combine (pieces) of known knowledge or concepts with those of any other, despite any dissimilarities whatsoever; give me two things, and I can think of them at once and thereby at least produce a (possibly nonsense!) Frankenstein combination. Any two things separately thinkable are jointly imaginable, subject only to the limits of working memory, which are least restrictive when one is most conscious, that is -- most awake.)
    - Note: Why is it that consciousness seems to be particularly helpful for flexibly binding and unbinding symbols, e.g., when I substitute values into an equation, or more abstractly, when I substitute an equation into itself? [Add simple logic ref, perhaps from Godel's Proof.] Why is it that lucid dreamers struggle read in their dreams?
  - Consciousness's integrative ability goes beyond Hebbian learning or the generitically wired and behaviorally refined pathways of white matter. Again, it is the possibility of combining in intensity two or more experiences that have never been jointly experienced before. (Note: sidesteps for now the possibility that such combinations can be explored latently by background neural processes, esp. dreaming, which serves an annealing funcit on among many others.)
  - What makes such novel combinations possible? I claim that such an extreme ability to integrate requires inference-time adaptation. In order for two brain areas which do not know about one another to communicate in ways they never have before, consciousness must not merely provide the bandwidth for their signals to reach one another; it must also facilitate (at inference time) the formation of reciprocal representations (of B in A and of A in B).
  - In order to communicate deliberately rather than merely be a machinic broadcaster of a signal, B must model itself. It must be able to decode it own output at least somewhat. Otherwise communication would be at best a shot in the dark. Before A and B have established communication, they must have methods for parsing and decoding their own outputs that are independent of one another. A (B) must model data_A (data_B) using resources that are unkown to B (A).
  - An implication: to parse `data_B`, A must model B: A must not only `model(data_B)` but also `model(self_B(data_B))` because B must already contain and run `self_B(data_B)` in order to communicate deliberately.
- **Computational structure: Recursion**: there are functional limits to what A can known or actively model about itself; therefore it will have incomplete knowledge of the implementations of the subroutines that are invoked in modeling either itself or B.
  - These subroutines need not be and cannot in general be guaranteed to be strictly controlled by B, as this would require 1) a level of knowledge that is infeasible, and 2) a level of segreation of neuronal activity that is unrealistic. (When I am thinking about a spider, there is always a small chance that I will think about a birthday hat.) The upshot:
  - Subroutines can call other subroutines and also their own invokers. The process of running model(data_B) can recursively recruit an ensemble of subproutines that, in their attempts to implement parts of model(dataB), may find their own errors too large and therefore recruit an expanding ensemble.
  - So far, this process describes the qualia of open-ended awareness, such as e.g., paying attention to wildlife: there is a sense in which their, once attention is glued to them, they in fact control your mind, because their own actions do not merely send your brain raw data, but rather now send data that is parsed through actively engaged simulators; we see them through our errors and the subprocesses those errors spawn. Those things that cannot be classified or delegated to any automatic subprocess simply exist as the shimmering edge of reality they have exposed us to in our naked awareness of novelty. This is a recurrent processing model in which I have framed Deleuze's account of difference. That is, consciousness exits to provide a medium which in principle allows one to compare not against all established variations in the world, but rather (simply, modestly) all internal variations unknown by the "thinker's" mind yet encodable and simulatable via automatic processes that exist in the thinker's brain. That which cannot be automatic focuses us directly on the world as distilled into it, and thereby at least permits the formation of new simulations, although how this happens is, at least for now, impossible to say in detail: by necessity, it is a "passive synthesis," with the emphasis on passive.

DRAFT: From an intuitive point of view, such an ability requires consciousness to concurrently form and match simulations of the recipient of its attention; that is, for process A to attend consciously to process B, A must open a channel of communication to a form of input from B whose raw data are observable but whose meaning is unkown. In order to process this data, A must already implicitly simulate B; that is, to the extent that A can parse B's data at all, A must *already* contain processes that can invert B's processessing and therefore must resemble it. However, in the case of interest, namely establishing novel contact, such preliminary observations will leave large stretches of B's data indecipherable. Thus, the simulations of the inverse data generating process must be refined, and it may be that more (modularly) independent simulations must be formed inside of A in order to most thoroughly decipher B's data. It can also happen that, while A initially allocates only a certain amount of computational resources to modeling B, the errors in such a process necessitate the allocation of new resources. 

## 2. Entropy, Information, Mutual Information, Open-Ended Mutual Information

Claude Shannon introduced entropy to characterize communication channels. His goal was to characterize the capacity of communication media, or channels of communication, in a way that would remain agnostic to the content of the messages transmitted. His focus was explicitly on the efficiency of transmission through a channel with fixed limits rather than the deeper problem of communication: how to understand the meaning of the message, once recieved. In keeping with his lucid presentation, he is upfront about the scope of his work:

> The fundamental problem of communication is that of reproducing at one point either exactly or ap-
proximately a message selected at another point. Frequently the messages have meaning; that is they refer
to or are correlated according to some system with certain physical or conceptual entities. These semantic
aspects of communication are irrelevant to the engineering problem. The significant aspect is that the actual
message is one selected from a set of possible messages. The system must be designed to operate for each
possible selection, not just the one which will actually be chosen since this is unknown at the time of design.

Practical scenarios involve communicating messages between computers (that is, encoding data and programs such that a remote computer could run the program on the data and return its result), sending video footage to a television screen such that it will display properly on the hardware, and perhaps most prosaically, standard verbal communication between two humans who speak the same languge (e.g., a telegram or email).

In all these cases, the problem of using a channel to communicate a message is trivial; any one of an infinite number of coding schemes would suffice. It is the engineering of efficient channel use that is non-trivial and that motivates Shannon's use of entropy.

***The upshot*** is that Shannon considers communication between entities that can already communicate by some means, and indeed must do so in order to agree on a coding and ecoding scheme by which they will read from and write to the channel. A good coding scheme will allow them to communicate more quickly using the same channel. But to agree on a scheme, they must first communicate by some other means. It may be that a perspicacious child who wishes to send his neighbor naughty messges via Morse Code with a flashlight at his bedroom window ... will be sorely disappointed if his neighbor doesn't know Morse code, doesn't recognize it, and doesn't pick up on it.

Thus the question: how to establish semantic communication given an open channel.

It is convenient to use Shannon's terminology:

<img 
    src="/assets/images/shannon-comm.png" 
    alt="Description" 
    style="
        width: 100%; 
        max-width: 800px; 
        height: auto; 
        display: block; 
        margin: 0 auto;
    "
/>

Given ergodic distributions of a source, we can derive that the maximum bits per symbol that can be transmitted on a channel with fixed discrete alphabet is $C/H$ where C is the channel capacity and H is the entropy of the generating probability distribution (the source whose signals are to be transmitted):

```math
C = \lim_{T\rightarrow \infty} N(t) \\
H = -\sum_{i=1}^N p_i log_2 p_i 
```

***Continuous Channel***

I have stated Shannon's theorem for a discrete channel, but the result is similar for a continous channel, provided one defines an appropriate measure of capacity. Capacity cannot be defined as the number of distinct messages that pass through the channel in time $T \rightarrow \infty$, but can still be defined in terms of the continuous entropies he introduces for probability densities. It is instructive to see how it is framed.

The channel capacity C will be the maximum achievable rate R of signal transmission, where the optimization is over the channel input signal x and the recieved signal (output) y.

```math
R = H(x) - H(x|y)
```

The first term is the entropy of the signal. Shannon names the second term the *equivocation* in reference to the fact that it is precisely the entropy in x that would remain if one knew the received signal y. For a given `H(x)`, if the recieved signal had no equivocation, then the rate would be maximized and contain all information in x; if x and y were independent, then the equivocation would equal `H(x)` and the rate would be zero.

To rephrase,

```math
R = H(x) - H(x|y) \\
R = -\int P(x) log P(x) + \int P(x, y)log \frac{P(x, y)}{P(y)} \\
R = \int P(x, y) log \frac{P(x, y)}{P(x)P(y)} \\
R = D_{KL}(P(x,y)||P(x)P(y)) = I(x, y)
```

By maximinzing this quantity with respect to the input signals P(x), we achieve the R = C, the channel capacity.

Given noise `y - x = n` that is independent of x, we can write H(x, y) = H(x, n). Then, expanding both sides:
```math
H(x, y) = H(x, n) \\
H(x, y) = H(y) + H(x | y) \\
H(x, n) = H(x) + H(n) \\
```
we obtain
```math
H(x) - H(x | y) = H(x) - H(n)
```
Thus the channel rate can be written equivalently:
```math
C = \max H(y) - H(n) = \max H(x) - H(x | y)
```


Discrete: 
There is a residue of the discrete. From the Sampling Theorem (which Shannon gives his own perspective on in Communication in the Presence of Noise), Given that signals of limited bandwidth W can be perfectly reconstructed 

**How can a code be established?**

I am not the first to investigate theis question. For example, a modem connecting to an internet provider must perform a self-supervised learning algorithm to optimize its communication rate. (I learned about this here.) (Once the communication protocol is established, Shannon would characterize such a system as "mixed" ("continuous" / "discrete" -- perhaps "analog" / "digital" had not yet come into vogue.))

https://archive.org/details/bstj44-4-547

### 2.1 Crooks Fluctuation Theorem

In 

### 2.2 Statistical Physics of Replication

Jeremy England sets a lower bound on the heat output of reproducing systems in terms of four characteristics:
- v: Volume
- d: Durability
- r: Growth rate
- s: Entropy Production


### 2.3 Active Inference

The Free Energy Principle is a mathematical framework whose goal is to explain the emergence of agenctic behavior; thus it must represent agents in a sufficiently general-purpose way. To do so, it begins with a mathematical choice to partition reality into two sets of states, those "internal" to the agent or "system" (x) and those "external" to it (y); this partition could be regarded as an extrinsic definition of the system, made by a removed party who is studying it, e.g., an omniscient microbiologist who can infallibly discriminate between which parts of reality are inside and outside of single-celled bacterium under a microscope.

Given such a division, the FEP explores how, when, and why systems might minimize their surprise $-log(P(y))$. There is an immediate difficulty: how does X know about things that are by definition external to it? (There is another difficulty: a system can win by surrender, i.e. by forgoing its ability to even represent or register surprise, but this either is or quickly leads to the trivial solution of nonexistence.) It must form a model of external states using internal resources. (I will closely follow Ch. 4 of Thomas Parr, Giovanni Pezzulo, and Karl J. Friston, "Active Inference" (MIT Press, 2022))

```math
-logP(y) =  -log \left(\sum_x P(x, y)\right) \\
-logP(y) = -log \left(\sum_x P(x, y) \frac{Q(x)}{Q(x)} \right) \\
-logP(y) = -log\left( -\mathbb{E}_{x \sim Q(x)} \left( \frac{P(x, y)}{Q(x)}\right) \right) \\
-logP(y) \leq -\mathbb{E}_{Q(x)} log\left( \frac{P(x, y)}{Q(x)}\right) \\
- logP(y) \leq \mathbb{E}_{Q(x)} log \left(\frac{Q(x)}{P(x, y)}\right) =: F[Q(x), y]
```
In other words, F[Q, y] is defined to be the KL Divergence between an internal test distribution Q(x) and the true joint distribution of simultaneously occurring events (x, y). To minimize F[Q, y] is to minimize an upper bound on external surprise. Moreover, the expectation is taken with respect to Q(x), a function of internal states.

To restate:

```math
-log P(y) \leq F[Q, y] := D_{KL}(Q(x) || P(x, y))
```

Using the 

***2 forms of the Free Energy Principle***

Did I say "Principle?" It's really more like the Free Energy Conglomoration. This is because Variational Free energy F is minimized to bound surprise; however, Predictive Free Energy is Maximized to Choose Actions that 

***The Boundary Revisited***

It is true that 

Friston writes extremely eloquently:

> Under ergodic assumptions, the long-term average of surprise is entropy. This means that minimizing free
energy—through selectively sampling sensory input—places
an upper bound on the entropy or dispersion of sensory
states. This enables biological systems to resist the second law
of thermodynamics—or more exactly the fluctuation theorem
that applies to open systems far from equilibrium [14,15].
However, because negative surprise is also Bayesian model
evidence, systems that minimize free energy also maximize a
lower bound on the evidence for an implicit model of how
their sensory samples were generated. In statistics and machine
learning, this is known as approximate Bayesian inference and
provides a normative theory for the Bayesian brain hypothesis
[16– 20]. In short, biological systems act on the world to place
an upper bound on the dispersion of their sensed states,
while using those sensations to infer external states of the
world. This inference makes the free energy bound a better
approximation to the surprise that action is trying to minimize.

Several connections are in order:
1.  The fluctation theorems that Friston cites have since been simplified and extended in the seminal work of Gavin Crooks; moreover, bilding on this work, e.g., Jeremy England has provided simple characterizations of living systems that are compatible with thermodynamics; these would be 
2. Friston appears to be speaking directly to Shannon, from his original sentence which is the essential definition of entropy, to his statement re: evidence maximization. To wit,
A first way epistemic imperatives become apparent is during the minimiza-
tion of variational ­ free energy. One of the ways to decompose ­ free energy is to
express it as a Gibbs energy expected ­ under the approximate posterior minus
the entropy of the approximate posterior. In other words, the agent is striving
to increase entropy. While this seems paradoxical, the paradox dis­ appears if
one considers that this is the entropy of the agent’s (approximate posterior)
belief. This can be understood as the imperative to explain ­ things as accurately
as pos­ si­ ble but also “keep options open” and avoid committing to any specific
explanation ­ unless this is necessary—­ that is, the maximum entropy princi­ ple
( Jaynes 1957).
A second way epistemic dynamics become apparent is during the mini-
mization of expected ­ free energy, wherein—­ interestingly—­ there are two entro-
pies with opposite signs. ­ These include the posterior predictive entropy (how uncertain I am about what outcomes I would encounter given a choice) that
must be maximized—as for beliefs about states in the variational ­ free energy—and
the conditional entropy of outcomes given states (the ambiguity entailed
by a policy) that must be minimized. While during the minimization of varia-
tional ­ free energy the imperative is to maximize entropy of (pre­ sent) beliefs,
during the maximization of expected ­ free energy the imperative is to select
actions that minimize the ambiguity of (­ future) beliefs. This gives rise to epis-
temic, curious, novelty-­ seeking, and information-­ foraging be­ hav­ iors, which
support uncertainty resolution or improvement of the generative model—which
in turn minimizes surprise in the long run (Seth 2013; Friston, Rigoli
et al. 2015; Seth and Friston 2016; Schwartenbeck, Passecker et al. 2019).




***Self-evidencing***

> Any adaptive system that actively samples sensations to minimize varia-
tional ­ free energy is (equivalently) an agent that actively gathers evidence
for its generative model, aka a self-­ evidencing agent (Hohwy 2016). ­ These
systems are able to avoid dissipation, self-­ regulate, and survive by achieving
set-­ points provided by basic homeostatic pro­ cesses. [...]

> A generative model endowed with temporal depth opens the door to
the minimization of expected ­ free energy—or in psychological terms, plan-
ning. In Active Inference, this entails much more than increased adaptivity:
it entails at least a primitive form of agency. For an adaptive system, mini-
mizing expected ­ free energy is equivalent to having the (implicit) prior that
one is a ­ free energy minimizing agent—­ but acts to minimize ­ free energy in
the ­ future. When this (prior) belief enters the generative model, the adap-
tive system becomes able to form beliefs about how it should behave in the
­ future and which trajectories it ­ will pursue. In other words, it becomes able
to select among alternative ­ futures as opposed to simply selecting how to deal
with the sensed pre­ sent, as in the simplest agents described above. This tem-
poral depth therefore translates into a psychological depth. To ask about
the ways living creatures populate the continuum between the simplest
and most complex adaptive systems—­ and what forms of Active Inference
they can express—is an empirical question.

## 3 Non-equilibrium statistical mechanics (Langevin Equations)


Wishlist:

Notes on phenomenology / other theories of consciousness.
- Husserl (Ideas)
- Heidegger (Phenomenology of Time-Consciousness)
- Deleuze (Difference and Repetition)

Reading list:
- Shannon (Communication)
- Shannon (Noise)
- Crooks Fluctuation Theorem
- Jeremy England - Biology of Life
- Design of an optimal probe
- Bennet - Thermodynamics of Computational
- David Wolpert - Work, Entropy Production, and Thermodynamics of Information under Protocol Constraints Physics/ Computation-Thermodynamics-Constraints.pdf
- Theory of Usable Information Under Computational Constraints
- Assembly Theory
- "Prefrontal Working Memory and Hippocampal Epsiodic Memory: Unifying Memories Stored in Weights and Activation Slots."

Further leads:
- Activte Inference (Friston)
  - Perhaps this can be promoted to Interactive Inference.
- Spin Glass Theory and the Replica Trick
- Kardar Vol II. (Statistical Physics of Fields)
- Field theories of neural networks