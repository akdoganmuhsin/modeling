# Virus Transmission Dynamics: Horizontal vs. Vertical Transmission

This directory contains the Python simulation and numerical solution for a system of ordinary differential equations (ODEs) modeling infectious disease dynamics that account for both **horizontal** (person-to-person) and **vertical** (parent-to-offspring) transmission pathways.

---

## 1. Governing Equations

The total population is divided into three compartments: Susceptible ($S$), Infectious ($I$), and Recovered ($R$). The system dynamics are governed by the following system of differential equations:

$$\frac{dS}{dt} = \nu (S + R) + \nu (1 - p) I - \beta S I - \mu S$$

$$\frac{dI}{dt} = \beta S I + \nu p I - \gamma I - \mu I$$

$$\frac{dR}{dt} = \gamma I - \mu R$$

### Parameters
* **$\beta$**: Horizontal transmission rate
* **$\gamma$**: Recovery rate
* **$\mu$**: Natural mortality rate
* **$\nu$**: Birth rate
* **$p$**: Vertical transmission probability from infected mother ($0 \le p \le 1$)

---

## 2. Basic Reproduction Number ($R_0$)

Including vertical transmission modifies the effective basic reproduction ratio $R_0$:

$$R_0 = \frac{\beta N + \nu p}{\gamma + \mu}$$

When $p > 0$, the pathogen can persist in the population even under strict isolation protocols ($\beta \to 0$), provided that $\nu p > \gamma + \mu$.

---

## 3. Repository Structure

```text
01-virus-transmission/
│
├── virus_model.ipynb       # Executable Jupyter / Google Colab Notebook
├── output_graph.png        # High-resolution simulation trajectory plot
└── README.md               # Model formulation and documentation
