# LCA4DH  
### A Life Cycle Assessment data-driven tool for the evaluation of district heating and cooling networks  

**“Measuring today, designing a sustainable heat for tomorrow.”**

## Synthetic Description  
The authors developed and provided a computational code delivered as an open-source tool written in **Python**.  
The tool allows **energy utility companies** operating in the **District Heating and Cooling (DHC)** sector — as well as other stakeholders — to evaluate the **environmental profile** of the thermal energy supplied to buildings by district networks in an **automated and standardized** way, fully compliant with the requirements of the new **Energy Performance of Buildings Directive (EPBD, version 4)**.  

The tool integrates **Brightway2.5** as its core computational engine for **Life Cycle Assessment (LCA)**.

## Installation and Prerequisites  

Main Python environment and package versions:  

| Package | Version |
|----------|----------|
| python | 3.12.9 |
| jupyterlab | 4.3.6 |
| pandas | 2.2.3 |
| numpy | 1.26.4 |
| nbimporter | 0.3.4 |
| xlsxwriter | 3.2.2 |
| xlrd | 2.0.1 |
| traceback | built-in |
| pathlib | built-in |
| bw2data | 4.4.3 |
| bw2io | 0.9.7 |
| bw2calc | 2.0.1 |
| ecoinvent licence | ecoinvent 3.11 EN 15804+A2 |

## PRINCIPAL ARCHITECTURE OF THE TOOL 
## Computational framework
the computational structure developed for the tool in this research will be simplified when it is compared with what was explained by Beccali, Cellura, and Di Matteo (1997), Heijungs and Suh (2002), Ardente, Beccali, and Cellura (2004). The engine imports an emission/characterization factors matrix (Q'). As noted, it consists of rows representing products (District Heating and Cooling components components) and elementary
flows and columns representing the impact category for each process and environmental intervention. The matrix was then multiplied by an A' matrix to obtain the scores (per functional unit – fU, equal to 1 kWh of heating or cooling provided by the network) for the heating or cooling supplied by the network analyzed. Matrix A' comprises rows representing life cycle Modules and columns representing products and environmental flows (e.g., kg of steel per fU, CO₂ emission for combustion of natural gas per fU, etc.). Figure 3 schematizes the two matrices, A' and Q',
showing the matrix h' with the scores, represented by Modules in rows and impact categories in columns.

## ⚙️ Architectural Framework

The computational engine of **LCA4DH** has been fully implemented in **Brightway2.5**, leveraging its node–edge architecture to perform Life Cycle Assessment (LCA) of District Heating and Cooling Networks (DHCNs).  
Each **node** represents the specific module describing the life cycle of each specific energy system or infrastructure (e.g., boiler, Combined Heat and Power unit, heat pump, thermal storage), while **edges** define material, energy, and emission exchanges among them. This structure allows the model to compute life cycle inventories (LCI) and impacts dynamically, following the physical and logical connections of the analyzed system.

The engine is composed of three interconnected sections:

1. **Input Model**  
2. **Computational Model**  
3. **Output Model**

---

### 🧩 Input Model

The **input model** defines the structure and workflow for incorporating both user-supplied and external datasets.  
Users provide **activity data**, such as operational parameters and technical specifications, via a structured **Excel interface**.  

This file includes:
- An **introductory sheet**, describing the general configuration of the DHCN — including energy system typologies, network parameters, and auxiliary subsystems;  
- A series of **automatically generated sheets**, one for each technology, where the number of rows corresponds to the number of installed units (e.g., multiple boilers or CHP units).  

> Example:  
> A DHCN composed of four natural gas boilers, one CHP unit, and one cooling tower will generate three sheets — one with four rows (boilers), and one each for the CHP and cooling tower.

If **primary data** from the DHCN operator are unavailable, **secondary data** sourced from literature are used as reliable substitutes.

External datasets include:
- **Emission factors** from **ecoinvent 3.11 EN 15804** (Wernet et al., 2016);  
- **Characterization factors** from the **Environmental Footprint (EF 3.1)** method (Fazio et al., 2018);  
- **End-of-Life (EoL)** coefficients for materials and processes.

To optimize computation speed and ensure data integrity, emission factors are **pre-structured** in a *closed-structure* Excel or `.pkl` file.  
A dedicated **Python preprocessor**, operating independently from the Brightway engine, extracts only relevant data from the full ecoinvent database. This process:
- Filters out redundant or irrelevant flows;  
- Normalizes data per **functional unit (fU)**;  
- Stores only the required indicators from the chosen characterization method.  

Similarly, the **EoL parameters** are preprocessed and stored in a separate file (`Parametri_EoL.xlsx`), containing coefficients for recycling, incineration, and landfill fractions. These can be manually adjusted by the user when more reliable primary data become available.

---

### 🔗 Computational Model

The **computational model** represents the core of the engine.  
It operates through a network of **interconnected Brightway activities** (nodes) and exchanges (edges), forming a graph that mirrors the physical and operational structure of the DHCN.

Each activity corresponds to a life cycle module or process stage, consistent with **EN 15804:2019** (CEN, 2019). The relationships defined in previous project phases are implemented to calculate impacts for each component and phase of the network.


These calculations are executed automatically through Brightway’s internal methods, where each node can retrieve and apply emission and characterization data dynamically, ensuring consistency and reproducibility across all modules.

Each module (e.g., *Boiler*, *Heat Pump*, *CHP*, *Thermal Storage*) operates as an independent Brightway script, but all communicate through a **central orchestrating script**, which:
- Aggregates results from all components;  
- Manages exchanges among subsystems;  
- Normalizes results to the **functional unit**;  
- Ensures correct data transfer among life cycle modules.

This architecture supports modular analyses — each component can be assessed independently or integrated into a full system simulation — and allows quick recalculations if input data or parameters are updated.

---

### RESULTS AND OUTPUT

The **output model** consolidates and organizes results derived from the Brightway computational graph.  
While detailed output handling is described in a separate section, the computational engine is designed to provide flexible aggregation of results both **by technology** (e.g., boilers, heat pumps, CHP) and **by life cycle stage** (A–D). 
Outputs can be expressed per functional unit or as relative contributions, enabling users to identify critical components and guide system optimization.

---

### 🧠 Summary

The **Brightway2.5-based architecture** ensures a transparent, modular, and reproducible computational workflow.  
By integrating **structured Excel data**, **ecoinvent 3.11 EN 15804**, and the **EF 3.1** characterization method, the LCA4DH engine provides a scalable platform for evaluating the environmental performance of District Heating and Cooling Networks.

> For further information on input data structures, calibration methodologies, and datasets, please refer to the related scientific publications.

🔧 Backup Operations and Setup Instructions

Before running any simulations, download the entire package without modifying the position or hierarchy of its contents.

1. Required Software

To ensure correct functionality of the computational engine, please install the following tools:

Miniconda

Brightway 2.5

Jupyter Lab

It is strongly recommended to follow the official Brightway installation guide linked above.

2. Importing Ecoinvent Databases

You must also install the Ecoinvent biosphere and Ecoinvent 3.11 EN15804 databases.
Follow the official instructions provided here:
👉 Importing Ecoinvent into Brightway

Important:
During installation, the authors renamed the databases as follows:

- ei = ecoinvent-3.11-EN15804

- bio = ecoinvent-3.11-biosphere

For the tool to work properly, make sure to update these names in the scripts according to the database names you chose during installation.

3. Project Configuration

The tool is designed to run within the LCA4DHC project, which has been preconfigured by the authors.
Users are free to import the package into a different Brightway project; however, for beginners, it is strongly advised not to modify the project structure or its contents.
The tool must be executed in the same Brightway project where the Ecoinvent libraries have been imported.

🗂 Folder Path Configuration
To ensure correct execution, some folder paths must be updated manually:
Open the script Libraries.ipynb.
Modify the following variables according to your local setup:
ENERGYSYSTEM_PATH
ROOT_PATH
base_path
These paths must point to the correct directories within your local environment.
These steps are required only the first time the tool is executed.
Once the tool has been successfully run, you do not need to repeat them.

## EXECUTION

📘 Excel File Compilation

The input data describing the district heating network must be entered in the dedicated Excel file named CompilatoreBackup.xlsx.

This file contains a main sheet called generatorsConfig:

The first section collects general information about the network.

The energy systems section refers to the general inventory of the systems included in the network.

Once the required information has been filled in, clicking the Start button activates a macro that automatically generates additional Excel sheets corresponding to each specific energy system.

Note:
Only the sheets associated with the selected energy systems are activated.
Systems for which the user has set the number of units to 0 will not be activated.

Each sheet related to an energy system requires specific input data for that particular machine or technology.
A reference table is provided below (or in the documentation) listing all required inputs and detailed instructions for completing each section.

All sheets must be fully completed before running the tool.

▶️ Running the Environment
Once Miniconda, Brightway, and the required libraries are installed:
Activate your Brightway environment within Miniconda.
Open Jupyter Lab and navigate to the provided scripts.
Launch the script named RUN.ipynb to initialize the databases and verify the configuration.



