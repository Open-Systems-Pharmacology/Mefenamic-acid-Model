### 2.3.1 Absorption

Studies including only oral applications of mefenamic acid could be used for model building. During model building  the *in vivo* intestinal permeability and an effective *in vivo* solubility in this PBPK model were optimized (see also [Section 2.3.5](#235-Automated-Parameter-Identification)).

Dissolution kinetics of the Ponstan capsule  were implemented via an empirical Weibull dissolution function. It was tried to identify the respective parameters. Model building, however, showed that these parameters do not appear to be rate-limiting. Thus, the values were fixed to an instantaneous release with a `Dissolution time (50% dissolved)` of 1 minute and a `Dissolution shape` of 10. 

Mefenamic acid is typically administered in fed conditions. Mefenamic acid was administered in the in-house study ([Becker 2015](#5-References)) with meals or snacks. For the 5th administration at 24 h in this study (simultaneous administration with vericiguat) a standard meal in PK-Sim `Meal: High-fat breakfast (Human)` was considered. All other administration considered a snack. The parameter `Meal energy content` for this snack was optimized to best match clinical data  (see also [Section 2.3.5](#235-Automated-Parameter-Identification)).

### 2.3.2 Distribution

Mefenamic acid was reported as being greater than 90% bound to albumin in plasma ([Champion 1978](#5-References)). However, exact values are unknown. Goosen *et al.* ([Goosen 2017](#5-References)) reported a fraction unbound in 2% bovine serum albumin solution of 3.8%. Assuming human serum albumin (HSA) as major binding partner and a HSA concentration in plasma *in vivo* of 40 g/dL = 4%, a calculated fraction unbound in plasma of 1.9% can be obtained. This value was used in this PBPK model. 

An important parameter influencing the resulting volume of distribution is lipophilicty. The reported experimental logP values were in the range of 5. This value served as a starting value. Finally, the model parameter `Lipophilicity` was optimized to best match clinical data (see also [Section 2.3.5](#235-Automated-Parameter-Identification)).

After testing the available organ-plasma partition coefficient and cell permeability calculation methods built in PK-Sim, observed clinical data was best described by choosing the partition coefficient calculation by `Rodgers and Rowland` and cellular permeability calculation by `PK-Sim Standard`. 

### 2.3.3 Metabolism and Elimination

Since this PBPK model was built for the purpose of acting as a perpetrator drug for UGT1A9-mediated drug-drug interactions, no detailed representation of the metabolism and excretion was implemented. A simple unspecific hepatic clearance was optimized to best match clinical data (see also [Section 2.3.5](#235-Automated-Parameter-Identification)).

### 2.3.4 UGT1A9 Inhibition

An in-house *in vitro* study ([Jungmann 2019](#5-References)) evaluated the inhibitory constant (K<sub>i</sub>) of mefenamic acid on the glucuronidation of the selective substrate propofol in recombinant UGT1A9. A mixed-type mechanism, however close to a competitive type, was found. After correcting for fraction unbound (but here this was 1 ([Fricke 2020](#5-References)), the obtained *in vitro* values were directly implemented:

| **Model Parameter** | Value | Unit   | **Description**                           |
| :------------------ | ----- | ------ | ----------------------------------------- |
| `Ki_c`              | 0.3   | µmol/L | K<sub>i</sub> * f<sub>u,inc</sub>         |
| `Ki_u`              | 21.3  | µmol/L | Alpha * K<sub>i</sub> * f<sub>u,inc</sub> |


### 2.3.5 Automated Parameter Identification

This is the result of the final parameter identification.

| Model Parameter                                       | Optimized Value | Unit       |
| ----------------------------------------------------- | --------------- | ---------- |
| `Lipophilicity`                                       | 5.030           | Log Units  |
| `Specific intestinal permeability`                    | 1.41E-05        | cm/min     |
| `Solubility at reference pH`                          | 80.95           | µg/ml      |
| `Specific clearance` (unspecific hepatic clearance)   | 9.503           | l/µmol/min |
| `Meal energy content` of snack (mefenamic acid study) | 29.27           | kcal       |
| `Dissolution time (50% dissolved)` of Ponstan capsule | 1 FIXED         | min        |
| `Dissolution shape` of Ponstan capsule                | 10 FIXED        |            |

