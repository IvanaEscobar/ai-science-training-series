# Intro to AI Series: AI Accelerators


Scientific applications are increasingly adopting Artificial Intelligence (AI) techniques to advance science. There are specialized hardware accelerators designed and built to run AI applications efficiently. With a wide diversity in the hardware architectures and software stacks of these systems, it is challenging to understand the differences between these accelerators, their capabilities, programming approaches, and how they perform, particularly for scientific applications. 

We will cover an overview of the AI accelerators landscape with a focus on SambaNova, Cerebras, Graphcore, and Groq systems along with architectural features and details of their software stacks. We will have hands-on exercises that will help attendees understand how to program these systems by learning how to refactor codes written in standard AI framework implementations and compile and run the models on these systems. 



## Slides

* [Intro to AI Series: AI Accelerators](./AI_Accelerators.pdf) 

## Hands-On Sessions


* [Cerebras](./Cerebras/README.md)
* [Graphcore](./Graphcore/README.md)  
* [SambaNova](./Sambanova/README.md)                                    
* [Groq](./Groq/README.md)        


### Director’s Discretionary Allocation Program

To gain access to AI Testbeds at ALCF after current allocation expires apply for [Director’s Discretionary Allocation Program](https://www.alcf.anl.gov/science/directors-discretionary-allocation-program)

The ALCF Director’s Discretionary program provides “start up” awards to researchers working to achieve computational readiness for for a major allocation award.

## Homework 

You need to submit either Theory Homework or Hands-on Homework. 

#####  Theory Homework
* What are the key architectural features that make these systems suitable for AI workloads?
* Identify the primary differences between these AI accelerator systems in terms of their architecture and programming models.
* Based on hands-on sessions, describe a typical workflow for refactoring an AI model to run on one of ALCF's AI testbeds (e.g., SambaNova or Cerebras). What tools or software stacks are typically used in this process?
* Give an example of a project that would benefit from AI accelerators and why?

##### Hands-on Homework

* [Cerebras Homework](./Cerebras/README.md#homework)
* [Sambanova Homework](./Sambanova/README.md#homework)
* [Graphcore Homework](./Graphcore/README.md#homework)
* [Groq Homework](./Groq/README.md#homework)

## Useful Links 

* [Overview of AI Testbeds at ALCF](https://www.alcf.anl.gov/alcf-ai-testbed)
* [ALCF AI Testbed Documentation](https://www.alcf.anl.gov/support/ai-testbed-userdocs/)
* [Director’s Discretionary Allocation Program](https://www.alcf.anl.gov/science/directors-discretionary-allocation-program)
* [ALCF Events Page](https://www.alcf.anl.gov/events/intro-ai-series-ai-accelerators-0)  

##### Acknowledgements

Contributors: [Siddhisanket (Sid) Raskar](https://sraskar.github.io/), [Murali Emani](https://memani1.github.io/), [Varuni Sastry](https://www.alcf.anl.gov/about/people/varuni-katti-sastry), [Bill Arnold](https://www.alcf.anl.gov/about/people/bill-arnold), and  [Venkat Vishwanath](https://www.alcf.anl.gov/about/people/venkatram-vishwanath).

> This research used resources of the Argonne Leadership Computing Facility, which is a DOE Office of Science User Facility supported under Contract DE-AC02-06CH11357.


---
# Solution

The key architectural features that make these systems suitable for AI workloads is the memory is uniformly distributed across cores, whereas traditional architectures hold memory seperate from cores. Cerebras has SwarmX, which manages synchronization of memory by using broadcast and reduce.


Differences between AI accelerator systems in terms of architecture and programming models:
- AI accelerator systems programming is prioritized by the availability of the data in the operation, called dataflow. 
- The dataflow is represented as a graph, snd the compiler will maps the program onto the architecture.


A typical workflow for refactoring an AI model to run on ALCF AI testbeds:
- Cerebras: Uses PyTorch along with a CerebrasAPI. Most of the software stack remains the same. You can insatll the cerebrasAPI via `pip install` 
- Cerebras uses Kubernetes for job submission
- Graphcore: MIMD architecture. IPU uses bulk synchronous parallel means the entire chip with be in local tile compute, global cross-tile sync, or data exchange modes. You hve to ssh into the graphcore loginnode, then ssh into the poplar node. 
- Graphcore uses SLURM for job submission

Example of a project that could use AI accelerators: 
- the AI accelerators could accelerate reading through data. For example, banks holld a large amount of data to track and understand transactions done by their clients. These AI accelerators could be dedicated to train on transaction data and determine anomolous behavior. This would help against fraud transactions.
