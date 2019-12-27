## Fall 2019: Critterworld 
### Final Project CS 2112: Honors Object Oriented Design and Data Structures, Cornell University 
### by Shiyuan Huang and Felix Hohne 

___
**Abstract**

Our Final Project, approximately 10,000 lines of Java code, involved creating a simulation of a world of animals called critters that can move around, eat food, attack one another, reproduce, and evolve. These critters move on a 2-D hexagonal grid; when they move or perform actions, they use energy. When they run out of energy, they die and become food for other critters. The genome of each critter includes a program that determines what each critter does each turn under specific conditions. When critters mate or bud, this program is copied over to its offspring, possibly with mutations. 


We implemented: 

+ A Parser, Interpreter, and Fault Injector for a context-free grammar that represent the critter genomes
+ A simulator and Graphical User Interface to view the Critter World
+ A method that calculates the closest available food to a critter using Dijkstra’s Algorithm with a Priority Queue implemented using a Binary Heap
+ A multi-threaded, distributed application communicating over HTTP and using JSON, with the GUI running on a client computer and querying the server about the state of the world, and the model containing the simulation logic, parser, and interpreter on a server and responding to client requests via HTTP

While we are unable to show our actual code in order to protect academic integrity, we provide several examples of features we implemented.

___
**Spiral Critter** 

Here is an example of a program we wrote that causes a critter to spiral on a map. Our Parser parses the program written in the critter language, converts it into an Abstract Syntax Tree, then interprets the instructions based on conditions occurring in the world, as computed by the simulator. 

We did this by using the following context-free grammar to write our spiral critter program:

<img width="987" alt="Grammar" src="https://user-images.githubusercontent.com/58995473/71489313-4b45fb80-2825-11ea-8001-99c3bb8f9e4c.png">

Using the context-free gramar above, we wrote the following Spiral Critter Program, modified to protect academic integrity: 

<img width="1059" alt="newSpiral" src="https://user-images.githubusercontent.com/58995473/71490416-12a92080-282b-11ea-9e7a-65bb0c230dd5.png">

The Spiral Critter in Action: 

![SpiralVideo](https://user-images.githubusercontent.com/58995473/71511468-c5f93000-2892-11ea-8c83-155208a09357.gif)

___
**Graphical User Interface**

A key part of our assignment was to be able to visualize our simulation. When we originally wrote our simulation logic, we worked off a Command Line Interface. Here, the numbers represent critters and the direction they are pointing in, # represent rock tiles, F represent food tiles, and _ represent empty tiles. 

<img width="176" alt="NewCUIImage" src="https://user-images.githubusercontent.com/58995473/71511941-6a2fa680-2894-11ea-9877-7c727b47f639.png">

This naturally made it challenging to debug, test and appreciate the simulation in progress. We then developed a Graphical User Interface using JavaFX. This GUI is showing the same scene as above: 

<img width="1279" alt="GUIVersion" src="https://user-images.githubusercontent.com/58995473/71512451-82a0c080-2896-11ea-99b8-67dfd68bf14f.png">

In this Graphical User Interface, users can load custom worlds and critters they wrote using the File Menu, read through a simple tutorial using the question mark button, run the simulation step by step or at a continuous speed of up to 500 frames per second using the buttons at the bottom left, click on a critter and see its critter information including entire program and last executed rule on the right panel, and see the number of turns that this simulation has run and the number of critters that are alive. Here, Green tiles represent food tiles, light blue tiles represent empty tiles, arrows represent critters, and grey tiles represent rock hexes. We show the end of the world as an endless sea of rock hexes, so that users can never scroll off the edge of the map. 

Here is the GUI in action: 

![ActionGUI](https://user-images.githubusercontent.com/58995473/71513716-ce099d80-289b-11ea-92cd-d947f9e8077f.gif)


___
**Dijkstra's Shortest Path Algorithm**
To demonstrate our of Dijskstra’s Shortest Path Algorithm, we used it in game to enable the critter to find the closest food tile, including the number of turns that would be required to eat food directly in front of it. 

Here is an example of Dijsktra’s Algorithm in action: 

_TODO_

___

**Distributed Application and Thread Safety**

The final core part of the project was separating our Graphical User Interface from the simulation code, allowing the two to be run separately. Because of the Model-View-Controller design pattern, where the model has few, if any, references to the view and controller, this was relatively simple to accomplish; all that was required was to make the model code thread-safe, so that multiple threads could read the simulation state at the same time.

As a demonstration, we run two GUIs at the same time, with different permissions. The top GUI has admin permissions and can make modifications to the world, whereas the bottom GUI only has read-access to the world and therefore the play and pause buttons are greyed out. Despite having different zoom conditions and different permissions, the two GUIs display the same world state, except for perhaps some slight lag as HTTP requests arrive at the server at potentially delayed intervals: 

![NewConcurrency](https://user-images.githubusercontent.com/58995473/71516401-08c60280-28a9-11ea-8ed4-d4000686db15.gif)

