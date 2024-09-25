# Working with custom Controllers

## Contents

1. [Writing a custom controller](#writing-a-custom-controller)
2. [Interacting with the network](#interacting-with-the-network)
3. [Using a custom controller](#using-a-custom-controller)

---

## Writing a custom controller

1. Create a new files
    ```
    Flexcomm-Simulator-Flow/routing/my-controller.py
    ```

2. Create a new class extending `algo.RoutingAlgorithm` and overriding the abstract methods. Example:
    ```python
    class NewRoutingAlgo(algo.RoutingAlgorithm):
        def __init__(self, graph: nx.Graph, ref: str = None) -> None:
            super().__init__(graph)
            
            # ...

        def new_flow(self, app: Application):
            # ...

        def remove_flow(self, app: Application):
            # ...
    ```

3. Write your custom logic. Refer to [ospf.py](https://github.com/extinto77/Flexcomm-Simulator-Flow/blob/master/routing/ospf.py) for an example:
    ```python
    class Ospf(algo.RoutingAlgorithm):
        def __init__(self, graph: nx.Graph, ref: str = None) -> None:
            super().__init__(graph)
            self.state = {}
        
        def new_flow(self, app: Application):
            self.state[app] = nx.shortest_path(
                self.graph, app.host.name, app.remote.name, self._calculate_weight
            )
            self._apply_routing()
        
        def remove_flow(self, app: Application):
            self.state.pop(app)
            self._apply_routing()
    ```

---

## Interacting with the network

FAZER ISTO !!! funções mais importantes e assim ...

<!-- 
- The [Topology](https://github.com/RuiCunhaM/Flexcomm-Simulator/blob/master/ns-3.35/src/topology/model/topology.h) class provides a simple wrapper around a [boost::graph](https://www.boost.org/doc/libs/1_82_0/libs/graph/doc/index.html) representation of the entire network:
    - Access the Graph
        ```cpp
        Graph Topology::GetGraph ();     
        ```

    - Change edge weights
        ```cpp
        void Topology::UpdateEdgeWeight (Ptr<Node> n1, Ptr<Node> n2, int newWeight);
        ```

    - Calculate shortest path(s) using Dijkstra's Algorithm:
        ```cpp
        vector<Ptr<Node>> Topology::DijkstraShortestPath (Ptr<Node> src, Ptr<Node> dst);
        vector<Ptr<Node>> Topology::DijkstraShortestPaths (Ptr<Node> src);
        ```

    - Access a `Channel`
        ```cpp
        Ptr<Channel> Topology::GetChannel (Ptr<Node> n1, Ptr<Node> n2);
        ```

- Acsess Switch's data
    ```cpp
    // "node" is from type Ptr<Node>
    Ptr<OFSwitch13Device> device = node->GetObject<OFSwitch13Device> ();
    device->GetCpuUsage ();
    // ...
    ```

- Access Channel's data
    ```cpp
    // "channel" is from type Ptr<Channel>
    channel->GetChannelUsage ();
    // ...
    ```

- Sending commands to a switch. Refer to [ofsoftswitch13's Documentation](https://github.com/CPqD/ofsoftswitch13/wiki/Dpctl-Flow-Mod-Cases) for more details about `dpctl`:
    ```cpp
    std::ostringstream cmd;
    cmd << "flow-mod cmd=add,table=0,prio=0 apply:output=ctrl:128";
    DpctlExecute (swDpId, cmd.str ());
    ```

- Converting from `Data Path Id` to `Node Id` and vice-versa:
    ```cpp
    // Convert Data Path Id to Node Id
    uint32_t DpId2Id (uint64_t DpId);

    // Convert Node Id to Data Path Id 
    uint64_t Id2PdId (uint32_t Id);
    ``` -->

---

## Using a custom controller

To use a custom controller in the simulation set the `CONTROLLER` flag to the filename and the name of the intended controller:
```
make run CONTROLLER=my-controller.NewRoutingAlgo
```

---
