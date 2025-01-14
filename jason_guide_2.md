# Jason - AgentSpeak Logic
#### By Mahirul Islam

## Introduction

This article will provide a theoretical overview of the BDI framework, AgentSpeak and symbolic notation.

## About AgentSpeak

If you have coded in a mainstream language like Python, Java, JavaScript, C# etc, you would understand that they are all syntactically, functionally and structurally similar. For AgentSpeak, completely disregard the system that you are familiar with, because this language is unlike anything you have seen before.

> While not required for learning AgentSpeak, you can read the original scientific paper which conceptualised the language [here](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=a20352a44780acc63cce1417502088668bec5add). It also includes alot of mathematical/logical notation, so if you are familiar with such, it will greatly help.

This language was made by Anand Rao to make the "BDI" framework. BDI stands for Belief-Desire-Intention.

## What is BDI

Belief-Desire-Intention, or BDI is a language to model computer agents. It is a logical system, which uses symbols. In this context of intelligent agents, a symbol is a way to represent any relationship between objects, represented as such:

```prolog
predicate(object_1, ... ,object_n)
```

This may sound very abstract. The "predicate" is the relationship that is being checked for, and the objects are that which are being checked for such relationship. For example: `inside(house, chair)` could be interpreted as *"the chair is inside the house"*. It is also not necessary that a symbol contains more than one object. For example: `prime(47)` could be interpreted as "47 is prime" (which is true). 

In Jason, these symbols are widely used to check for, acquire and replace **beliefs**. 

Desires are goals which the agent wants to achieve. Intentions are plans that the agent will take to meet its desires. In a way, intentions may be seen as a function of beliefs and desires: I = f(B, D).

## Plans

To carry out a plan of "do_something", it is written as `!do_something.`. The exclamation mark **(!)** is Jason notation to define a plan. There is also a full-stop **(.)** after the statement. This acts as similarly to a grammatical full-stop, to end a statement, similar to a semi-colon **(;)** in languages like Java or C++. 

Code which executes upon a plan being initiated follows this structure:

```
!do_plan.

+!do_plan : context <- action1; action2; ... ; actionX.
```

The plus (+) sign indicates that the code should be run upon recieving the plan. The context, which is followed by a colon (:), is additional information which must be met before the actions are executed. As for the actions, this could include: obtaining a belief, executing a new plan, or performing a hard-coded function. You will also notice that they are separated by semi-colons **(;)**. In this sense, they act like commas, separating elements of a list, with the final action being closed with a full-stop. 

### Hard-Coded Actions

The Jason framework provides some hard-coded functions not present in the base AgentSpeak, to help with quality-of-life. They are written as: `.action(arguments).` where the initial full-stop **(.)** indicates that it's an action. In Jason, you can use `.print("text").` as a pre-defined action. This will log the text onto the **MAS Console** (I will explain what that is soon).

## Running your first application

On [part 1](mahir-islam.github.io/jason_guide_1), there is a guide on how set Jason up. If you haven't already, then I recommend that you give it a read. Performing this command:

```bash
jason app create project_name
```

Replace *project_name* with any name you wish. Then in the appropriate filepath `/src/agt/`, have a look at either `bob.asl` or `alice.asl`, and you will find this code:

```prolog
/* Initial goals */
!start.

/* Plans */
+!start : true <- .print("hello world.").
```

You should now be able to interpret this:
* `!start.` - Implement the plan called "start",
* `+!start :` - If the plan "start" is implemented,
* `true <-` - The context returns true, so proceed,
* `.print("hello world.").` - Perform the action of printing "hello world"

To see this in action, go to the base directory of the project, then run in your terminal:

```bash
jason project_name.mas2j
```

This will open a Java GUI known as the **MAS Console**, where both Bob and Alice will say "hello world.".
