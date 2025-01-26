# Distributed Sudoku Solver

### `Grade: 19.8/20`

## Project Abstract  

**Distributed Sudoku Solver** is a system designed to solve Sudoku puzzles collaboratively across a network of distributed nodes. This project demonstrates the principles of distributed computing, including fault tolerance, scalability, and efficient workload distribution.  

The system employs a peer-to-peer (P2P) architecture where nodes communicate and cooperate to validate and solve Sudoku puzzles. Nodes can dynamically join or leave the network, and each node's computational capacity is factored into the workload distribution. The architecture ensures redundancy and consistency, making the system resilient to node failures.  

**Key Features:**  
- **Dynamic Network Topology**: Nodes can join or leave the network at runtime, ensuring flexibility and scalability.  
- **Distributed Workload**: Sudoku-solving tasks are distributed across the network, leveraging the computational power of all nodes.  
- **Fault Tolerance**: The system ensures consistent results even in the presence of node failures.  
- **Customizable Node Configuration**: Users can define node-specific parameters, such as ports, peer connections, and processing delays, to simulate real-world scenarios.  
- **RESTful API**: Provides endpoints for submitting Sudoku puzzles, checking network status, and retrieving system statistics.  

This project showcases the practical application of distributed systems concepts, emphasizing collaborative problem-solving and robust system design.  
For more details, please refer to the [presentation slides](docs/presentation.pdf) and, if needed, the created and used [protocol](docs/protocol.pdf).

---

## How to Run  

### 1. Running the Initial predifined Node  
The first node in the network must be initialized to start the system.  

1. Navigate to the `src/scripts` folder:  
   ```bash
   cd src/scripts
   ```  
2. Run the initialization script:  
   ```bash
   ./runInitNode
   ```  

### 2. Adding a Predifined Node  
Additional predifined nodes can be added to the network using predefined scripts.  

1. Navigate to the `src/scripts` folder:  
   ```bash
   cd src/scripts
   ```  
2. Run the script for the desired node:  
   ```bash
   ./runNode2
   ```  
3. Repeat this step for additional nodes, modifying the script name accordingly.  

### 3. Adding a custom Node  
You can create a custom node by specifying its configuration.  

1. Run the following command, replacing the placeholders with desired values:  
   ```bash
   python3 src/node.py -p <HTTP_PORT> -s <P2P_PORT> -h <HANDICAP> -a <PEER_NODE_ADDRESS>
   ```  
   - **HTTP_PORT**: The HTTP port of the new node.  
   - **P2P_PORT**: The peer-to-peer communication port of the new node.  
   - **HANDICAP**: The processing delay for the node.  
   - **PEER_NODE_ADDRESS**: The address of an existing peer node (e.g., `127.0.0.1:7002`).  

Example:  
   ```bash
   python3 src/node.py -p 8003 -s 7003 -h 0.01 -a 127.0.0.1:7002
   ```  

### 4. Requesting a Sudoku Solution  
You can request solutions for predefined Sudoku boards with missing cells.  

1. Navigate to the `src/scripts` folder:  
   ```bash
   cd src/scripts
   ```  
2. Run the appropriate script:  
   ```bash
   ./solve3  # For a board with 3 cells missing
   ./solve4  # For a board with 4 cells missing
   ```  

### 5. Requesting a Custom Sudoku Board Solution  
To solve a custom Sudoku board, use the REST API.  

1. Run the following `curl` command, replacing the JSON with your Sudoku board:  
   ```bash
   curl http://localhost:8001/solve -X POST -H 'Content-Type: application/json' -d '{"sudoku":[[6, 9, 5, 2, 8, 7, 0, 3, 1], [4, 7, 8, 5, 1, 3, 9, 2, 6], [2, 1, 3, 6, 9, 4, 8, 5, 7], [9, 3, 7, 8, 2, 6, 5, 1, 4], [8, 6, 1, 9, 0, 5, 2, 7, 3], [5, 4, 2, 7, 3, 1, 6, 8, 9], [7, 8, 9, 1, 6, 2, 3, 4, 5], [3, 5, 6, 4, 7, 8, 1, 9, 0], [1, 2, 4, 3, 5, 9, 7, 6, 8]]}'
   ```  

### 6. Requesting Network Status  
To check the current status of the network:  

1. Navigate to the `src/scripts` folder:  
   ```bash
   cd src/scripts
   ```  
2. Run the appropriate script:  
   ```bash
   ./network1  # Queries node 1
   ```  

Alternatively, use the REST API:  
   ```bash
   curl http://localhost:8001/network -X GET
   ```  
Replace `8001` with the HTTP port of the target node.

### 7. Requesting Network Statistics  
To retrieve statistics such as the number of validations performed:  

1. Navigate to the `src/scripts` folder:  
   ```bash
   cd src/scripts
   ```  
2. Run the appropriate script:  
   ```bash
   ./stats1  # Queries node 1
   ```  

Alternatively, use the REST API:  
   ```bash
   curl http://localhost:8001/stats -X GET
   ```  
Replace `8001` with the HTTP port of the target node.

---  

## Bookmarks

**GitHub Repository (private | source of the project)**

- [Distributed Sudoku Solver Repository](https://github.com/detiuaveiro/cd2024_proj_-112981_113384)

---

## Team Members

| <div align="center"><a href="https://github.com/tomasf18"><img src="https://avatars.githubusercontent.com/u/122024767?v=4" width="150px;" alt="Tomás Santos"/></a><br/><strong>Tomás Santos</strong><br/>112981<br/><hr/>DevOps</div> | <div align="center"><a href="https://github.com/DaniloMicael"><img src="https://avatars.githubusercontent.com/u/115811245?v=4" width="150px;" alt="Danilo Silva"/></a><br/><strong>Danilo Silva</strong><br/>113384<br/><hr/>Team Manager</div> |
| --- | --- | 