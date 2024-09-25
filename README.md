# FIFO Memory Module in Verilog

## Overview

This project implements a **First In First Out (FIFO) memory** module using Verilog. A FIFO memory buffer is a storage system where data is written to the memory sequentially and read out in the same order. The FIFO memory module is widely used in applications where temporary data storage is needed, and the order of data input and output must be preserved.

## Features

- **8-bit Data Width**: The FIFO supports an 8-bit wide data input and output.
- **FIFO Control**: Handles conditions like FIFO full, FIFO empty, and overflow/underflow detection.
- **Write and Read Control**: A write pointer and a read pointer control data storage and retrieval.
- **Threshold Signal**: Generates a threshold signal when a certain amount of the FIFO memory is utilized.
- **Synchronous Design**: All operations are triggered on the rising edge of the clock signal.
- **Asynchronous Reset**: The module supports an asynchronous reset to initialize pointers and status signals.

## Modules

The project is structured into multiple Verilog modules, each with specific functionality:

1. **`fifo_mem`**: The top-level module that integrates the entire FIFO system.
    - Inputs: `clk`, `rst_n`, `wr`, `rd`, `data_in`
    - Outputs: `data_out`, `fifo_full`, `fifo_empty`, `fifo_threshold`, `fifo_overflow`, `fifo_underflow`
    
2. **`write_pointer`**: Manages the write operations of the FIFO.
    - Tracks the write pointer and signals when data can be written to the FIFO.
    
3. **`read_pointer`**: Manages the read operations of the FIFO.
    - Tracks the read pointer and ensures data is read sequentially.

4. **`memory_array`**: The memory array stores the actual data. 
    - It holds 16 elements, each 8 bits wide, and uses the write and read pointers to store and retrieve data.

5. **`status_signal`**: Monitors the status of the FIFO, generating signals such as `fifo_full`, `fifo_empty`, `fifo_threshold`, `fifo_overflow`, and `fifo_underflow`.

## Usage

### Inputs
- **`clk`**: Clock signal to synchronize operations.
- **`rst_n`**: Active-low asynchronous reset signal to initialize the FIFO.
- **`wr`**: Write enable signal. When high, allows data to be written into the FIFO.
- **`rd`**: Read enable signal. When high, allows data to be read from the FIFO.
- **`data_in`**: 8-bit input data to be written into the FIFO.

### Outputs
- **`data_out`**: 8-bit output data read from the FIFO.
- **`fifo_full`**: High when the FIFO is full and cannot accept more data.
- **`fifo_empty`**: High when the FIFO is empty and no data is available to read.
- **`fifo_threshold`**: High when the FIFO reaches a certain threshold level.
- **`fifo_overflow`**: High when data is attempted to be written to a full FIFO.
- **`fifo_underflow`**: High when data is attempted to be read from an empty FIFO.

## Simulation and Testing

The FIFO module can be tested using a Verilog testbench, simulating various cases such as:
- Normal operation (writing and reading data).
- Attempting to write when FIFO is full.
- Attempting to read when FIFO is empty.
- Monitoring the overflow and underflow conditions.

## Applications

FIFO memory systems are used in various applications, including:
- Data buffering between systems with different data rates.
- Network routers and switches for queuing data packets.
- Real-time systems where input-output data order must be preserved.

## Conclusion

This project demonstrates the implementation of a basic 8-bit FIFO memory system in Verilog, with key control features such as detecting full, empty, overflow, and underflow conditions. The FIFO design can be expanded or modified for different data widths, buffer depths, and application-specific requirements.


This README provides an overview of the project and guides users through the functionality of the FIFO memory system. Feel free to adjust specific details based on your requirements!
