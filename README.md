# COP5615 Assignment - Project 2

## Gossip and Push-Sum Algorithm on different Network Topologies

### Group Members: 

Sunny Dhama, UFID: 4328-6076, sunny.dhama@ufl.edu
Jagannath Jayanti, UFID: 1856-7125, jjayanti@ufl.edu

---

## Source file location:

project1/root_supervisor.erl

---

## Usage

1.  cd to the `project1` folder
2.  Run erlang console

```bash
erl
```

2.  Compile all required files

```bash
c(root_supervisor).
c(server).
c(client).
c(worker).
```

3.  Run

```bash
erl -smp enable -sname root -setcookie sunnydhama -pa ebin -s root_supervisor main [k | ip_addr]
```

examples

```bash
erl -smp enable -sname root -setcookie sunnydhama -pa ebin -s root_supervisor main 10.20.52.41
erl -smp enable -sname root -setcookie sunnydhama -pa ebin -s root_supervisor main 6
```

4. Please see example images in this folder.

---

## Implementation Details

For local implementation follow the Usage guidelines above.

```bash
erl -smp enable -sname root -setcookie sunnydhama -pa ebin -s root_supervisor main [k | ip_addr]
```

where `k=number of leading zeros` for the generated bitcoins required.  
`ip_addr= IP Address of the server` you want to connect to, in this case the local machine acts aa a miner

## What is Working ?

In the project, all the required topoligies i.e, Full Network, 2D Grid, Line, Imperfect 3D Grid are successfully implemented with both the algorithms - Gossip and Push Sum. In both the alorithms, convergence was obtained for all the nodes. 

### Convergence for each algorithm

1. Gossip Algorithm - The network is said to converge in gossip algorithm when each node of the network has converged. Subsequently, a node converges when it hears or receives the message 10 times. Once a node converges it stops sending or transmitting the messages forwared. 

2. Push-Sum Algorithm - In a network following the push-sum protocol, each node/actor converges when it's s/w ratio does not change more than 10^-10 for 3 consecutive times the actor recieves and updates it s and w values.


## What is the largest network you managed to deal with for each type of topology and algorithm ?

In both Gossip and Push Sum algorithm the largest that was successfully implemented comprised of 10 thousand nodes in all the four given network topologies. 

The reason for choosing the same number of nodes in all topologies was that the performance of each could be compared and measured against others.



## Assignment Details

### Implementation

For implementing the project, a hierarchical design approach was followed. The main component of the system is the supervisor under which the other modules are created, each responsible for one aspect of the network. These are as follows:

1. Driver / Gen Server
2. Sub-Supervisor
3. Node Supervisor
4. Nodes
5. Topologies


#### Input

For Gossip with line topology

```bash
erl -noshell -s main_sup start 10000 line gossip
```

Here, 10000 represent the number of nodes, "line" represents the topology and "gossip" represents the algorithm or protocol to be followed.

#### Output

```bash

------BEGIN gossip------
NumNodes: '10000', Topology: line, Algorithm: gossip
Time for convergence: 667ms 
------END "gossip"------

```






