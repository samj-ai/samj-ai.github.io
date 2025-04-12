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

Given ergodic distributions of a source, we can derive that the maximum bits per symbol that can be transmitted on a channel with fixed discrete alphabet is C/H :

```math
C = \lim_{T\rightarrow \infty} N(t) \\
H = -\sum_{i=1}^N p_i log_2 p_i 
```




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
- Theory of Usable Information Under Computational Constraints
- Assembly Theory
- "Prefrontal Working Memory and Hippocampal Epsiodic Memory: Unifying Memories Stored in Weights and Activation Slots."

Further leads:
- Activte Inference (Friston)
  - Perhaps this can be promoted to Interactive Inference.
- Spin Glass Theory and the Replica Trick
- Kardar Vol II. (Statistical Physics of Fields)
- Field theories of neural networks