# Ulna v2.6 - Diabetes Simulator

Ulna v2.6: Development Platform for Artificial Pancreas Algorithms

(c) 2023 Mohamed R. Smaoui

Dept of Computer Science, College of Sciences, Kuwait University, Kuwait

mohamed.smaoui@ku.edu.kw

We present in this work a clinically validated cloud-based distributed platform that supports the development and comprehensive testing of single and dual-hormone algorithms for type 1 diabetes mellitus (T1DM).

The platform is built on principles of object-oriented design and runs user algorithms in real-time virtual clinical trials utilizing a multi-threaded environment enabled by concurrent execution over a cloud infrastructure. The platform architecture isolates user algorithms located on personal machines from proprietary patient data running on the cloud. Users import a plugin into their algorithms (Matlab, Python, or Java) to connect to the platform. Once connected, users interact with a graphical interface to design experimental protocols for their trials. Protocols include trial duration in days, mealtimes and amounts, variability in mealtimes and amounts, carbohydrate counting errors, snacks, and onboard insulin levels.

The platform facilitates development by solving the ODE model in the cloud on large CPU-optimized machines, providing a 62% improvement in memory, speed and CPU utilization. Users can easily debug & modify code, test multiple strategies, and generate detailed clinical performance reports. We validated and integrated into the platform a glucoregulatory system of ordinary differential equations (ODEs) parameterized with clinical data to mimic the inter and intra-day variability of glucose responses of 15 T1DM patients.

The platform utilizes the validated patient model to conduct virtual clinical trials for the rapid development and testing of closed-loop algorithms for T1DM.

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


