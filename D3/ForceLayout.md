这个模块实现了用以模拟粒子物理运动的velocity Verlet数值积分器。

甚至可以用来作为一个基本的物理引擎。

Broadly speaking there are 4 steps 

We can define own force functions but D3 comes with a number of useful ones built in:

The strength of the attraction or repulsion can be set using `.strength()` 

`d3.forceSimulation([nodes])`

Creates a new simulation with the specified array of nodes and no forces.

The simulator starts automatically.

Use *simulation.on* to listen for tick events as the simulation runs.

If you wish to run the simulation manually instead, call *simulation.stop*, and then call *simulation.tick* as desired.

`simulation.nodes([nodes])`

If nodes is not specified, returns the simulation's array of nodes as specified to the constructor.

A *force* is simply a function that modifies nodes' positions or velocities;

### Centering

The centering force translates nodes uniformly so that the mean position of all nodes (the center)

`d3.forceCenter([x, y])`

Creates a new centering force with the specified *x-* and *y-* coordinates.

If *x* and *y* are not specified, they default to <0,0>.