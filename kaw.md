@def title = "Kinetic Alfvén Waves"
@def hascode = false
@def rss = ""
@def rss_title = "Review and research of KAW"
@def rss_pubdate = Date(2022, 8, 5)

# Kinetic Alfvén Waves

陈骝教授真乃等离子体物理界的大师。这篇 [Physics of kinetic Alfvén waves: a gyrokinetic theory approach][Chen+2021]，我目前就只能看懂经典的SAW的部分。

根据文中推断，KAW and whistler waves are different. My gut feeling is that whistler waves can be derived from the two-fluid theory, while KAW can only be properly described with kinetic theories.

## Simulation Setups

### 2D slab

\begin{align}
\rho_m &= \rho_m(x) \\
\mathbf{B}_0 &= B_0\hat{z} \\
\delta B_y(x,t=0) &= \exp(-x^2/\Delta_x^2) \\
|k_y \Delta_x| \ll 1 \\
\partial \delta B_y /\partial t = 0
\end{align}

### 2D magnetopause

The simulation is performed in the XZ plane, with x being the direction normal to the magnetopause and z being the direction of wave vector tangential to the magnetopause. Initially, the magnetopause current sheet in slab geometry is assumed to be centered at $x = 0$ in the middle of the simulation domain, separating two uniform plasma regions of the magnetosheath ($x < 0$) with a high‐density and low‐magnetic field strength and magnetosphere ($x > 0$) with a low‐density and high‐magnetic field. The initial current sheet is assumed to be a tangential discontinuity, with the normal component of magnetic field $B_x = 0$.
The magnetic fields in the magnetosheath and magnetosphere are parallel to each other, but the fields can have an arbitrary angle $\theta = \tan^{-1}(B_y/B_z)$ relative to the 2‐D simulation plane, which is equivalent to allowing a nonzero, east‐west, azimuthal wave vector under a northward IMF.

Let the subscripts “s” and “m” represent the quantities in the magnetosheath and magnetosphere, respectively. The initial profile of the ion number density is given by

\[
n(x) = \frac{1}{2}(n_m + n_s) + \frac{1}{2}(n_m - n_s)\tanh(x/D)
\]

where $D_0$ is the halfwidth of the magnetopause current sheet. The initial ion temperature $T_{i0}$ and the electron temperature $T_{e0}$ are assumed to be uniform everywhere, while the ions are loaded with an isotropic, Maxwellian velocity distribution. For a given magnetosheath ion beta $\beta_{is}$ and $T_{e0}/T_{i0}$, the initial magnetic field $B(x)$ is determined by the total pressure balance

\[
P(x) + \frac{B(x)^2}{2\u_0} = \text{const.}
\]

throughout the simulation domain, where the total thermal pressure $P(x) = P_i(x) + P_e(x)$. The Alfvén speed is then obtained from

\[
V_A(x) = \sqrt{\frac{B(x)^2}{\mu_0 m_i n(x)}} = \frac{2}{m_i}\frac{[B_s^2/2\mu_0 + n_s(T_i+T_e)-n(x)(T_i+T_e)]}{n(x)}
\]

In the simulation, the ion number density in the magnetosheath is chosen to be $N_s = 300$ per cell and the number density in the magnetosphere is $N_m = N_s / 10 = 30$. The uniform grid size in the x direction is chosen to be $\Delta x = 0.5d_{is}$, where $d_{is}$ is the ion skin depth in the magnetosheath, and the grid size in the z direction is $\Delta_z = 2d_{is}$.
The size of the simulation domain is chosen around $L_x \times L_z = 200d_{is} \times 256d_{is}$. The time step is $\Delta t = 0.05\Omega_s^{-1}$, where $\Omega_s$ is the ion gyrofrequency in the magnetosheath (fixed?).

Periodic boundary conditions are assumed at $z = 0$ and $z = L_z$. Open boundary conditions are used at $x = L_x/2$ on the magnetospheric side. The solar wind wave perturbations are imposed from the incoming boundary at $x = -L_x/2$ in the magnetosheath and are assumed to be a sinusoidal wave with a single frequency, $\omega = \omega_0$. For each case, the quantities $k_z, a \equiv \omega_0 /(k_{\parallel 0} V_{As})$, and $\delta V_i$ of the incident wave are prescribed, where $k_{\parallel 0} = k_z \cos(\theta)$ is the initial parallel wave number, $V_As$ is the magnetosheath Alfvén speed, and $\delta V_i$ is the wave amplitude in the flow velocity. Initially, the currents are assumed to be carried solely by ions (WHAT DOES THIS MEAN?). The imposed incident wave is assumed to satisfy the MHD fast mode dispersion relation, which under the given $a$ results in the following expression for wave propagation angle $\alpha \equiv \tan^{-1}(k_\perp/k_\parallel)$:

\[
\cos^2\alpha = \frac{a^2 (C_s^2/V_A^2 + 1) - C_s^2/V_A^2}{a^4}
\]

where $C_s = \sqrt{\gamma P/m_i n}$ is the sound speed, with $\gamma = 5/3$. The perturbations $\delta\mathbf{B}/B_s$, $\delta\mathbf{V}_i/V_{As}$, $\delta n/n_s$, and $\delta T_i/T_s$ are calculated from the set of the ideal MHD equations.
Note that for given $\beta_i$ and $T_e/T_i$, $C_s^2/V_A^2 = \gamma \beta_i (1 + T_e/T_i)/2$. In the simulation, it is found that the most crucial parameters to set up the initial wave are $\omega_0$ and $k_{\parallel 0}$.

| Case | $\theta$ | $\beta_{is}$ | $T_{e0}/T_{i0}$ | $\omega_0$  |  $a$  | $\delta V_i$  |
|------|----------|--------------|-----------------|-------------|-------|---------------|
| 1    | 0        | 0.5          | 0.4             | 0.392       | 2.0   | 0.04          |

### 3D



[Chen+2021]: https://link.springer.com/article/10.1007/s41614-020-00049-3