# Jason - AgentSpeak Logic (Part 2)
#### By Mahirul Islam

## Introduction

This article will provide a theoretical overview of the BDI framework, AgentSpeak and symbolic notation. In my PhD, we are working on a system where a symbolic Jason program works in-tandem with a **Deep Learning** (DL) network to produce something which combines the powerful DL function approximating with the safety and explainability of a symbolic agent. Not to self, make sure to drink enough **H<sub>2</sub>O**.

## About AgentSpeak

If you have coded in a mainstream language like Python, Java, JavaScript, C# etc, you would understand that they are all syntactically, functionally and structurally similar. For AgentSpeak, completely disregard the system that you are familiar with, because this language is unlike anything you have seen before.

> While not required for learning AgentSpeak, you can read the original scientific paper which conceptualised the language [here](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=a20352a44780acc63cce1417502088668bec5add). It also includes alot of mathematical/logical notation, so if you are familiar with such, it will greatly help.

This language was made by Anand Rao to make the "BDI" framework. BDI stands for Belief-Desire-Intention.

## What is BDI

Belief-Desire-Intention, or BDI is a framework to model computer agents. It is a logical system, which uses symbols. In this context of intelligent agents, a symbol is a way to represent any relationship between objects, represented as such:

```prolog
predicate(object_1, ... ,object_n)
```

This may sound very abstract. The "predicate" is the relationship that is being checked for, and the objects are that which are being checked for such relationship. For example: `inside(house, chair)` could be interpreted as *"the chair is inside the house"*. It is also not necessary that a symbol contains more than one object. For example: `prime(47)` could be interpreted as *"47 is prime"* (which is true). 

In Jason, these symbols are widely used to check for, acquire and replace **beliefs**. When you check the agent's beliefs, they are notated as symbols.

Desires are goals which the agent wants to achieve. Intentions are plans that the agent will take to meet its desires. In a way, intentions may be seen as a function of beliefs and desires: `I = f(B, D)`.

## Plans

To carry out a plan of "do_something", it is written as `!do_something.`. The exclamation mark **(!)** is Jason notation to define a plan. There is also a full-stop **(.)** after the statement. This acts similarly to a grammatical full-stop, to end a statement, similar to a semi-colon **(;)** in languages like Java or C++. 

Code which executes upon a plan being initiated follows this structure:

```
!do_plan.

+!do_plan : context <- action1; action2; ... ; actionX.
```

The plus **(+)** sign indicates that the code should be run upon recieving the plan. The **context**, which is followed by a colon (:), is additional information which must be met before the actions are executed. If the context returns false, then the rest of the code will not run, similar to how an if-statement will not run if the conditions are not met. 

As for the **actions**, this could include:
* Obtaining a belief,
* Executing a new plan,
* Performing a hard-coded function.
You will also notice that they are separated by semi-colons **(;)**. In this sense, they act grammatically like commas, separating elements of a list, with the final action being closed with a full-stop. 

### Hard-Coded Actions

The Jason framework provides some hard-coded functions not present in the base AgentSpeak, as quality-of-life features. They are written as: `.action(arguments).` where the initial full-stop **(.)** indicates that it's an action. In Jason, you can use `.print("text").` as a pre-defined action. This will log the text onto the **MAS Console** (I will explain what that is soon).

## Running your first application

In [part 1](mahir-islam.github.io/jason_guide_1), there is a guide on how set Jason up. If you haven't already, then I recommend that you give it a read. In other words:

```prolog
!read(part1).

+!read(part1) :
  not finished_reading(part1) <- goto("mahir-islam.github.io/jason_guide_1");
  finished_reading(part1).
```

Performing this command in the terminal:

```bash
jason app create project_name
```

Replace *project_name* with any name you wish. Then, in the appropriate filepath `/src/agt/`, have a look at either `bob.asl` or `alice.asl`, and you will find this code:

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

## Adding Beliefs

Beliefs are also indispensible for any Jason program. Suppose after saying "hello world", we want Bob to acknowledge that he followed through on the !start plan. We could add a belief like `finished_plan(start)` which he will remember. Suppose we also want the agent Alice to acknowledge her own existence ~(the robots are becoming sentient >:])~, we could give her a belief such as `i_am(alice)` upon completing !start.

In your `.asl` agent files, change Bob's plan to this:

```prolog
+!start : true <-
	.print("hello world.");
	+finished_plan(start).
```

Notice that the line to add the belief `finished_plan(start)` starts with a plus **(+)**. This is slightly different; it indicates that the agent should 'add' this belief to it's belief-base.

Likewise, for `alice.asl`, you would write `+i_am(alice)` on her plan as such:

```prolog
+!start : true <-
	.print("hello world.");
	+i_am(alice).
```

Now, if you run `jason project_name.mas2j` again, the console will appear the same. However, if you go on the MAS Console, click the **Debug** button, and click on the agents. You will see their beliefs present.

### Troubleshooting

| Problem | Solution |
| ------ | ------ |
| The Jason CLI is not responding | Try restarting your computer. If the issue still persists, use GitBash instead of Command Line. Read [chapter 1](mahir-islam.github.io/jason_guide_1)  for an installation guide |
| The MAS Console outputs "executing: <action>, but not implemented" | Make sure in the !start plan, actions are separated using semicolons, functions start with a full-stop, and the plan is also closed with a full stop  |
-----


## Summary

Now, you should be able to:

- [x] Create, run, and interpret plans 
- [x] Add and view beliefs
- [x] Print text to the console

### Other Chapters

[Chapter 1](mahir-islam.github.io/jason_guide_1)
[Chapter 2](mahir-islam.github.io/jason_guide_2)


