# Terminal Scavenger Hunt

## About this Activity

In this class, you will need to have a basic understanding of how to navigate the terminal. The goal of this scavenger hunt is to familiarize yourself with some of the terminal commands we will be using in this course. 

## Objective

The game is simple: each team will be assigned a unique keyword they must find to finish the hunt. You and your team must navigate through the files in this directory, searching for clues. Follow the clues to be the first to find your keyword, earning the eternal admiration of your classmates. 

## A Note on File Hierarchy

Computers organize folders and files into something known as a **file hierarchy**. The specifics of your file hierarchy will depend on what operating system you are using, but things generally begin with what's known as a **root directory** (AKA home directory). This directory, sometimes symbolized with a `~`, is the "mother of all folders," meaning all of your other folders and files will live inside of the root directory. This is also a great time to let you know that the word **directory** is just another word for folder. The two terms can be used interchangeably. For example, the file hierarchy on your computer might look something like this:

```
| home/
|-- jovyan/
|  | summer2024/
|  |--| csci2270/
|  |  |--| assignments/
|  |  |  |--| assignment1.cpp
|  |  |  |--| assignment2.cpp
|  |  |--| notes/
|  |  |  |--| lecture1.txt
|  |  |--| syllabus.txt
|  |--| math2350/
```

In the above example, anything ending with a `/` is a directory, and everything else is a file. Levels of directory nesting are represented with tabs. For instance, both the `assignments/` and `notes/` directories live inside of the `csci2270/` directory, which itself lives inside of `summer2024/`. For the remainder of the explanation below, we'll use the file hierarchy above.

Any time we interact with the terminal, we are operating somewhere within our file hierarchy. In some ways, the file hierarchy *is* your computer. 


## Basic Terminal Commands Overview

When we execute terminal commands, we do so by typing the command into the prompt. On JupyterHub, the prompt will look something like this:

```console
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270$
```

You can always figure out where you are currently located in your file hierarchy by reading the prompt above. Everything that comes after the `:` symbol lists out your current location in your file hierarchy. For example, in the above scenario we would be in our `csci2270` folder:

```
| home/
|-- jovyan/
|  | summer2024/
|  |--| csci2270/*
|  |  |--| assignments/
|  |  |  |--| assignment1.cpp
|  |  |  |--| assignment2.cpp
|  |  |--| notes/
|  |  |  |--| lecture1.txt
|  |  |--| syllabus.txt
|  |--| math2350/
```

\* = you are here

Before you get started, you'll need to know a few basic terminal commands:

**pwd** <br/>
`pwd` stands for "print working directory." The working directory is the folder inside of which you are currently operating.  

Example:

```console
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270$ pwd
/home/jovyan/summer2024/csci2270
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270$
```

**ls**

`ls` stands for "list." This command will list all of the folders and files that are stored within your working directory. 

Example:

```console
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270$ ls
assignments     notes     syllabus.txt
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270$
```

**cd**

`cd` stands for "change directory." You can use this command to get around inside the terminal. `cd` supports both *relative* and *absolute* pathing. What are relative and absolute pathing? Great question!

*Relative* pathing refers to the practice of giving the path of the directory to which you want to go relative to where you are now. Think of it like giving directions to a friend. If you're telling them how to get to the cafe from the classroom, you might just say "Go left, then take your first right, walk straight for a bit and then go right again." You just gave your friend directions to the cafe *relative* to their current position.  

Example:
```console
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270$ cd assignments
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270/assignments$ ls
assignment1.cpp     assignment2.cpp     
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270/assignments$
```

*Absolute* pathing refers to the practice of giving the entire path of the directory to which you want to go, regardless of where you currently are now. Using the example from before, this is like telling your friend "Starting at the entrance to the Engineering center, go up the stairs, then take a left, walk straight for a bit, ..." For the terminal, absolute pathing starts from the root directory. This can be useful when the directory you want to get to is located far away from where you are currently operating. Sometimes it's easier just to go back to the root and find the folder from there.

Example:
```console
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270$ cd ~/summer2024/csci2270/assignments
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270/assignments$ ls
assignment1.cpp     assignment2.cpp     
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270/assignments$
```

Both of the examples above will achieve the same outcome: we are now located in our `assignments/` directory. 


```
| home/
|-- jovyan/
|  | summer2024/
|  |--| csci2270/
|  |  |--| assignments/*
|  |  |  |--| assignment1.cpp
|  |  |  |--| assignment2.cpp
|  |  |--| notes/
|  |  |  |--| lecture1.txt
|  |  |--| syllabus.txt
|  |--| math2350/
```

\* = you are here

The `cd` command supports all kinds of fancy operations, especially when combined with relative pathing. For example, we can type `cd ..` to move up one folder from where we are now. If we typed `cd ../..`, we would move *two* folders up from where we are now. This is nice when you want to back out of one folder and then immediately enter into another. 

Example:
```console
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270/assignments$ cd ../notes
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270/notes$ pwd
home/jovyan/summer2024/csci2270/notes
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270/notes$
```

If you ever get lost, you can go back to your root directory by using the command `cd ~`.

Example:
```console
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270/notes$ cd ~
jovyan@jupyter-IDENTIKEY:~$
```

```
| home/
|-- jovyan/*
|  | summer2024/
|  |--| csci2270/
|  |  |--| assignments/
|  |  |  |--| assignment1.cpp
|  |  |  |--| assignment2.cpp
|  |  |--| notes/
|  |  |  |--| lecture1.txt
|  |  |--| syllabus.txt
|  |--| math2350/
```

\* = you are here

**rm**

The `rm` command stands for "remove." This command is used to delete files or folders. This command will also support absolute and relative pathing. 

Example:
```console
jovyan@jupyter-IDENTIKEY:~$ rm summer2024/csci2270/assignments/assignment1.cpp
jovyan@jupyter-IDENTIKEY:~$ cd summer2024/csci2270/assignments
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270/assignments$ ls
assignment2.cpp     
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270/assignments$
```

Our new file hierarchy will look like this:

```
| home/
|-- jovyan/
|  | summer2024/
|  |--| csci2270/
|  |  |--| assignments/*
|  |  |  |--| assignment2.cpp
|  |  |--| notes/
|  |  |  |--| lecture1.txt
|  |  |--| syllabus.txt
|  |--| math2350/
```

\* = you are here

If we want to delete a non-empty folder, we need to add a special `-r` instruction to the `rm` command. The `-r` stands for "recursive." This tells the terminal to delete the folder and everything else inside of it.

```console
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270/assignments$ cd ..
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270$ rm -r notes
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270$ ls
assignments     syllabus.txt     
jovyan@jupyter-IDENTIKEY:~/summer2024/csci2270$
```

Our new file hierarchy will look like this:

```
| home/
|-- jovyan/
|  | summer2024/
|  |--| csci2270/*
|  |  |--| assignments/
|  |  |  |--| assignment2.cpp
|  |  |--| syllabus.txt
|  |--| math2350/
```

\* = you are here

**Caution:** You may be aware of the `rm -rf` command. The `f` stands for "force." Using this command without discretion can cause you to accidentally delete folders that you do not want gone.

**More Commands**

There are many more commands available for you to use on the terminal than what we've discussed here. Check out this [guide to more terminal commands](https://gist.github.com/bradtraversy/cc180de0edee05075a6139e42d5f28ce).

## The Hunt Begins!

Now that you're familiar with the basics of the terminal, it's time to begin the hunt! Here's the first clue:

```
CLUE 1 HERE
```

Use the terminal commands from above to start searching through files and follow your first clue. 

## End Conditions

The scavenger hunt ends when you find the final clue. Bring your final clue to the instructor to win!