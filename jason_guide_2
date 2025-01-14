# Jason - AgentSpeak Logic
#### By Mahirul Islam

## About AgentSpeak

If you have coded in a mainstream programming language, like Python, Java, JavaScript, C# etc, you would understand that they are all syntactically, functionally and structurally similar. Now for AgentSpeak, completely disregard the system that you are familiar with, because this language is unlike anything you have seen before. 

My PhD project involves using AgentSpeak to create autonomous agents as part of my research. We are using a program called Jason, as an interpreter. I am writing this guide to help save time for other people who wish to learn AgentSpeak. First, to download this program onto your computer, [follow this guide here.](https://jason-lang.github.io/doc/tutorials/vscode/readme.html). 

To summarise the installation guide **(for Windows)**:

- Make sure you have Java installed.
- Download Jason from GitHub [here](https://github.com/jason-lang/jason/releases). Make sure you choose the **.zip** fle. Unzip the file, then you will see a **bin** file.
- Copy and paste that bin file directory, then open the Environmental Variables window. On the **System Variables (the one on the bottom, not the top)**, select the “Path” variable.
- Press “New”, then paste the filepath.
- To test whether the installation is successful, type `jason` into your terminal, and it should display a message.

### Issues

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
