# D Flip-Flop (DFF) Verification using UVM

This repository contains the design and verification of a D Flip-Flop, a fundamental building block of sequential logic. The project's main focus is to demonstrate a more advanced UVM testbench structure that utilizes multiple, targeted sequences to verify different operational modes of the DUT.

---

### Project Overview

This project showcases the verification of a simple D Flip-Flop with an asynchronous reset. The key highlight is the use of a layered test plan executed via separate sequences, which is a common practice in professional verification environments.

-   **DUT**: A single-bit D Flip-Flop with a clock, reset, data input (`din`), and data output (`dout`).
-   **Verification Environment**: A UVM testbench that uses specific sequences to test reset behavior, normal data propagation, and random stimulus.

---

### Folder Structure

-   `rtl/dff_design.v`: Contains the Verilog design for the D Flip-Flop and its interface.
-   `tb/dff_tb.sv`: Contains the complete SystemVerilog/UVM code, including all components and the top-level testbench module.

---

### Key Verification Components

-   **Multiple Targeted Sequences**: This testbench uses three distinct sequences to verify specific functionality:
    -   `rst_dff`: A sequence that only drives the reset signal high to confirm the flip-flop resets correctly.
    -   `valid_din`: A sequence that keeps reset low and drives random data to `din` to verify normal operation.
    -   `rand_din_rst`: A sequence that drives both `din` and `rst` randomly to test the DUT under chaotic conditions.
-   **Stateful Scoreboard**: The scoreboard is more advanced as it must track the state (`expected_dout`) of the flip-flop from one cycle to the next to predict the correct output.
-   **Configuration Object (`config_dff`)**: Demonstrates the use of a configuration object to control agent behavior (in this case, setting it to `UVM_ACTIVE`).

---

### How to Run

To run this simulation, you will need a simulator that supports SystemVerilog and UVM.

1.  Compile both `rtl/dff_design.v` and `tb/dff_tb.sv`.
2.  Ensure the UVM library is included in your compilation command.
3.  Set `tb` as the top-level module for simulation.
4.  Run the simulation. The test will automatically execute and report the status of each sequence.
