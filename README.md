# ModelNetlist


## Introduction

This repository contains a simple model for representing netlists(electronic circuits). It is developed for educational purposes hence favors simplicity over performance. The attempt is to develop a simple model which can completely describe a netlist. SimpleNelist is using [NetworkX](https://networkx.github.io/) which is a more generic graph representation written in Python.

ModelNetlist can be used to learn how algorithms are written in EDA(Electronic Design Automation). Under applications/ there are several examples on how to write algorithms to extract information about a netlist. More detailed explanation of the application and its implementation is present in the README in each application folder.

This model is used by [ChipHackers](https://chiphackers.com) for their EDA related challenges. Try solving those challenges to get more familiar on how to use ModelNetlist model.


## Installation

Currently only method to start using ModelNetlist is through GitHub repository. Please use below BASH commands to setup the enviorment. Windows users can set the PYTHONPATH variable appropriately.

```sh
cd <clone directory>

git clone https://github.com/udara28/ModelNetlist.git

export PYTHONPATH="<clone directory>/ModelNetlist"
```

## Usage

### Simple Example

#### Generating a netlist


```python
from ModelNetlist import *

netlist = ModelNetlist('top1')

and1 = AND2(netlist)
netlist.addCell(and1)

or1 = OR2(netlist)
netlist.addCell(or1)

inv1 = INV(netlist)
netlist.addCell(inv1)

net1 = Net(netlist)
net1.addDriver(and1.output(0))
net1.addLoad(or1.input(0))
netlist.addNet(net1)

net2 = Net(netlist)
net2.addDriver(or1.output(0))
net2.addLoad(inv1.input(0))
netlist.addNet(net2)

netlist.saveGraph('schema.png')

```

Above script will create a ModelNetlist and save the diagram in a file called schema.png which will look like below.

![schema.png](https://github.com/chiphackers/ModelNetlist/schema.png)



