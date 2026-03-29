# 🚨 Agent-Based Simulation of Emergency Evacuation in University Lecture Halls

> **Master's Thesis | Clausthal University of Technology | Institute of Computer Science | September 2025**

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Platform: NetLogo](https://img.shields.io/badge/Platform-NetLogo%207.0-blue.svg)](https://ccl.northwestern.edu/netlogo/)
[![Status: Completed](https://img.shields.io/badge/Status-Completed-brightgreen.svg)]()
[![University: TU Clausthal](https://img.shields.io/badge/University-TU%20Clausthal-red.svg)](https://www.tu-clausthal.de/)

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Research Questions](#-research-questions)
- [Key Features of the Model](#-key-features-of-the-model)
- [Simulation Architecture](#-simulation-architecture)
- [Lecture Hall Layouts](#-lecture-hall-layouts)
- [Behavioral Strategies](#-behavioral-strategies)
- [Experimental Design](#-experimental-design)
- [Key Results & Findings](#-key-results--findings)
- [Repository Structure](#-repository-structure)
- [Getting Started](#-getting-started)
- [Technologies & Skills](#-technologies--skills)
- [Author & Supervisors](#-author--supervisors)
- [License](#-license)

---

## 🔍 Overview

Emergency evacuations from crowded spaces such as university lecture halls present significant challenges for ensuring human safety. This project presents a **sophisticated agent-based simulation model** built in **NetLogo**, designed to analyze the complex dynamics of emergency evacuations in these specific environments.

The model investigates the critical interplay between:
- 🏛️ **Architectural design** — how hall layouts affect escape routes and bottlenecks
- 🧠 **Human behavioral psychology** — panic contagion, herding, rational decision-making
- ⏱️ **Evacuation efficiency** — total clearance time, agent flow rates, congestion patterns

This research provides **evidence-based insights for university administrators, safety planners, and architects** — delivering a powerful tool for assessing the safety of existing lecture halls and designing safer educational spaces.

> **Why this matters:** Most agent-based evacuation studies focus on generic public spaces (shopping malls, transit hubs). This thesis specifically addresses the *unique architectural and behavioral challenges* of university lecture halls — fixed seating rows, narrow aisles, tiered layouts, and high occupant density — a largely under-studied domain.

---

## ❓ Research Questions

This thesis was guided by the following core research questions:

1. How can agent-based models be tailored to simulate emergency evacuations specifically in **lecture hall settings**?
2. What are the **critical architectural and behavioral factors** influencing evacuation efficiency?
3. How do **different layout designs and occupancy patterns** impact evacuation effectiveness?
4. What **behavioral rules and decision-making processes** best represent realistic evacuation scenarios?
5. How do variations in **exit configurations and seating arrangements** affect safety outcomes?

---

## ⚙️ Key Features of the Model

| Feature | Description |
|---|---|
| **Heterogeneous Agents** | Students + Professor, each with distinct behavioral profiles |
| **4 Evacuation Strategies** | Panic-Rush, Calm-and-Orderly, Nearest-Exit (Rational), Herding (Follow-Others) |
| **Mixed Population Mode** | Realistic blend of all strategy types in configurable proportions |
| **Panic Contagion** | Social panic spread modeled as a contagion among nearby agents |
| **Modified Dijkstra Pathfinding** | Custom BFS-based pathfinding with cost weights for navigation |
| **Mobility Impairments** | Agents with reduced mobility affecting movement speed realistically |
| **Tiered & Stair Navigation** | Physical effects of stair aisles and tiered seating on agent speed |
| **Exit Blockage Scenarios** | Experiments with partial or full exit obstruction |
| **BehaviorSpace Integration** | Automated batch experiments across hundreds of parameter combinations |
| **Real-Time Visualization** | Color-coded panic levels, congestion heatmaps, agent flow tracking |

---

## 🏗️ Simulation Architecture

The model is built around four core components:

```
┌─────────────────────────────────────────────────────┐
│                  NetLogo Environment                │
│                                                     │
│  ┌──────────────┐      ┌──────────────────────────┐ │
│  │  Agent Layer │      │   Environment Layer       │ │
│  │              │      │                           │ │
│  │ • Students   │◄────►│ • Hall Layout (Grid)      │ │
│  │ • Professor  │      │ • Exit Configurations     │ │
│  │ • Behaviors  │      │ • Obstacles & Aisles      │ │
│  └──────┬───────┘      └──────────────────────────┘ │
│         │                                            │
│  ┌──────▼───────────────────────────┐               │
│  │       Behavior & Decision Layer   │               │
│  │                                   │               │
│  │ • Pathfinding (Modified BFS)      │               │
│  │ • Panic Propagation (Contagion)   │               │
│  │ • Exit Choice Strategy            │               │
│  │ • Social Dynamics (Herding)       │               │
│  └──────┬────────────────────────────┘              │
│         │                                            │
│  ┌──────▼──────────────────────────┐                │
│  │         Data & Metrics Layer     │                │
│  │                                  │                │
│  │ • Evacuation Time Tracking       │                │
│  │ • Bottleneck Detection           │                │
│  │ • Panic Level Monitoring         │                │
│  │ • Agent Flow Rate Analysis       │                │
│  └──────────────────────────────────┘               │
└─────────────────────────────────────────────────────┘
```

---

## 🏛️ Lecture Hall Layouts

Five distinct lecture hall configurations were modeled and compared:

| Layout | Description | Key Characteristic |
|---|---|---|
| **Traditional** | Single front/rear exit, standard row seating | Baseline reference |
| **Center-Aisle Only** | Single central aisle leading to one exit | Creates bottleneck pressure |
| **Tiered Seating** | Stepped rows with stair navigation constraints | Realistic auditorium model |
| **Dual-Aisle** | Two parallel aisles with distributed exits | Improved flow distribution |
| **Wide Auditorium** | Large-scale hall with multiple exit points | High-capacity scenario |

---

## 🧠 Behavioral Strategies

Agents are assigned one of the following evacuation strategies, each grounded in established evacuation psychology literature:

**1. 😰 Panic-Rush**
- Agents experience rapidly escalating panic levels
- Erratic movement, tendency to freeze at extreme panic (>90%)
- Compresses interpersonal spacing at bottlenecks

**2. 🧘 Calm-and-Orderly**
- Methodical movement toward exits without crowd influence
- Maintains personal spacing and avoids collisions

**3. 🗺️ Nearest-Exit (Rational)**
- Dynamic exit selection based on distance and real-time congestion
- Improves exit load balance when visual field is unobstructed

**4. 👥 Herding (Follow-Others)**
- Agents follow visible moving neighbors
- Can lead to efficient dispersion *or* severe congestion depending on early random movements

**5. 🔀 Mixed Population**
- Configurable blend of all the above (e.g., 40% panic, 30% orderly, 20% rational, 10% herding)
- Most realistic scenario for real-world evacuation modeling

---

## 🧪 Experimental Design

Experiments were conducted using **NetLogo BehaviorSpace** for automated batch simulation across hundreds of parameter combinations:

| Parameter | Values Tested |
|---|---|
| Lecture Hall Layout | Traditional, Center-Aisle, Tiered, Dual-Aisle, Wide-Auditorium |
| Evacuation Behavior | Panic-Rush, Calm-and-Orderly, Nearest-Exit, Mixed-Population |
| Initial Panic Level | 0%, 20%, 50% |
| Number of Students | Variable (low to high density) |
| Exit Blockage | None, Partial, Full |
| Familiarity Percentage | 0% – 100% (% of agents familiar with exits) |
| Exit Width | Narrow to wide configurations |

**Primary Metrics Collected:**
- Total evacuation time (ticks)
- Agent flow rate (agents/unit time)
- Bottleneck formation locations and duration
- Average panic level over time
- Congestion event count by behavior type

---

## 📊 Key Results & Findings

### 🏆 Finding 1: Symmetry Wins
Symmetrical exit arrangements with balanced sightlines enabled significantly more equitable utilization of available evacuation capacity, reducing congestion duration and physical compression near doors. When visual symmetry was disrupted — by obstructions or asymmetric design — flows became lopsided, reinforcing queues at salient exits regardless of travel-time efficiency.

### 🚪 Finding 2: Aisle Width is Critical
Narrow feeder aisles throttle approach rates upstream of adequately sized doors. **Targeted widening of aisles yielded marked improvements** in clearance times and local density without requiring changes to door widths — a cost-effective retrofit strategy.

### 😱 Finding 3: Herding is Fragile
Herding behavior produced either serendipitous dispersion *or* severe congestion depending on stochastic early movements, underscoring the fragility of relying on self-organization without guided interventions.

### 🧭 Finding 4: Rational Agents Need Visibility
Rational navigators improved exit load balance when visibility allowed dynamic route comparison — but their advantage evaporated under occlusion from smoke or architectural barriers.

### 👨‍🏫 Finding 5: Leader Agents Have Disproportionate Impact
Leader agents (e.g., the professor) demonstrated disproportionate positive impact when their positioning maximized visual reach over major seating sectors. Placement outside these influence corridors sharply curtailed their effectiveness.

### 🔑 Overarching Conclusion
> *"Safe and efficient lecture hall evacuation depends on anticipating predictable interactions between space-use biases and built environment affordances under stress. The most reliable improvements arise from **combined interventions** addressing both geometry and expected behavior — rather than isolated fixes."*

**Practical Design Recommendations:**
- Treat balanced sightlines as evacuation capacity — not just door widths
- Evaluate feeder aisles with the same scrutiny as exit hardware
- Manage door proximity to avoid premature merging of crowd streams
- Preserve perceptual access to all exits alongside any structural changes
- Deploy trained personnel (leaders) in positions of maximum visual coverage

---

## 📁 Repository Structure

```
📦 emergency-evacuation-simulation/
│
├── 📄 README.md                        ← You are here
│
├── 📂 simulation/
│   └── EvacModel_FINAL_UPDATE_V2.nlogox   ← NetLogo simulation model
│
├── 📂 thesis/
│   └── MASTER_THESIS_FINAL_SID.pdf    ← Full thesis document (101 pages)
│
└── 📂 docs/                           ← (Optional) Additional figures, screenshots
    └── screenshots/                   ← NetLogo GUI & result visualizations
```

---

## 🚀 Getting Started

### Prerequisites

- **NetLogo 7.0.0** or higher — [Download here](https://ccl.northwestern.edu/netlogo/download.shtml)
  - Free and open-source, runs on Windows, macOS, and Linux

### Running the Simulation

1. **Clone or download** this repository:
   ```bash
   git clone https://github.com/Sidharthkris/emergency-evacuation-simulation.git
   cd emergency-evacuation-simulation
   ```

2. **Open NetLogo** on your system.

3. **Load the model file:**
   `File → Open → simulation/EvacModel_FINAL_UPDATE_V2.nlogox`

4. **Configure parameters** in the interface panel:
   - Select a `lecture-hall-layout` (e.g., `tiered`, `dual-aisle`)
   - Choose an `evacuation-behavior` (e.g., `mixed-population`)
   - Set `initial-panic-level` and student count

5. **Click `Setup`** to initialize the environment, then **`Go`** to start the simulation.

### Running Batch Experiments (BehaviorSpace)

For automated multi-run experiments:
`Tools → BehaviorSpace → Select Experiment → Run`

This allows systematic comparison across all parameter combinations and exports results as CSV for further analysis.

---

## 🛠️ Technologies & Skills

This project demonstrates the following skills relevant to IT and software engineering roles:

| Category | Technologies / Concepts |
|---|---|
| **Simulation & Modeling** | NetLogo, Agent-Based Modeling (ABM), BehaviorSpace |
| **Algorithms** | Modified Dijkstra / BFS Pathfinding, Contagion Modeling |
| **Data Analysis** | Statistical analysis of simulation outputs (scatter plots, box plots, histograms) |
| **Software Design** | Modular simulation architecture, parameterized experimental design |
| **Academic Research** | Systematic literature review, scientific writing (English & German), peer-reviewed citation |
| **AI Tools** | Effective use of ChatGPT, Claude, Gemini for brainstorming and code optimization |
| **Documentation** | LaTeX (thesis), Markdown (README), structured code documentation |

---

## 👤 Author & Supervisors

**Author:** Sidharth Vijayan Krishnan
📚 M.Sc. Computer Science — Clausthal University of Technology (TU Clausthal), Germany
📅 Thesis submitted: September 26, 2025

**Supervisors:**
- Prof. Dr. Robert Bredereck — Clausthal University of Technology
- Dr. Tobias Ahlbrecht — Institute of Computer Science, TU Clausthal

---

## 📄 License

This work is licensed under a **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

You are free to share and adapt this material for any purpose, provided appropriate credit is given.

[![CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

---

*If you find this project useful or interesting, please consider giving it a ⭐ — it helps with visibility and is appreciated!*
