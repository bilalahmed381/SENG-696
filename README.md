# Investigating Data Poisoning in Multi-Agent Code Generation Systems
## Assignment # 1

## 1A — System Specification

### 1. Introduction and Scope
This project develops a **simulated multi-agent environment** to study **data poisoning in collaborative code-generation systems**.  
Multi-agent systems (MAS) are increasingly used in software engineering to automate code writing, review, and testing through cooperation between intelligent agents.  
However, this collaboration also introduces potential **adversarial risks**, where a single poisoned or compromised agent can influence the performance of others.

The goal of this system is to build a **research platform** to inject, observe, and analyze data poisoning in multi-agent collaboration. The study focuses on understanding **how poisoned outputs propagate** through inter-agent communication, affecting overall reliability.

### 2. System Purpose
The system aims to:

- Provide an environment to **simulate and analyze data poisoning** in multi-agent coding workflows.  
- Study how a **maliciously trained code generation agent** affects other collaborating agents.  
- Assess **resilience, trust, and fault tolerance** in collaborative AI systems.  
- Support future integration of **defensive mechanisms** such as anomaly detection or trust scoring.

### 3. Functionalities
The system will consist of several agents responsible for different roles in the software-generation pipeline.  
It extends traditional multi-agent environments by adding a **test generation agent** and a **poisoned agent** for simulation.

| Agent | Functionality |
|--------|----------------|
| **Code Generator Agent** | Generates source code from software specifications. |
| **Code Reviewer Agent** | Reviews and refines generated code. |
| **Test Generator Agent** | Creates automated test cases for generated code. |
| **Coordinator Agent** | Manages communication and workflow between agents. |
| **Poisoned Agent Module** | Simulates adversarially trained or compromised agents to test propagation. |
| **Monitor/Logger Module** | Records communication and tracks poisoning effects. |

### 4. Environment and Tools
The prototype will be built using modular, extensible technologies to support multiple frameworks.

- **Language:** Python  
- **MAS Frameworks:** SPADE, Mesa, or a custom environment  
- **LLM Integration:** For code generation, review, and testing  
- **Data Poisoning Utilities:** Custom adversarial training scripts

### 5. Expected Outcomes
- A working MAS prototype simulating poisoned and unpoisoned interactions.  
- Quantitative analysis of poisoning propagation.  
- Insights for designing **defensive frameworks** for secure, collaborative AI systems.  

---

## 1B — Design Document (MaSE Methodology)

The design follows the **MaSE (Multi-Agent Systems Engineering)** methodology, which structures development through **goal identification**, **role modeling**, **agent architecture**, and **detailed agent descriptions**.

### 1. Goal Identification
**Primary Goal:**  
Investigate how data poisoning propagates and impacts a cooperative multi-agent coding system.

**Subgoals:**
1. Simulate realistic collaboration among code generation agents.  
2. Introduce a poisoned agent and observe its influence.  
3. Study communication-based error propagation.  
4. Evaluate metrics such as contamination rate, accuracy, and dependency strength.

### 2. Role Identification
| Role | Description | Goals Supported |
|-------|--------------|-----------------|
| **Coordinator** | Manages communication and assigns tasks. | All |
| **Code Generator** | Produces code from specifications. | 1, 2 |
| **Reviewer** | Reviews and improves generated code. | 1, 3 |
| **Test Generator** | Builds unit and integration tests. | 1, 3 |
| **Poisoned Agent** | Simulates a compromised agent with malicious logic. | 2, 3 |
| **Monitor/Analyzer** | Logs and analyzes propagation data. | 3, 4 |

### 3. Agent System Architecture

```text
                 ┌────────────────┐
                 │  Coordinator   │
                 └──────┬─────────┘
                        │
      ┌─────────────────┼──────────────────┐
      │                 │                  │
┌────────────┐    ┌────────────┐    ┌──────────────┐
│ Code Gen   │    │ Reviewer   │    │ Test Gen     │
└─────┬──────┘    └─────┬──────┘    └──────┬───────┘
      │                 │                  │
      │                 │                  │
      └─────────────────┴──────────────────┘
                        │
                ┌───────────────┐
                │ Poisoned Agent│
                └───────┬───────┘
                        │
                ┌───────────────┐
                │ Monitor Agent │
                └───────────────┘

````
The **Coordinator Agent** serves as the central controller.  
The **Poisoned Agent** introduces adversarial code into the workflow, while the **Monitor Agent** collects communication and performance data.

### 4. Agent Descriptions

#### **Coordinator Agent**
- Manages workflow and assigns subtasks.  
- Handles message routing and recovery.  
- Ensures coherent integration of all results.

#### **Code Generator Agent**
- Produces code modules from requirements.  
- Shares outputs with Reviewer and Test Generator agents.  
- May be influenced by poisoned training data.

#### **Reviewer Agent**
- Evaluates generated code for correctness and security.  
- Interacts bidirectionally with the Code Generator.  
- Can be indirectly affected by poisoned code inputs.

#### **Test Generator Agent**
- Creates automated unit and integration tests.  
- Detects faulty or poisoned logic via failed tests.

#### **Poisoned Agent**
- Acts as a malicious or compromised generator.  
- Produces subtly incorrect or insecure code.  
- Used to observe error propagation and cascading effects.

#### **Monitor/Analyzer Agent**
- Logs communication and task outcomes.  
- Analyzes patterns of corruption and impact on system performance.

### 5. Internal Agent Architecture

Each agent follows a **Perception → Reasoning → Action** loop.

- **Perception:** Receive input or messages from other agents.  
- **Reasoning:** Apply logic or model (normal or poisoned).  
- **Action:** Produce output and send it to peers or coordinator.  

The **Poisoned Agent** alters its reasoning layer using adversarial parameters to simulate malicious influence.

### 6. Summary

Following the **MaSE methodology** ensures clarity in defining goals, roles, and interactions for the system.  
This design provides a controlled environment to study **error propagation in multi-agent systems** and supports future development of **secure, trustworthy agentic architectures**.
