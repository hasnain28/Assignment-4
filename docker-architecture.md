Docker architecture is a master slave node architecture.

There could be one or more master nodes also called as control plane nodes.

Also there could be one or more worker nodes as well also called as data plane nodes.

Components of docker architecture could be divided into two categories.

1.Master node components.
2.All node components.

Firstly we will look into master node components.

**API SERVER:**

It is the entrypoint of cluster.

It authenticates and authorizes the request.

Management hub of the K8s cluster.

Facilitates communication between components within and also from outside the cluster.

Only component to communicate with **etcd.**

Offers CRUD interface for querying and modifying the cluster state.


**etcd:**

It is the database of the cluster.

Data is stored in it in the form of key value pair.

Anything created by API server is stored and maintained in etcd.

It manages the state of cluster.

Stores config data which can be accessed by K8s master API server using simple HTTP or JSON APIs.

**Scheduler:**

It tells the API server to forward the request of creating pod to which worker node based on priority.

Watches new workloads and assign nodes to them.

Decides best node on which pod should be deployed.

Default methodology is to check resource availability but can be overriden by custom scheduling.

**Controller manager:**

Manages controllers.

Controller manager runs adn loops and its main goal is to always keep on trying to make the current state equals to desired state.
state


**Now comes the all node components which exist on both master and worker nodes.**

**Kubelet:**

It is the bridge that joins the available CPU, disk and memory for a node into the large K8s cluster.
Communicates with API servers to find pods that sould be running on its node.
It also reports back the health of the node as well of pods running on its node.
It also manages the health check and restart policy of container.

**Kube-Proxy:**

It is the networking brain of node.
Manages the routing table of node.
Every pod gets it unique IP.
Route traffics to actual pod.

**Pod:**

Smallest deployable unit in K8s.


Its just a logical wrapper over a container for easily passing arguments to container.

Can have one or more more containers but its preferred to have one container per pod.
Containers within a pode share an IP address and port space and can find each other via localhost.






