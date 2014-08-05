SUMO-CUDA
=========

An implementation of the SUMO traffic simulation tool suite using CUDA for GPU speedup.

The Goal
=========

The SUMO-CUDA system is a microscopic simulation meant to provide an example of a real world problem (traffic simulation) run on a massively parallel device. To do this, the system employs the use of a NVIDIA graphics card with CUDA computational ability, combined with an operating system able to utilize the CUDA libraries. The system is composed of a structure called a network which represents the edges (roads), and nodes (junctions or endpoints), and vehicles (which are the key component to the system). The system operates in timesteps, in each timestep a single unit of work is done across the network. This is important to how the simulation is run accurately. For example, in order make a movement, a vehicle must take into account the information about the vehicle in front of it. If we were to iterate through vehicles making movements one by one, the system would be inaccurate because the next vehicle to move would be making a decision based upon data newer than it had access to if it were actually making the decision in real time.  Thus, all decisions are made in a half step, and the second part of the step takes the decisions and puts them into effect. This is where CUDA becomes very applicable to the problem. If the relevant information about a half step for each vehicle is passed to a massively parallel device, we can compute the relevant decisions all at once, rather than compute it serially. The SUMO-CUDA system provides an example of a simplified traffic simulation system that attempts to do this in a way that is faster than running on  traditional computational device.

---------

Authors: Chris Blatchley, Thaddeus Bond
