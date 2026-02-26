# LCA4DHC  
*A Life Cycle Assessment data-driven tool for the evaluation of District Heating and Cooling networks*

---

## Project Goals

LCA4DHC is a data-driven Life Cycle Assessment (LCA) tool designed to support the environmental evaluation of District Heating and Cooling (DHC) networks.

The tool aims to:

- Evaluate the environmental impacts of heating and cooling supplied by DHC networks from a **life cycle perspective**
- Ensure compliance with **EPBD (Energy Performance of Buildings Directive, version 4)** requirements
- Support **standardized and automated** LCA calculations according to **EN 15804 + A2 and EN 50693**
- Enable assessments **per technology** and **per life cycle module (from A to D) - from-creadle-to-creadle**
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
- **ecoinvent database v3.11 (EN 15804)** – Emission factors and background processes.
- Other versions of the ecoinvent database can be used; be sure to change process names used in the database when required.
- **Environmental Footprint method (EF 3.1)** – Life Cycle Impact Assessment characterization factors  
- **Miniconda** – Python environment and package management  
- **Jupyter Lab** – Execution environment and user interface  

⚠️ A **valid ecoinvent license** is required to run the tool.

---

## Life Cycle Impact Indicators

The LCA4DHC tool currently implements a selected set of **Life Cycle Impact Assessment (LCIA) indicators** in accordance with **EN 15804 + A2 and EN 50963**, using characterization methods from **Environmental Footprint (EF v3.1)**.

The following indicators are available in the current version of the tool:

| Acronym | Impact category (EN 15804 + A2) | Method reference |
|------|---------------------------------|------------------|
| CC | Climate change – total | EF v3.1 – IPCC 2021 |
| CCfossil | Climate change – fossil | EF v3.1 – IPCC 2021 |
| CCbio | Climate change – biogenic | EF v3.1 – IPCC 2021 |
| CCluc | Climate change – land use and land use change | EF v3.1 – IPCC 2021 |
| A | Acidification | EN 15804 + A2 |
| EF | Eutrophication – freshwater | EN 15804 + A2 |
| EM | Eutrophication – marine | EN 15804 + A2 |
| ET | Eutrophication – terrestrial | EN 15804 + A2 |
| POF | Photochemical oxidant formation (human health) | EN 15804 + A2 |
| PM | Particulate matter formation | EN 15804 + A2 (additional indicators) |
| OD | Ozone depletion | EN 15804 + A2 |
| ERnren | Energy resources – non-renewable | EN 15804 + A2 |
| PENRT | Total use of non-renewable primary energy resources | EN 15804 + A2 |
| RUMM | Material resources – metals and minerals | EN 15804 + A2 |
| WU | Water use | EN 15804 + A2 |

Indicator selection and implementation are fully transparent within the computational workflow and can be extended in future releases.

---

## License

                                 Apache License
                           Version 2.0, January 2004
                        http://www.apache.org/licenses/

   Copyright 2026 Kevin Autelitano and Jacopo Famiglietti

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

             http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.

---

## Disclaimer

The **LCA4DHC** tool is provided for *research, academic, and technical support purposes only*.

- The authors do **not guarantee** the absence of errors, inaccuracies, or omissions.
- The authors accept **no liability** for any direct or indirect damages resulting from the use of the tool.
- Users are **fully responsible** for validating the correctness, robustness, and suitability of the results for their specific application.
- Results should be **independently reviewed**, especially when used for regulatory, policy, or decision-making purposes.
- The Excel input file **`DataInput` must be fully completed in all its sections**, with all required data fields properly filled in. Incomplete or partially compiled input files may lead to invalid or misleading results.

### Thermal capacity definition

When providing **thermal capacity values** for energy conversion systems (e.g., boilers, Combined Heat and Power units, heat pumps, etc.), users must refer to the **useful thermal power delivered to the water circuit** of the district heating or cooling network.

### Scenario configuration

Users can modify decarbonization scenarios for the **natural gas vector** and **refrigerant gases** by selecting the reference scenario year. This enables the analysis of different decarbonization pathways over time.

Prospective scenarios for the **electricity** and ** other components** are *not implemented* in this tool. For electricity-related prospective assessments, please refer to the  
[PRospective EnvironMental Impact asSEment (premise)](https://doi.org/10.1016/j.rser.2022.112311).

---

## References

This tool is based on the following peer-reviewed publications:

- **Famiglietti, J., Toosi, H. A., Dénarié, A., & Motta, M.** (2022).  
  *Developing a new data-driven LCA tool at the urban scale: The case of the energy performance of the building sector*.  
  **Energy Conversion and Management**, 256, 115389.  
  https://doi.org/10.1016/j.enconman.2022.115389
  
- **Vauchez, M., Famiglietti, J., Autelitano, K., Colombert, M., Scoccia, R., & Motta, M.** (2023).  
  *Life Cycle Assessment of District Heating Infrastructures: A Comparison of Pipe Typologies in France*.  
  **Energies**, 16(9), 3912.  
  https://doi.org/10.3390/en16093912

- **Autelitano, K., Famiglietti, J., Toppi, T., & Motta, M.** (2023).  
  *Empirical power-law relationships for the Life Cycle Assessment of heat pump units*.  
  **Cleaner Environmental Systems**, 9, 100135.  
  https://doi.org/10.1016/j.cesys.2023.100135
  
---

## Citation (Academic Use)

If you use this tool in academic work, please cite it as:

> Autelitano, K., & Famiglietti, J. (2026). *LCA Tool for District Heating Networks*. Zenodo. https://doi.org/10.5281/zenodo.18302949

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

## Acknowledgments

This tool was funded by the National Recovery and Resilience Plan (NRRP), Mission 4 Component 2 Investment 1.3—Call for tender No. 1561 of 11.10.2022 of Ministero dell’Università e della Ricerca (MUR)—and funded by the European Union, NextGenerationEU, project code PE0000021, Concession Decree No. 1561 of 11.10.2022 adopted by Ministero dell’Università e della Ricerca (MUR), CUP–D43C2200309001, according to attachment E of Decree No. 1561/2022, project title “Network 4 Energy Sustainable Transition–NEST.”

