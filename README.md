Ulna v2.6 - Diabetes Simulator

------------
INSTALLATION
------------

To install the simulator graphical interface, please click on "Ulna-2.6.msi".

The installation will create a shortcut for Ulna on your desktop upon completion.


----------------------------
CONTROLLER ALGORITHM PLUGINS
----------------------------

Ulna has a simple controller algorithm installed that can be used directly without having to hook-up your external controller 
algorithm. It is provided as a test algorithm.

To develop your external controller algorithm with Ulna, please use one of the algorithm plugins available to you in this 
release.


-----------
JAVA PLUGIN
-----------

The AlgorithmPlugin-JAVA-11.zip can be imported as a project into an IDE such as Eclipse. It has a sample PID controller for you 
to start with. If you import the project into an IDE such as Eclipse, you can run the plugin by starting the 
StartSimulation.java file.


-------------
MATLAB PLUGIN
-------------

The AlgorithmPlugin-MATLAB.zip contains the following 3 files:
	- T1D_Algorithm.m
	- launch.sh
	- NexusCommunicator_MATLAB.jar


You can develop your code inside the T1D_Algorithm.m file. This file contains 2 functions available to you that are called by 
the simulation environment. 

The first function is the setInitialConditions() and is called once at the beginning of a simulation run to pass to your 
controller algorithm information regarding the simulation protocol (such as duration, time step, etc.). 

The second function is simulateStep() and is called continuously at every time step. This function provides your control 
algorithm the current glucose measurement of the virtual patient in simulation, the current time, any meals the patient is 
having at the moment, and whether the patient is performing exercise at the moment.

This method is expected to return your controller algorithm's response to this data. The response includes the following 4 
parameters that must be returned at every call: insulinBasal, insulinBolus, glucagonBasal, glucagonBolus. 

To test how well your algorithm performs on the virtual patients in the simulator, you mush plugin your algorithm to the 
simulator. To do so, you need to execute the launch.sh program. The launch.sh program has 2 path variables that you must 
update, one pointing to your T1D_Algorithm.m file and the other pointing to the NexusCommunicator_MATLAB.jar file. Once you 
modify the file paths inside the launch.sh file, you can run it in the command line with the following command: "./launch.sh"

This will launch the NexusCommunicator panel and plug your controller algorithm. Once this shows on your screen, you can start 
a new simulation in the Ulna program. 


-------------
PYTHON PLUGIN
-------------

The AlgorithmPlugin-PYTHON.zip contains the following 3 files:
	- T1D_Algorithm.py
	- launch.py
	- NexusCommunicator_PYTHON.jar


You can develop your code inside the T1D_Algorithm.py file. This file contains 2 functions available to you that are called by 
the simulation environment. 

The first function is the setInitialConditions() and is called once at the beginning of a simulation run to pass to your 
controller algorithm information regarding the simulation protocol (such as duration, time step, etc.). 

The second function is controlStep() and is called continuously at every time step. This function provides your control 
algorithm the current glucose measurement of the virtual patient in simulation, the current time, any meals the patient is 
having at the moment, and whether the patient is performing exercise at the moment.

This method is expected to return your controller algorithm's response to this data. The response includes the following 4 
parameters that must be returned at every call: insulinBasal, insulinBolus, glucagonBasal, glucagonBolus. 

To test how well your algorithm performs on the virtual patients in the simulator, you mush plugin your algorithm to the 
simulator. To do so, you need to execute the launch.py program. The launch.py program has 2 path variables that you must 
update, one pointing to your T1D_Algorithm.py file and the other pointing to the NexusCommunicator_PYTHON.jar file. Once you 
modify the file paths inside the launch.py file, you can run it in the command line with the following command: "python 
launch.py"

This will launch the NexusCommunicator panel and plug your controller algorithm. Once this shows on your screen, you can start 
a new simulation in the Ulna software. 


-------
Contact
-------

Web: http://csilab.io

Email: msmaoui@cs.ku.edu.kw

(c) 2023 Mohamed R. Smaoui


