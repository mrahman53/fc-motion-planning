# FCND - 3D Motion Planning
![Quad Image](./misc/enroute.png)


This project is 3D Motion Planning for flying car that is developed in local machine and connecting with simulator.

## To run this project on your local machine, follow these instructions:
### Step 1: Download the Simulator
This is a new simulator environment!

### Step 2: Set up your Python Environment
If you haven't already, set up your Python environment and get all the relevant packages installed using Anaconda following instructions in [this repository](https://github.com/udacity/FCND-Term1-Starter-Kit)

### Step 3: Clone this Repository

git@github.com:mrahman53/fc-motion-planning.git

source activate fcnd
python backyard_flyer_solution.py



### Writeup:

Code Starter:
In backyard_flyer_solution.py and motion_planning.py provided by Udacity, there are some differences that is extra state has ben added
which is planning state.

In planning_utils.py, create_grid, A* algorithm and prune_path method was given and A* has been modified later.

In motion_planning.py, where all the steps are implemented form Arming to flying to Landing. Besides the few supportive functions
from planning_utils for path_planning.


Phases of backyard_flyer_solution.py:
Manual--->Arming---->TakeOff---->Waypoint---->Disarming

Phases of motion_planning.py:
Manual--->Arming---->Path-Planning----->TakeOff---->Waypoint---->Disarming


![state-machine](https://user-images.githubusercontent.com/1839661/41432061-e0b022ec-6fe2-11e8-8b93-76e25a95fc6b.png)


In plan_path method:

--the vehicle's route planning is implemented from current position to goal position. <br/>
--With given target_altitude and saftey_distance is set to 5. <br/>
--From the colliders.csv file we extracted the lat0 and lon0 which has been set vehicle's home position. <br/>
--Then Convert a global position (lon, lat, up) to a local position (north, east, down) relative to the home position using global_to_local function. <br/>
--After reading the obstacle map data from colliders.csv, we created grid. <br/>
--Then set some goal position from command line to route. <br/>
--Used A* algorithm with diagonal motion to optimize our route search. <br/>
--Used Collinearity technique to implement prune function that minimize Waypoints. <br/>

A* algorithm:

--Used Action Enum set to a cost of sqrt(2) for diagonal motion. <br/>
--Used valid_actions function to validate the next move. <br/>