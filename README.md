# ECE-3544-Digital-Design-I-Project-3-Part-A-Design-and-Synthesis-of-a-Comparator-System

Download Here: [ECE 3544: Digital Design I Project 3 (Part A) – Design and Synthesis of a Comparator System](https://codingherolab.com/product/ece-3544-digital-design-i-project-3-part-a-design-and-synthesis-of-a-comparator-system/)

For Custom/Original Work email codingprolab@gmail.com/whatsapp +1(541)423-7793

Project Objective

In this project, you will implement a comparator system from new and existing design units. Since your design will rely largely upon code that you have already written, you will have the opportunity to test (and possibly improve upon) the synthesizability of your Verilog code.

 

In addition, you will implement your top-level module on the Altera DE1-SoC board, so you will learn how to assign pins of your FPGA to the module’s input and output ports, and how to synthesize the module.

 

Requirements

The DE1-SoC board IS REQUIRED for this project.

 

You must have the current version of ModelSim-Altera Starter Edition and Quartus II Web Edition 14.1 installed on your computer. (When I installed Quartus 14.1, it updated version 10.1d of ModelSim ASE to version 10.3c, but the first time I started ModelSim ASE 10.3 it picked up from the same point that I had left ModelSim ASE 10.1d the last time that I had run it.)

 

The instructions are done using these versions of ModelSim and Quartus. While the directions may be consistent with other versions of ModelSim and Quartus, you must use the versions indicated above.

 

 

Project Description

In this assignment, you will design and implement the system represented in the block diagram shown below so that it works on the DE1-SoC board.

 

7-seg
Display

Driver

(Digit)

SW[7:4]
HEX2[6:0]
7-seg
Display

Driver

(Digit)

SW[3:0]
HEX0[6:0]
 
7485

 

A
B

I(A > B)

I(A < B)

I(A = B)

Q(A > B)
Q(A < B)

Q(A = B)

0
0

1

7-seg
Display

Driver

(Symbol)

HEX1[6:0]
LED[7:4]
LED[3:0]
 

You will receive a top-level module that defines the input and output interfaces of the FPGA and the DE1-SoC board. The basic top-level module also provides examples of module instantiation. Follow the instructions on pin assignment and programming your board to implement the existing behavior of the top-level module on your DE1-SoC board, then test the board to verify that that existing module performs as expected. Do not program your board before you have performed the pin assignment.

 

After you verify the functionality of the existing module and your board, implement the system described in the block diagram. Create a test-bench to simulate your design. After you verify the functionality of your design in simulation, program your board with the implementation of the final design.

 

Implementing the Basic Module

Make a working folder for this Project and copy the Quartus archive to that folder. You should use the same guidelines for locating and naming your working folder as I have indicated for previous assignments.

 

Start Quartus. Open the archive file in Quartus by selecting Project ® Restore Archived Project. You will find an interface for the project. The existing interface does not implement the final design, but it does demonstrate the way board-level inputs and outputs interface with instantiated modules. For now, you don’t need to modify any the code in the top-level module or in the modules that have been included for instantiation in the top-level module, but you should review all of the Verilog files to develop an understanding for what the system should do when you implement it on the DE1-SoC board.

 

 

Pin Assignment

Before you program the FPGA with the design contained in a Quartus project, you must perform a pin assignment. This step is important – an incomplete or incorrect pin assignment could damage your board.

 

The DE1-SoC Board has many peripherals, but we will not use all of them in this assignment. In general, you must assign each bit of the ports in your top-level module (slider switches, pushbuttons, clocks, LEDs, and hex display inputs – all as needed) to a physical pin on your FPGA. The existing top-level module uses the switches, the LEDs, and the hex displays. Your final design will use eight switches, eight LEDs, and three hex displays.

 

To make a pin assignment, you must know which FPGA pins correspond with the board’s peripherals. You can find this information in the DE1-SoC manual, which I have posted for download along with the project files.

 

Follow the instructions in the document “Pin Assignment for the DE1-SoC” board to assign pins for the top-level module. Remember that you must perform the analysis and elaboration step on an existing top-level module before you can assign pins for that module, and you must re-compile your project each time you make a change to the pin assignment. (You should make a habit of re-compiling your project each time you make a change to any element of your design.)

 

Programming the FPGA with the Basic Module

After you make a complete, correct pin assignment, you can program your board. Follow the instructions in the document “Programming your DE1-SoC Board” to implement the design contained in the top-level module.

 

After you program your board, test the functionality of the existing design and your board by manipulating the input switches and observing the LEDs and the hex displays.  You should be able to verify that the design and your board are in working order based on your understanding of the behavior of the top-level module and its instantiated components.

 

Implementing the Final Design

Make changes to the top-level module as described in the comments of the existing module. Your goal is to implement a system matching the block diagram in the “Project Description” section of this specification.

 

You have already implemented several of the blocks in the diagram in previous assignments. Use your seven-segment display drivers from your homework and your 7485 module from Project 2. You must use the version of the 7485 module that has no delays in it. You must add these files to the existing project. I recommend that you copy them to the working folder that you create for this project. In the Files tab of the Project Navigator, right-click on the Files folder and choose Add/Remove Files in Project. In the window that appears, choose the … button to browse for the files you want to add, then click Add once you have selected them.

 

Since our goal this semester has been to write code that will synthesize correctly in addition to simulating correctly in ModelSim, this project will provide you with the opportunity to test the synthesizability of code that you have already written. If Quartus gives synthesis errors for either of these modules, you should determine what elements of your code have caused the synthesis error and correct them.

 

 

The only truly new module that you must create for this project is the block representing the “symbol” seven-segment display driver. This module must use the outputs of the 7485 module to display one of three symbols, based on the way in which A and B compare:

 

A > B
(this is a lower-case g)

A = B
(this is an upper-case E)

A < B
(this is an upper-case L)

 

To create this module in Quartus, choose File ® New, and then choosing Verilog HDL File under Design Files. Write the module as you have written modules in ModelSim previously. After you save the file, you must add it to the project. To compile the module, click Analysis & Synthesis under Compile Design in the Tasks window. (Performing the Analysis & Synthesis task should suffice for any situation where you make changes to a Verilog module and wish to re-compile the Verilog source. If this does not suffice, you may need to re-compile the entire project. Since compilation can take a long time, you should only do it in situations where you have to do it, e.g., when you are ready to program your board with your design.)

 

Simulation

The project files include the framework for a test bench. In general, you can create a test bench in Quartus by choosing File ® New, and then choosing Verilog HDL File under Design Files. Remember to add the file to the existing project, and to repeat the Analysis and Synthesis step after you have finished making changes to the file that you add.

 

Follow the instructions in the document “Simulating Quartus Modules Using ModelSim” to simulate the behavior of the top-level module.

 

Write your test bench to simulate different operating cases of the comparator system. A sequence similar to the validation sequence (or the validation sequence itself) would be a good start. The validation test sequences are not nearly exhaustive. While you need not produce an exhaustive set of test cases in your test bench, you should not rely on the validation sequence as the sole test of your system’s correctness.

 

Programming the FPGA with the Final Design

After you make sure of your comparator’s functionality via simulation, you are ready to program the FPGA with your final design. You should not need to assign the pins a second time, but you might wish to open the Pin Planner to verify that your pin assignment remains unchanged.  Follow the instructions in the document “Programming your DE1-SoC Board” to implement the final design on your FPGA.

 

After your program your board, test the functionality of your final design by manipulating the input switches and observing the LEDs and the hex displays. While the validation sheet contains one sequence of input tests that you can try, the validation test is not exhaustive. As you did with your test bench, you should perform an amount of testing that you consider adequate for verifying the working order of your design.

 

 

Project Submission

Write a report describing your design and implementation process. Your report should include waveforms showing the correct behavior of your design.

 

I have included the validation sheet that the GTAs will use to test your design after the submission deadline. You do not have to go to the CEL to have your project validated. Instead, you should use the information in the validation sheet as one basis for testing your design before you submit your project.

 

Your project submission on Scholar should include the following items:

Project report in PDF
Source files for your top-level module and any modules that they require to function, and test benches for the top-level module.
 

Submit your report as an electronic document on Scholar, along with the individual source files. You must submit all elements of the project by the deadline to avoid late penalties; the assignment is only as timely as the last element to be submitted.

 

Your top-level module may be tested with our own secret test bench, so it is important that you use the module declaration provided with the archived project. You must also include the source files for every module required for your top-level module. Failure to do so will result in a grade of 0 for that portion of the project.

 

Grading for your submission will be as described on the cover sheet included with this description
