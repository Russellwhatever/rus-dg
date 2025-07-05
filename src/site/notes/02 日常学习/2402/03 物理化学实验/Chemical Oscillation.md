---
{"dg-publish":true,"permalink":"/02/2402/03/chemical-oscillation/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-04T16:08"}
---

# 1. Objects
To know the mechanism of the oscillating reaction and to determine the apparent activation energy of the oscillating reaction via measuring the open circuit potential-time curve.
# 2. Emperimental principles
## 2.1 Chemical oscillation
For some reactions, the concentrations of certain components fluctuate periodically in a non-equilibrium or nonlinear manner, a phenomenon known as chemical oscillation. 
The bromate-containing chemical oscillation is named after its discoverers, Belousov and Zhabotinsky, and is referred to as the BZ reaction.
## 2.2 Three conditions of chemical oscillation
(1) being an open system far from equilibrium
(2) consisting at least one autocatalytic step
(3) bistable, i.e., the system can oscillatate between two steady states.
## 2.3 BZ reaction
The generally acknowledged mechanism for the BZ reaction is the FKN mechanism, which can essentially be viewed as a reaction comprising three main stages.
### (1) Bromination(when the concentration of $Br^-$ is high)
$$
BrO_3^- + 2Br^- + 3CH_2(COOH)_2 + 3H^+ -> 3BrCH(COOH)_2 + 3H_2O.
$$
### (2) Autocatalytic process(when the concentration of $Br^-$ is low)
$$
BrO_3^- + 4Ce^{3+} + 5H^+ -> HOBr + 4Ce^{4+} + 2H_2O.
$$
### (3) $Br^-$ regeneration
$$
BrCH(COOH)_2 + 4Ce^{4+} + HOBr + H_2O -> 2Br^- + 3CO_2 + 4Ce^{3+} + 6H^+.
$$

For a certain concentration of $Br^-$, the direction of reaction will converse. The critical concentration can be easily calculated.
$$
[Br]_{critical} = \frac{k_6}{k_2} [BrO_3^-] = 5 \times 10^{-6} [BrO_3^-].
$$
Furthermore, with $\ln\left( \frac{1}{t_{u}}  \right)= -\frac{E}{RT}+\ln A$(or $\ln\left( \frac{1}{t_{z}}  \right)= -\frac{E}{RT}+\ln A$), we can calculate the activation energy.
# 3. Apparatus and reagent
  * CHI electrochemical analyzer with computer;
  * Magnetic stirrer;
  * Thermostatted water bath;
  * Saturated calomel electrode with 1 mol·L-1 H2SO4 salt bridge;
  * 100 mL electrolytic cell with jacket;
  * Platinum wire electrode;
  * 100 mL volumetric flask;
  * 10 and 50 mL measuring tubes;
  * 50 and 250 mL beakers;
  * Wash bottle;
  * Glass stirring rod, burette, 2 mL pipette;
  * Balance;
  * Cerium ammonium sulfate (A.R.);
  * Malonic acid (A.R.);
  * Potassium bromate (A.R.);
  * Sulfuric acid (A.R.).
# 4. Procedure
## 4.1 Preparation of the solutions
100 mL of :
 0.005 $mol/L$ cerium ammonium sulfate solution (in 0.2 molL- sulfuric acid)
 0.4  $mol/L$ malonic acid
 0.2  $mol/L$potassium borate
 3  $mol/L$ sulfuric acid
## 4.2 The preparatory works
- Turn on the power supply to warm up the CHI electrochemical analyzer for 10 min.
- turn on the thermostatted water bath (including the power supplies of the heater and stirrer).
- Set up the temperature of the water bath to 30 °C (or about 3 ~ 5 °C higher than the room temperature).
- Add 10 mL respectively of the cerium ammonium sulfate solution, the malonic acid solution and sulfuric acid to the thoroughly washed electrolytic cell.
- Meanwhile, warm the 10 mL potassium bromate solution in the water bath.
 - Set parameters in the working interface of the electrochemical analyzer
## 4.3 Measurement
Click "run" and wait until the baseline is flat(or 60s). Add the pre-warmed 10mL potassium bromate solution to the electrolytic cell. Save the curve data.
## 4.4 Raise the temperature
Raise the temparature of the water bath to 32°C. Take out the electrodes. Wash the electrolytic cell and the electrodes. Then repeat the above procedures. Acquire data lines in every 2°C. 6curves are pictured and saved.
## 5. Data analysis(original experimental data,confirmed and signed, is attached in the appendix)
### 5.1


![99 Attachment/Pasted image 20240909152129.png](/img/user/99%20Attachment/Pasted%20image%2020240909152129.png)

| $\frac{1}{T} \space (10^{-3}K^{-1})$ | $\ln\left( \frac{1}{t_{z}} \right)$ |
| ------------------------------------ | ----------------------------------- |
| 3.3                                  | -4.08429                            |
| 3.279                                | -4.06903                            |
| 3.257                                | -3.957                              |
| 3.236                                | -3.79324                            |
| 3.215                                | -3.66868                            |
| 3.195                                | -3.49953                            |

Based on the time of peaks, the temperature-time curve is pictured and activation energy $E_{z}$ is calculated as $8.314\times 5.80152 KJ/mol = 48.2 KJ/mol$
### 5.2 
![99 Attachment/Pasted image 20240909152422.png](/img/user/99%20Attachment/Pasted%20image%2020240909152422.png)

| $\frac{1}{T} \space (10^{-3}K^{-1})$ | $\ln\left( \frac{1}{t_{z}} \right)$ |
| ------------------------------------ | ----------------------------------- |
| 3.3                                  | -5.00863                            |
| 3.279                                | -4.85281                            |
| 3.257                                | -4.86984                            |
| 3.236                                | -4.59915                            |
| 3.215                                | -4.53689                            |
| 3.195                                | -4.30946                            |
Based on the induction times of different temperature, the temperature-time curve is pictured and activation energy $E_{u}$ is calculated as $8.314\times 6.3715 KJ/mol = 53.0 KJ/mol$
# 6. Discussion
## 6.1 $\ln\left( \frac{1}{t_{z}} \right)-\frac{1}{T}$: Excluding a specific point
As for the $\ln\left( \frac{1}{t_{z}} \right)-\frac{1}{T}$ curve, the (3.30, -4.084) point clearly does not fit the linear trrend and appears to be an unreasonable outlier, so I would like  tro exclude it and re-perform the fitting on the reamaining points. Here is the result. By comparing the $r$(from 0.97931 to 0.99692), the new linear fitting is more resonable. The adopted slope is -6.78886, so $E$ should be $56.44 J/mol$
![99 Attachment/Pasted image 20240909141356.png](/img/user/99%20Attachment/Pasted%20image%2020240909141356.png)
But why is this happen? One possible reason could be that my partner had inadvertently increased the temperature midway through the first trial, resulting in lower than expected $t_{z}$ measurements.