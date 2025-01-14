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
predicate(object_1 ... object_n)
```

This may sound very abstract. The "predicate" is the relationship that is being checked for, and the objects are that which are being checked for such relationship. For example: `inside(house, chair)` could be used to be interpreted as "the chair is inside the house". It is also not necessary that a symbol contains more than one object. For example: `prime(47)` could be interpreted as "47 is prime" (which is true). 

In Jason, these symbols are widely used to check for, acquire and replace **beliefs**. 

Desires are goals which the agent wants to achieve. Intentions are plans that the agent will take to meet its desires. In a way, intentions may be seen as a function of beliefs and desires: I = f(B, D).

## Plans

To carry out a plan of "do_something", it is written as `!do_something.`. The exclamation mark (!) is Jason notation to define a plan. There is also a full-stop (.) after the statement. This acts as similarly to a grammatical full-stop, to end a statement, similar to a semi-colon (;) in languages like Java or C++. 

Code which executes upon a plan being initiated follows this structure:

```
!do_plan.

+!do_plan : context <- action1; action2; ... ; actionX.
```

The plus (+) sign indicates that the code should be run upon recieving the plan. The context, which is followed by a colon (:), is additional information which must be met before the actions are executed. As for the actions, this could include: obtaining a belief, executing a new plan, or performing a hard-coded function. You will also notice that they are separated by semi-colons (;). In this sense, they act like commas, separating elements of a list, with the final action being closed with a full-stop.

## Plans

| Problem | Solution |
| ------ | ------ |
| There is no bin file | Make sure you have installed the .zip file from Github. |
| The Jason CLI is not responding | Try restarting your computer. If the issue still persists, use GitBash instead of Command Line. |

-----

## Your first Jason Project

> I recommend that you download GitBash as your terminal. It’s like Command Line, but has more features, and if you are already familiar with Linux, the commands are the same. When I mention the “terminal”, I will be referring to the GitBash terminal.

Open a folder where you want to store your Jason projects, then open the terminal and write this command:

```sh
jason app create first_project
```

You can change `first_project` to any name you wish for your project. Using an IDE of your choice (VSCode, Sublime Text, etc), open the directory. You will see a file with the **.mas2j** extension. This file is used to execute the program which you will make. 

To run the project, open the terminal in the project directory and execute this command:

```sh
jason first_project.mas2j
```
Where *first_project* is the name of your Jason project. A GUI window will open, where the default agents: *bob* and *alice* will both say “hello world”.

-----

## Project Format

By default, the **.mas2j** file will have this boilerplate code:

```java
MAS first_project {

    environment: example.Env(10)

    agents: bob;
            alice;

    aslSourcePath: "src/agt";
}
```

MAS stands for **multi-agent system**. The environment refers to the Java file *Env.java* which you may find in `project_name/src/env/example/Env.java`. The agents listed: **bob** and **alice**, are those which will be called during the runtime. Finally, `aslSourcePath` is the directory of the agents. In this case, go to `project_name/src/agt/`.

You will see two **.asl** files. ASL is the extension for AgentSpeak code. This is also where the agent logic is located. If you open `bob.asl`, you will find this code:

```prolog
!start.

+!start : true <- .print("hello world.").
```

…which is what caused Bob to say “hello world”. Alice also has the same code.

For the line: `!start.` the exclamation mark **!** is used to represent a plan. In this case, the plan is called **start**. The full stop **.** after the **!start** plan closes the statement. In a way, it is similar to semi-colon ; of C# or Java.
