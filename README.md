# ICGT-2023

This repository contains the sources for [the paper](./paper.pdf) submitted
to [ICGT-2023](https://conf.researchr.org/home/icgt-2023) together with additional information
below.

**The corresponding tool is
available [here](https://bpmnanalyzer.whitefield-c9fed487.northeurope.azurecontainerapps.io).**

## BPMN Semantics formalization

Our [wiki](https://github.com/timKraeuter/Rewrite_Rule_Generation/wiki) describes the the BPMN formalization in more detail accompanied by many example BPMN models and graph transformation rule examples.

### Process termination

Process termination is implemented by the following graph transformation rule in Groove:

![Atomic property AllTerminated implemented in Groove.](./artifacts/Terminate.png)

The rule is called **Terminate** and is automatically added during graph grammar generation.
The dashed red borders mark parts of negative application conditions, grey parts remain untouched,
blue parts are
deleted and green parts are added.

## Model Checking BPMN

### BPMN-specific properties

BPMN-specific properties currently have to be checked in Groove due to an
unresolved [bug](https://sourceforge.net/p/groove/bugs/499/) and unfinished implementation.

- Make sure Java is installed on your machine to run Groove (tested with Java version 1.8.0_301)
- Clone/download this repository.
- Start Groove by running the following command in **this directory**:

```
java -jar artifacts\groove-5_8_1\bin\Simulator.jar
```

- Load a graph grammar. You can generate one using the tool below and unzip it on your local
  machine.
- Run LTL verification by copying one of the desired properties (listed below) and right-clicking in
  the LTS-Simulation
  tab. Select ```Verify < Check LTL property (full state space)``` and paste the copied LTL
  property.

![check ltl property](./artifacts/check_ltl.png)

#### Safeness

The atomic property **Unsafe** is implemented by the following graph condition in Groove:

![Atomic property Unsafe implemented in Groove.](./artifacts/Unsafe.png)

The property matches whenever two tokens of one process snapshot have the same position (but have
different identities).

#### Option to complete

The atomic property **AllTerminated** is implemented by the following graph condition in Groove:

![Atomic property AllTerminated implemented in Groove.](./artifacts/AllTerminated.png)

The property matches whenever there is no process snapshot in the state running. All process
snapshots are terminated, i.e., have no tokens.

### Custom properties

Defining atomic propositions directly in the tool by distributing tokens over the process model has
not been implemented yet.
Thus, for the time being, custom properties have to be checked in Groove by defining atomic propositions there.

## Implementation

### Tool

The tool is available
online [here](https://bpmnanalyzer.whitefield-c9fed487.northeurope.azurecontainerapps.io).

[![Atomic property Unsafe implemented in Groove.](./images/impl.png)](https://bpmnanalyzer.whitefield-c9fed487.northeurope.azurecontainerapps.io)

The sourcecode of the tool is
available [here](https://github.com/timKraeuter/Rewrite_Rule_Generation) and instructions
how to run it locally on your machine can be
found [here](https://github.com/timKraeuter/Rewrite_Rule_Generation/blob/master/server/README.md).

### Test suite

The [wiki](https://github.com/timKraeuter/Rewrite_Rule_Generation/wiki) describes our [comprehensive test suite](https://github.com/timKraeuter/Rewrite_Rule_Generation/wiki/Test-Suite) to test our coverage of BPMN features. 

Feel free to contact me for further information.
