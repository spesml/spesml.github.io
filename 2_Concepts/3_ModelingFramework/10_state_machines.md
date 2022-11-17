---
layout: default
title: State Machines
nav_order: 10
parent: SpesML Modeling Framework
grand_parent: SpesML Concepts
permalink: /concepts/modeling_framework/state_machines.html
---
<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

<script>
  MathJax = {
    tex: {
      inlineMath: [['$', '$']]
    }
  };
</script>

# State Machines 

The semantic interface of atomic system elements can, inter alia, be defined by state machines (non-deterministic Mealy Machines). 
To this effect, the system element can be linked to the state machine that defines its behaviors. Each state machine linked to a system element must have the same input 
and output channels as the system element. The following introduces a reduced abstract syntax for state machines. The syntax can easily be 
extended by guards on transitions, hierarchical states, and further advanced concepts. However, every practically meaningful (weakly-causal and realizable) 
semantic interface can be modeled with a state machine solely using the reduced abstract syntax. Thus, it is always possible to transform a state machine in an extended syntax
to a semantically equivalent state machine in the reduced abstract syntax.    

As depicted in the following figure, each state machine consists of 
* states,
* initial states, 
* transitions, 
* input channels, and 
* output channels. 

Each transition consists of 
* a source state, 
* a target state, 
* an assignment mapping each input channel of the automaton to a finite stream of messages of the channel's type, and
* an assignment mapping each output channel of the automaton to a finite stream of messages of the channel's type.  

<div align="center">
<img width="500" src="statemachine.png">
<br><b>Figure:</b> 
Concepts of the reduced abstract syntax for state machines.
</div><br>

For a state machine to be meaningful, it must define a possible output for all possible inputs for each of its states. 
Otherwise, the behavior of the state machine could be undefined for some inputs. 
This even holds in case the state machine should not react to some input in some state at all, neither by changing its state nor by sending messages. 
In implementations, omitting explicit reactions can be interpreted as syntactic sugar for some default behavior or for arbitrary behavior. 
However, when considering the reduced abstract syntax, the following rule of well-formedness applies: 
For each state and each possible input channel assignment (mapping the input channels to finite streams of the channels' types), 
the state machine must contain at least one transition that starts in the state and has the input channel assignment. 

A run of a state machine represents the behavior of the state machine in response to received input and progressing time. A run of the state machine starts
in one of its initial states. Afterwards, the state machine receives inputs on its input channels and the time progresses. 
In each time unit, the state machine receives inputs via its input channels. 
When the time unit ends, the state machine changes its state based on a transition that (1) starts in its current state and (2) is enabled by the input received in the current time unit. 
The transition is enabled if the received streams on the input channels are equal to the streams for the channels as defined by the input channel assignment of the transition. 
When taking such a transition, the state machine outputs the messages as specified by the output channel assignment of the transition on its output channels and changes its state to the transition's target state.
In the next time unit, it proceeds analogously in its updated state. 

The communication history produced by a run is defined by the streams of messages that are communicated via the channels of the state machine during the run. 
Thus, communication histories abstract from the internal state changes that are not observable to the environment of state machines. 
Thus, communication histories represent a black-box view on runs of state machines where each communication history solely contains the information available to the environment of the state machine. 
The relation between the possible input and output communication histories of all runs of a state machine induce the state machine's semantic interface. 
With this, the semantic interface of a state machine is the function relating all possible input channel communication histories to all possible output channel communication histories as defined by the state machine.

The semantic interface of a state machine is guaranteed to be weakly causal. 
In case the state machine is a Moore Machine, the semantic interface is even strongly causal.
A Moore Machine is a state machine where the output of each transition solely depends on the source state of the transition and not on the current input.
Thus, all transitions originating from a state have the same output. In an implementation, requiring an initial output for a state machine and making the state machine
directly react to received inputs ensures that its behavior is strongly causal. From a theoretical viewpoint, this state machine can be translated to a Moore machine.  

## Mealy and Moore Machines

The behavior of a system element with syntactic interface $I \blacktriangleright O$ in the univeral interface model can be described using a state machine, more specifically a non-deterministic _Mealy Machine_ (_Moore Machine_ in case of strongly causal behavior).

A Mealy Machine is a tuple $(\Sigma, I,O, \Lambda, \Delta)$ where
- $\Sigma$ is a set of states,
- $I \blacktriangleright O$ is a syntactic interface,
- $\Lambda\subseteq \Sigma$ is a non-empty set of initial states, and 
- $\Delta \subseteq \Sigma \times (I\rightarrow M^*) \times (O\rightarrow M^*) \times \Sigma$ is a transition relation, relating a state and the inputs delivered to the machine to a follow-up state and output produced by the machine in this step. In case of a non-deterministic Mealy Machine, there may be several follow-up states and outputs related to a source state and input.
- The machine is required to be reactive, i.e., it holds that there exists a state $v \in \Sigma$ and an output $o: O \rightarrow M^* $ such that $(u,i,o,v) \in \Delta$ for all $u\in \Sigma$ and $i: I \rightarrow M^*$ such that 
$i(c) \in t$ if $c:t$ for all $c \in I$.
- The messages assigned to channels in transitions must be elements of the channels' types, i.e., it holds that $i(c) \in t$ if $c:t$ for all $c \in I$ and $(u, i, o, v) \in \Delta$. Similarly, it holds that $o(c) \in t$ if $c:t$ for all $c \in O$ and $(u, i, o, v) \in \Delta$.

The reactivity condition is important to ensure that the machine can react to every possible input in each of its states. 

A Mealy Machine $(\Sigma, I,O, \Lambda, \Delta)$ is said to be a Moore Machine iff there exists 
$ v' \in \Sigma  $ such that $ (u,i', o, v') \in \Delta $ for all $ (u,i,o,v) \in \Delta $ and $ i': I \rightarrow M  $ such that $ i(c) \in t $ if $ c : t $ for all $ c \in I $. 
In each of its states, the possible outputs of a Moore Machine solely depends on the state and not on its current inputs. However, the target states of different transitions originating in the same state may differ.
As Moore Machines are special Mealy Machines, all properties of Mealy Machines also hold for Moore Machines. 

A run $r$ of a Mealy Machine $(\Sigma, I,O, \Lambda, \Delta)$ is an infinite sequence of transitions $r = t_0, t_1, ... \in \Delta^\infty$ where $ t_j = (u_j, i_j, o_j, v_j) $ for all $ j \in \mathcal{N}$ such that 
- $u_0 \in \Lambda$ and
- $u_{j+1}  = v_j$ for all $ j \in \mathcal{N}$.

The first condition in the definition of run states that the machine starts in one of its initial states. 
The second condition states that the source state of a proceeding transition is the target state of its preceeding transition.
Thus, after taking a transition, the machine proceeds its computation in the target state of the transition. 

The behavior of a run $r = t_0, t_1, ... \in \Delta^\infty$ where $ t_j = (u_j, i_j, o_j, v_j) $ for all $ j \in \mathcal{N}$ is defined as the tuple $(i,o) $ where $i = i_0, i_1, ... $ and $o = o_0, o_1, ... $.
Thus, the behavior is the tuple modeling the relationship from the received inputs to the produced outputs of the machine.

The semantic interface of a Mealy Machine $M = (\Sigma, I,O, \Lambda, \Delta)$ is defined as the function $F: \overrightarrow{I}\rightarrow \wp (\overrightarrow{O})$ satisfying $ F(i) = \{ b|O : b \text{ is the behavior of a run of } M \wedge b|I = i \} $ for all $i \in \overrightarrow{I}$.
By construction, the semantic interface of each Mealy Machine is always a well-defined weakly causal function. If the Mealy Machine is even a Moore Machine, then the semantic interface is even guaranteed to be strongly causal.

## Timed-Event State Machines 
Timed-event state machines transition on the occurance of an event, which may be messages on incoming channels. A transition can be taken if an incomign message upholds the transition's precondition. Taking a transition does not denote the end of the current time slice, instead time is encoded in message streams. One possibility is to encode time in message streams is the addition of a special symbol $\checkmark$ called a tick. A tick denotes the end of a time slice. 

Timed-event state machines consum messages on input streams immediately if these are not ticks. Ticks block an incoming channel until ticks are present on all incoming channels, whereupon all ticks are consumed at once and ticks are sent on all outgoing channels, marking the end of the current time slice.

We update the definition of the transition relate from above and add ticks to inputs and outputs:

$\Delta \subseteq \Sigma \times (I\rightarrow M^* \cup \{\checkmark\}) \times (O\rightarrow M^* \cup \{\checkmark\}) \times \Sigma$

Similarly, the definition of a run of a timed-event state machine $(\Sigma, I,O, \Lambda, \Delta)$ is an infinite sequence of transitions $r = t_0, t_1, ... \in \Delta^\infty$ where $ t_j = (u_j, i_j, o_j, v_j) $ for all $ j \in \mathcal{N}$ such that 
- $u_0 \in \Lambda$,
- $u_{j+1}  = v_j$ for all $ j \in \mathcal{N}$ and
- $\exists k \in M^*$ such that $u_j = k : \checkmark$

## Time-Slice State Machines with Input Patterns
In this section, we extend the Mealy Machines introduced before with the notion of input patterns. The core idea is to allow transitions to specify not a single allocation of message sequences to channels, but instead to define a pattern or predicate on channel allocations. A transition can be taken, if the messages on the input channels in a given time-slice matches the pattern.

In the following we define input patterns not only for a single channel, but for an allocation of messages to a set of channels $C$. 
A patern in this sense is given by predicate $P:(C\rightarrow M^*)\rightarrow \mathbb{B}$. 

With this definition we can update the definition of the transition relation from above as:

$\Delta^p \subseteq \Sigma \times P_I \times (O\rightarrow M^*) \times \Sigma$, where $P_I$ denotes the set of patterns for channel set $I$. 

Similarly, we can update the definition of a run as follows:
A run $r$ of a Mealy Machine $(\Sigma, I,O, \Lambda, \Delta)$ is an infinite sequence of transitions $r = t_0, t_1, ... $ where $ t_j = (u_j, i_j, o_j, v_j) $ for all $ j \in \mathcal{N}$ such that 
- $u_0 \in \Lambda$ and
- $\forall j \in \mathbb{N}: \exists (u,p,o,v) \in \Delta^p: u=u_j \wedge v=v_j \wedge o=o_j \wedge p(i_j)$.

The definitions of behavior and causality carry over to the updated definition. 

In order to specify input patterns we may employ notation for first-order logic including the usual operations e.g. for streams and arithmetic. However, as an alternative we suggest to use notations for specifying predicates on sequences, for example regular expressions or linear temporal logic restricted on finite sequences ($\mathit{LTL}_f$)[1].

For exmaple, to specify that for input channel $i$ we received a sequence beginning with message $m$ and ending with message $n$ we may write the following regular expression: 

$p = \hat{}\;m.*\$$

where $\hat{}$ matches the beginning of the sequence, $\$$ matches the end of the sequence and $.*$ matches a arbitrary but finitely long subsequence of any messages. 

As a second example consider the same pattern formulated in $\mathit{LTL}_f$

$p = m \wedge \diamond(n \wedge \mathit{Last})$

where $\diamond \varphi$ denotes that $\varphi$ will hold at some instant in the future and $\mathit{Last}$ is a predicate which is only true for the last element of the sequence (equivalent to $\circ \neg \mathit{true}$, where $\circ \varphi$ is true if $\varphi$ is true in the next step)
