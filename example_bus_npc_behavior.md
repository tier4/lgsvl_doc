# Example Bus NPC Behavior

Bus NPC will be follow behavior tree like below.

![Behavior Tree](/out/example_bus_npc_behavior/example_bus_npc_behavior.png)

Each Task/Flow node should be work like below.

## Flow Node
### Sequencer
Seqeuncer execute all child tasks in sequence order.
Child nodes has priority and child nodes which describes in left side has higher priority.

### Selector
Selector select one child task and excute it.
Child nodes has priority and child nodes which describes in left side has higher priority.

## Task Node
### RouteSearch
If the NPC has no route, or current route was changed because of obstacles/lane change etc...
Replan route.

### FollowLane
The NPC follows the current lane and route.

### StoppingAtObstacle
The NPC follwing current lane and decelerating in order to avoid clash.

### StoppedAtObstacle
The NPC was safely stopped behind the othe object

### WaitUntilObstacleMoves
If the Obstacle is dynamic and on the current lane (for example othe moving vehicles), the NPC wait until the obstacle moves.

### WaitUntilTargetLaneClear
If the NPC Try to avoid obstacle with lane change, the NPC checks the target lane and wait until the target lane will be clear.

### AvoidObstacleWithLanneChange
If the NPC can avoid obstacle without lane violation, the NPC try to avoid obstacle by changing lanes

### WaitUntilOppositeLaneClear
If the NPC Try to avoid obstacle with lane violation, the NPC checks the opposite lane and wait until the opposite lane will be clear.

### AvoidObstacleWithLaneViolation
If the NPC cannot avoid obstacle witout lane violation, the NPC try to avoid obstacle with violating lane.

### StoppingAtStopLine
If the NPC find the stopline in front of the NPC, the NPC try to stop at the Stopline.

### StoppedAtStopLine
If the NPC succeed to stopped in front of the stopline, the NPC try to follow lanes.

### StoppingAtBusStop
If the NPC find busstop in front of the NPC, the NPC try to stop at the BusStop.

### StoppedAtStopLine
If the NPC succeed at the BusStop, the NPC try to follow lanes.

### WaitUntilYeildLaneClear
The NPC wait until the yeild lane is clear

### PassThroughTheIntersection
In this task, NPC try to pass throuhg the intersection.

### WaitUntilLeftTurnYeildLaneClear
The NPC wait until the yeild lane is clear

### TurnLeftInTheIntersection
In this task, NPC try to turn left in the intersection.

### WaitUntilRightTurnYeildLaneClear
The NPC wait until the yeild lane is clear

### TurnRightInTheIntersection
In this task, NPC try to turn right in the intersection.

### TryLaneChange
If the NPC thinks lane change will be necessary in order to follow lanes, the NPC check the target lane is clear, if the lane is clear, the NPC execute lane change.

### ChangingLane
The NPC is executing lane change.

## How to work
Each task node communicate with LGSVL simulator environment by using UniCom. (https://github.com/tier4/UniCom)
Path planner/controller was implimented as a Gameobject which atached to the NPC.