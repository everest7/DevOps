## Docker
#### Containerization:
An application that is being developed and deployed is bundled and wrapped together with all its configuration files and dependencies. This bundle is called a container.
#### Docker:
Docker is a containerization platform which packages your application and all its dependencies together in the form of containers so as to ensure that your application works seamlessly in any environment.
#### Dockerfile:
Docker can build images automatically by reading the instructions from a file called Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using docker build, users can create an automated build that executes several command-line instructions in succession.
![alt text](/images/Docker.png)
## Kubernetes
Kubernetes is an open-source container management tool which holds the responsibilities of container deployment, scaling & descaling of containers & load balancing. Docker builds the containers and these containers communicate with each other via Kubernetes.
A typical application would have a cluster of containers. These containers need to talk to each other. That’s when the K8s comes in and do the load balancing, scaling and monitoring these containers. 
![alt text](/images/k8s.png)
#### Pod:
We can think of Kubernetes pod as a group of containers that are run on the same host.
#### Node:
A node in Kubernetes is a worker machine which is also known as a minion. This node could be a physical machine or a virtual machine.
#### Deployment:
A deployment is responsible for create instance of and make sure a set of pods running.
#### Service:
A service is responsible for enabling network access to a set of pods. 1. Load Balancer: expose the service externally using some Cloud solution. 2. NodePort
![alt text](/images/k8s-service.png)
#### Benefits:
High Availability:
Scalability:
Disaster Recovery:
Self-healing: K8s will automatically start a new one if old replica dies.
Smart scheduling: K8s decides for you which worker node to run your container by finding the best fitting
#### ETCD:
A backing store for all cluster data. If a pod fails, then ETCD will get updated about it. So the control manager will intervene and start a new pod. We can create Etcd snapshot as backup. 

## Kafka:
![alt text](/images/kafka.png)
#### Offset
A sequential ID number that is used to uniquely identify each message in the partition. It also tells you at what position you have consumed the message in the queue. 
#### Zookeeper
We use Zookeeper to keep track of the Kafka cluster, so if any node fails, we can recover from previously committed offset. 
Advantage: High-throughput, low latency, fault tolerant, Durability, Scale out with incurring any downtime. 
#### Replication
A backup of partition. Follower will become the new leader if leader fails. 
#### Schema Registry
A Restful interface storing and retrieving your schema. What you send to Kafka broker is just a sequence of byte data. 
#### Avro
Avro enables schema evolution so that we can add more fields to the schema without changing much of the code. Avro has binary representation which is more efficient than JSON. 

## C#
- ref parameters needs to be initialized before passing it.
out doesn’t have to. Using output parameter to return multiple values from a function. 
- Using statement ensures dispose() method is called after the execution completed. suppose you have to open a database connection from within a class. The database connection instance is an unmanaged resource encapsulated within this class and should be released as soon as you are done with it.
- "throw" statement preserves original error stack whereas 
  "throw ex" have the stack trace from their throw point.
- Value Type and Reference Type
A data type is a value type if it holds a data value within its own memory space. It means the variables of these data types directly contain values. Stack reference type doesn't store its value directly. Instead, it stores the address where the value is being stored. In other words, a reference type contains a pointer to another memory location that holds the data. Heap(By returning the reference as return value, the object it references can still be used outside the method)

## .NET Framework
A platform for building various applications on windows. 
Component:
1. Class Library
2. Common Language Runtime
3. Common Type System: It has a set of rules which state how a data type should be declared, defined and used in the program.

## Spark and Scala
#### RDD 
RDD represents resilient distributed dataset. We usually partitioned the RDD to different cluster to achieve parallelization. 
Create RDD: 1. Load external dataset. 2. Distribute a collection
Operation on RDD:
1. Transformation: takes RDD as input and create new RDD by applying map(), filter().
2. Actions: returns final result of RDD, you can save the result as file and display it on the console. saveAsTextFile(). 
#### RDD lineage 
a process that reconstructs lost data partitions. The best thing about this is that RDDs always remember how to build from other datasets.
#### Lazy evaluation 
The execution will not start until anaction is triggered. Transformations are lazy in nature i.e. when we call some operation on RDD, it does not execute immediately. Spark adds them to a DAG of computation and only when driver requests some data, this DAG actually gets executed
#### Spark over MapReduce:
Spark is in-memory processing while MapReduce precesses the data in Disk. 
Good for iterative processing. Since Spark does this lazy evaluation, Spark’s Resilient Distributed Datasets (RDDs) enable multiple map operations in memory, while Hadoop MapReduce has to write interim results to a disk.