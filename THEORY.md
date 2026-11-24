# Theory and model definition

## Rainfall input

The notebook retrieves daily precipitation (`PRECTOTCORR`, mm/day) from the NASA POWER Daily API at 9.38° N, 80.40° E for 2015–2024. These are gridded estimates. A wet day is defined by the threshold $r_0=1$ mm.

Let $W_t$ be 1 for a wet day and 0 for a dry day. For calendar month $m(t)$, the occurrence model is

$$\Pr(W_t=1\mid W_{t-1}=0)=p_{DW,m(t)},\qquad \Pr(W_t=1\mid W_{t-1}=1)=p_{WW,m(t)}.$$

The monthly probabilities are estimated from consecutive observed day pairs. For a fixed month's parameters, the stationary wet probability used to initialize the chain is

$$\pi_m=\frac{p_{DW,m}}{1-p_{WW,m}+p_{DW,m}}.$$

Conditional on a wet day, rainfall is a shifted gamma distribution:

$$R_t=r_0+X_t,\qquad X_t\sim\mathrm{Gamma}(k_m,\theta_m),$$

where $k_m$ is shape and $\theta_m$ is scale in millimetres. The notebook fits the excess $x_i=r_i-r_0$ by method of moments: $\hat k=\bar{x}^2/s^2$ and $\hat\theta=s^2/\bar{x}$.

## Household water balance

Let $A$ be roof area (m²), $\eta$ collection efficiency, $K$ tank capacity (m³), $D$ daily demand (m³/day), and $S_{t-1}$ storage at the start of a day. Collected runoff is

$$C_t=R_tA\eta/1000.$$

The event order is collection, overflow, then demand:

$$O_t=\max(0,S_{t-1}+C_t-K),$$
$$U_t=\min(D,S_{t-1}+C_t-O_t),$$
$$S_t=S_{t-1}+C_t-O_t-U_t.$$

Here $O_t$ is overflow and $U_t$ is supplied water. Shortage is $D-U_t$. The daily conservation identity is

$$S_{t-1}+C_t=S_t+U_t+O_t.$$

A day is fully supplied when shortage is below $10^{-10}$ m³. Reliability is the fraction of scored days that are fully supplied; it is not a volume-based supply ratio.

## Simulation and uncertainty

One warm-up year is simulated so storage carries into the scored year. Each replication then scores 365 days. If $\rho_i$ is reliability in replication $i$ and there are $N$ independent replications,

$$\hat\rho=\frac{1}{N}\sum_{i=1}^{N}\rho_i,\qquad \hat\rho\pm1.96\frac{s_\rho}{\sqrt{N}}.$$

The interval reflects replication variability conditional on the fitted model. It does not include uncertainty in rainfall observations or fitted parameters.

## Calibration and validation

The notebook fits a validation model using 2015–2022 and checks it on held-out 2023–2024 data. A production fit uses 2015–2024. Rainfall occurrence and wet-day depth parameters are estimated separately by calendar month. The browser demo can load the production calibration CSV; without it, the demo labels its rainfall assumptions illustrative.

## Verification

The notebook checks conservation, boundary cases, tank-capacity monotonicity, a separate reference implementation across randomized cases, Markov stationary probabilities, synthetic parameter recovery, rainfall validation, and Monte Carlo error scaling. Its fixed water-balance benchmark is also reproduced by the browser demo within an absolute tolerance of $10^{-9}$ for five outputs. This deterministic check does not compare random-number streams or establish matching reliability estimates.
