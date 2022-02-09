The following are the basic commands that are shown in the first demo:

## 1. This command launches the ROS master:

```
roscore
```


## 2. This command launches a node:

Definition: 

```
rosrun package_name node_name
```
Example: 
```
rosrun turtlesim turtlesim_node
```


## 3. This command list all the current topics:

```
rostopic list
```


## 4. This command provides more information about a topic:

Definition: 

```
rostopic info topic_name
```
Example: 
```
rostopic info /rosout
```

## 5. This command provides more information about a message:

Definition: 

```
rosmsg info msg_type
```
Example: 
```
rosmsg info std_msgs/Bool
```

## 6. This command visualizes your current ROS system:

```
rosrun rqt_graph rqt_graph
```