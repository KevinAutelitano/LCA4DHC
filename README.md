# LCA4DHC  
*A Life Cycle Assessment data-driven tool for the evaluation of District Heating and Cooling networks*

---

## Project Goals

LCA4DHC is a data-driven Life Cycle Assessment (LCA) tool designed to support the environmental evaluation of District Heating and Cooling Networks (DHCN).

The tool aims to:

- Evaluate the environmental impacts of heat and cooling supplied by DHC networks on a **life cycle basis**
- Ensure compliance with **EPBD (Energy Performance of Buildings Directive, version 4)** requirements
- Support **standardized and automated** LCA calculations according to **EN 15804 + A2**
- Enable assessments **per technology** and **per life cycle stage (A–D)**
- Integrate **primary data** from network operators with **secondary data** from recognized LCA databases
- Provide a **modular, transparent, and reproducible** computational framework
- Facilitate scenario analysis and system optimization through rapid recalculations

---

## Project Status

- **Stable** – Core computational workflow is fully implemented and functional  
- **Experimental** – Scientific and methodological validation is ongoing  
- **Under active development** – Continuous updates and improvements  

**Operating system**
- Windows  

**Compilers / Interfaces**
- Excel-based input files (`.xlsx`, `.xlsm`)
- Python (via Jupyter Notebook)

---

## Requirements

Main Python environment and package versions required to run the tool:

| Package | Version |
|---|---|
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

➕ **Third party software dependencies (see below)**

---

## Third Party Software

LCA4DHC relies on the following third-party software and databases:

- **Brightway 2.5** – Core Life Cycle Assessment computational framework  
- **Ecoinvent database v3.11 (EN 15804 + A2)** – Emission factors and background processes  
- **Environmental Footprint method (EF 3.1)** – Life Cycle Impact Assessment characterization factors  
- **Miniconda** – Python environment and package management  
- **Jupyter Lab** – Execution environment and user interface  

⚠️ A **valid Ecoinvent license** is required to run the tool.

---

## License

LCA4DHC project is distributed under the **Apache License, Version 2.0 (January 2004)**.

The tool may not be use except in compliance with the License.  
Unless required by applicable law or agreed to in writing, the software is distributed on an **“AS IS” basis**, without warranties or conditions of any kind.

A copy of the License is available at:  
http://www.apache.org/licenses/LICENSE-2.0

---

## Disclaimer

The LCA4DHC tool is provided for **research, academic, and technical support purposes only**.

- The authors **do not guarantee** the absence of errors, inaccuracies, or omissions  
- The authors **accept no liability** for any direct or indirect damages resulting from the use of the tool  
- Users are **fully responsible** for validating the correctness, robustness, and suitability of the results for their specific application  
- Results should be independently reviewed, especially when used for regulatory, policy, or decision-making purposes  

---

## Citation (Academic Use)

If you use this tool in academic work, please cite it as:

> Autelitano, K., & Famiglietti, J. (2025). *LCA Tool for District Heating Networks*. Zenodo. https://doi.org/10.5281/zenodo.xxxxxx

---

## Contributing

Contributions are welcome.  
If you encounter bugs, issues, or have suggestions for improvements, please contact the authors or open an issue in the project repository.

---

## Author / Contact

**Kevin Autelitano**  
*Politecnico di Milano*  
📧 kevin.autelitano@polimi.it  

**Jacopo Famiglietti**  
*Politecnico di Milano*  
📧 jacopo.famiglietti@polimi.it  
