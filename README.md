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

The Spiral Critter in Action: 

![SpiralVideo](https://user-images.githubusercontent.com/58995473/71511468-c5f93000-2892-11ea-8c83-155208a09357.gif)

We did this by using the following context-free grammar to write our spiral critter program:

<img width="987" alt="Grammar" src="https://user-images.githubusercontent.com/58995473/71489313-4b45fb80-2825-11ea-8001-99c3bb8f9e4c.png">

Using the context-free gramar above, we wrote the following Spiral Critter Program, modified to protect academic integrity: 

<img width="1059" alt="newSpiral" src="https://user-images.githubusercontent.com/58995473/71490416-12a92080-282b-11ea-9e7a-65bb0c230dd5.png">

___
**Graphical User Interface**

_TODO_

___
**Dijkstra's Shortest Path Algorithm**
To demonstrate our of Dijskstra’s Shortest Path Algorithm, we used it in game to enable the critter to find the closest food tile, including the number of turns that would be required to eat food directly in front of it. 

Here is an example of Dijsktra’s Algorithm in action: 

_TODO_

**Distributed Application**

_TODO_
