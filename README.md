P-MAS-TG
========

Planner for Multiple Agent System with Temporal Goals 

-----
Description
-----
this package contains implementation for plan synthesis algorithms given a finite transition system (as the agent motion model) and a Linear temporal logic formula (as the agent task). It outputs the static plan as a sequence of agent motion and action, required to fulfill the task. 

<p align="center">  
  <img src="https://github.com/MengGuo/P_MAS_TG/blob/master/Intro/figures/collaborate.jpg" width="800"/>
</p>

<p align="center">  
  <img src="https://github.com/MengGuo/P_MAS_TG/blob/master/Intro/figures/nor.png" width="800"/>
</p>


-----
Features
-----
* Action model can be muted if only motion is concerned.
* Soft specification is optional.
* NetworkX structure for FTS, Buchi and Product automata.
* Static or on-the-fly construction of the product automaton.
* Stand-alone planner

```python
from P_MAS_TG.ts import MotionFts, ActionModel, MotActModel
from P_MAS_TG.planner import ltl_planner

# construct your motion and action model
#---------
robot_motion = MotionFts(node_dict, symbols, 'your_ws_name')
robot_motion.set_initial(initial_node)
robot_motion.add_un_edges(edge_list, unit_cost = 0.1)
#---------
robot_action = ActionModel(action_dict)
#---------
robot_model = MotActModel(robot_motion, robot_action)

# specify your hard and soft tasks
hard_task = '(([]<> r3) && ([]<> r4))'
soft_task = None

# set planner
robot_planner = ltl_planner(robot_model, hard_task, soft_task)

# synthesis
robot_planner.optimal(10,'static')
```

* Generate `.dat` for MatLAB to load Buchi and product automata model. See [square_world.py](https://github.com/MengGuo/P_MAS_TG/blob/master/Intro/Examples/to_matlab/square_world.py).





----
Debugging
----
* install python packages like networkx, ply.
* add this package to your PYTHONPATH, to import it in your own project.
* ltlba_32 and ltlba_64 are executable files complied under OS X. For other OS, please follow [ltl2ba/README.txt](https://github.com/MengGuo/P_MAS_TG/blob/master/Install_ltl2ba/README.txt).
* Try [test.py](https://github.com/MengGuo/P_MAS_TG/blob/master/test.py) and other examples in the [Examples](https://github.com/MengGuo/P_MAS_TG/tree/master/Intro/Examples) folder. 