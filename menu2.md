@def title = "Overview of Ganymede's Simulations"
@def hascode = false
@def rss = ""
@def rss_title = "Overview"
@def rss_pubdate = Date(2020, 7, 24)
@def tags = ["syntax", "code", "image"]

# Overview of Ganymede's Simulations

\toc


## resistive MHD, 2002

Ip and Kopp.

The simulation domain is $10 R_G$ surrounding Ganymede. Outer boundary may have reflections that effect the inner solution, and the inner BC $\mathbf{v}=0$ is inconsistent with the flow measurements from Galileo Plasma Subsystem (PLS).

The BCs are not clearly mentioned.

## Multifluid MHD, 2006

Paty & Winglee. 

The inner boundary lies along the base of the ionosphere, which is held constant on the assumption of a constant source of ionospheric and exospheric material from surface sputtering. Plasma incident on this boundary is lost to the simulation since neither the chemical effects associated with generation of aurora or the surface sputtering is included in the model.

| Variables | Inner Boundary | Outer Boundary (upstream) |
|---|---|---|---|---|
| $\rho$       | fixed, $H^+$ 2000 $\text{cc}^{-1}$, $O^+$ 1000 $\text{cc}^{-1}$  | fixed, 30 amu/cc |
| $P$          | scale height $H=263$ km, 9.0 to 0.1 eV from polar to equatorial| fixed
| $\mathbf{V}$ | float | fixed, 180 km/s |
| $\mathbf{B}$ | ? | fixed |

They want to incorporate the effect of multiple ion species. However, the model has some issues with the configuration of the magnetosphere, such that the magnetic field comparison is not good.

## Single fluid MHD, 2008-2010

4 Eqs. stretched spherical coordinates, leapfrog time marching, central differencing in space.

To maintain $\nabla\cdot\mathbf{B}=0$ condition, the magnetic potential $\mathbf{A}$ is used instead of magnetic field $\mathbf{B}$.

Semi-implicit method: introduces a term into the momentum equation that effectively modifies the inertial of the short-wavelength modes, while accurately treating the long wavelengths, enabling the timestep to exceed CFL limit for Alfvén and magnetosonic waves. It achieves efficiency by removing short-wavelength high-frequency oscillations, which are on the scale of grid spacing.
Preconditioned conjugate gradient method is used to invert the matrices.

$r \in [0.5,40] R_G$, $131\times 132\times 128 (r,\theta,\varphi)$ grid points. finest grid resolution in $\widehat{r}\sim 0.01 R_G \approx 26\text{km}$, average within the magnetosphere $0.04 R_G\approx 100\text{km}$.

The best BCs being advertised:

| Variables | Core Boundary ($r=0.5R_G$) | Surface Boundary ($r=1R_G$) | Outer Boundary (upstream) | Outer Boundary (downstream)|
|---|---|---|---|---|
| $\rho$       |        | fixed, $550 \text{amu}/cm^3$   | fixed | float |
| $P$          |        | fixed, $0.125\textnormal{nPa}$ | fixed | float |
| $\mathbf{V}$ |        | $\mathbf{V}\perp\mathbf{B}$    | fixed | float |
| $\mathbf{B}$ | dipole |                                | fixed | float |

### Core BC 

Set tangential $\mathbf{E}$ to be 0 (I don't know what this means and why.)

Advance the magnetic field between inner BC and core BC by setting $\mathbf{v}=0$[^1], so that there are only magnetic diffusion and numerical diffusion. make the diffusion time very long compared to the typical Alfvén timescale by adjusting $\eta$. $v_A=220\text{km/s}$, Lundquist number $\sim 4000$[^2].

[^1]: My guess is that the implementation is similar to the initial Mercury user module in BATSRUS. This magically works, but violates the basic principles of CFD.

[^2]: In plasma physics, the *Lundquist number* (denoted by S) is a dimensionless ratio which compares the timescale of an Alfvén wave crossing to the timescale of resistive diffusion. It is a special case of the Magnetic Reynolds number when the Alfvén velocity is the typical velocity scale of the system, and is given by $$ S=\frac{Lv_A}{\eta} $$ where $L$ is the typical length scale of the system, $\eta$ is the magnetic diffusivity and $v_A$ is the Alfvén velocity. High Lundquist numbers indicate highly conducting plasmas, while low Lundquist numbers indicate more resistive plasmas. Laboratory plasma experiments typically have Lundquist numbers between $10^2-10^8$, while in astrophysical situations the Lundquist number can be greater than $10^{20}$. Considerations of Lundquist number are especially important in magnetic reconnection.

### Inner BC

$r=1.05R_G$, ionosphere is treated as a finite-conductivity thin layer populated with cold dense plasma. uniform plasma density and pressure,
$$ n_{surf}=550\text{amu/cm}^3,\ n=39\text{cm}^3 $$

\begin{align}
T_{surf} = 20eV=20/(1.38\times10^{-23})\cdot 1.6\times10^{-19}=2.32\times10^5K, \\
P_{surf}=nk_B T=39\cdot 10^{6}\times k_B\times 20/k_B \cdot(1.6\cdot 10^{-19})\text{Pa}=0.125\text{nPa} .
\end{align}
Flows stop at this BC, $\mathbf{v}=0$. $\eta$ in this layer increases from the background value used far from Ganymede (nearly $0$, which means fully conducting) to the value assumed at the surface in order to mimic the finite electric conductance of the ionosphere. uncertain ionosphere conductance, height-integrated conductance $\Sigma=2S$ in the setup.

Later [Duling+, 2014] questioned this approximation. The extension of the resistivity profile outside the surface is only a numerical consideration, which is probably incorrect.

Forcing the ionospheric flow to be zero is a reasonably good approximation for a highly conducting obstacle. However, the moon's mantle is most likely to be quite weakly conducting and the conductance of Ganymede's ionosphere is quite uncertain.

* Ionosphere can be considered as a reservoir populated with cold and dense plasma. $\rightarrow$ constant plasma density and pressure is applicable. (From CFD perspective, fixing both density and pressure is overspecification.)
* reflect $U$: $\mathbf{v}_r=0,\mathbf{v}_\theta$ and $\mathbf{v}_\phi$ continuous.$\rightarrow$ float. This allows the boundary to act as a hard wall with respect to the flow and prevents the plasma from penetrating the boundary. However, not allowing the flow go through the boundary is not appropriate for an ionosphere with finite conductance.
* $B$ dependent $U$:  requires the component of the flow velocty perpendicular to the local magnetic field to be continuous at the inner boundary, $\mathbf{v}_{\perp1}=\mathbf{v}_{\perp2}$, where $\mathbf{v}_\perp=\mathbf{v}-\frac{\mathbf{v}\cdot\mathbf{B}}{B}\widehat{b}$

Resistivity profile: between the core boundary $r=0.5R_G$ and the moon's surface $r=1.0R_G$ is the insulating rocky mantle whose electrical conductivity is extremely low ($\sim 0$). No plasma flowing in this region, the model solves for a magnetic diffusion equation only. High numerical resistivity corresponding to a Lundquist number of $0.2$ in this region.

The flowing plasma outside the ionosphere ($r>1.05R_G$) is regarded infinitely conducting $\eta=0$. In terms of conductivity, the ionosphere, whose finite conductivity arises from neutral-ion collisions, can be considered as a transition layer between the insulating mantle and the highly conducting magnetosphere. In the setup, we let the ionospheric resistivity decrease monotonically from its value in the mantle to its background value outside the ionosphere.
$$ \eta=\eta(r) $$
An anomolous resistivity being setup to enable fast reconnection to occur in regions where magnetic shear is strong. It is introduced only outside the ionosphere and is turned on only at locations where the local current density exceeds some threshold.

### Outer BC

$r=20 R_G$, divided into upstream ($X\le 0$) and downstream ($X>0$). Fix $\rho,P,\mathbf{v},\mathbf{B},\mathbf{E}_t$ on all points at the upstream; non-reflecting BC, free-to-leave (float) at the downstream.
The flow speed in the reference frame of Ganymede is
$$ \mathbf{v}=140 \text{km/s} $$
The average plasma $n$ is around $4\text{ cm}^{-3}$ with a range from $1$ to $10\text{ cm}^{-3}$. Assuming that mass-charge ratio is $14$, and ions are singly charged. For G8 pass,
$$ P_t=3.8\text{nPa} $$
so that the solar wind temperature is
$$ T_{solar} = P/(nk_B)=3.8\text{ nPa}/(4*1.38\times10^{-23})/1.2=5.7367\times10^7 K $$
This is equivalent to about $250eV$. The coefficient $1.2$ corresponds to the original settings of ion/electron temperature ratio $5$.

The initial model in 2008 without resistivity generates a magnetopause which is $10\%$ smaller than the observed one for G28.

The later improved model in 2009 tunes the resistivity.

The Dungey-cycle like global flow pattern should be: plasma flow is brought into the magnetosphere mainly through reconnection on the upstream side and in turn convects over the polar cap into the downstream region. Then it is expected to partially return toward the moon and upstream at low latitude ($z=0$ cut).

## Ideal MHD with Non-Conducting Surface, 2014

| Variables | Inner Boundary | Outer Boundary (upstream) | Outer Boundary (downstream)|
|---|---|---|---|
| $\rho$       | float  | fixed | float |
| $e$          | float  | fixed | float |
| $\mathbf{V}$ | absorb | fixed | float |
| $\mathbf{B}$ | insulating | fixed | float |

The magnetic insulating BC is complicated. Even until now I don't fully understand the derivation.

### Atmosphere and ionosphere

$O_2$: radially symmetric distribution, 0 initial velocity.

The amount of momentum loss is modeled through a collision frequency,
$$ \nu_n(r) = \sigma_n V_0 n_n(r) $$
which is a function of the $O_2$ cross section $\sigma_n = 2.0\times10^{-19}\,m^2$, typical plasma flow velocity $V_0$, and the number density of $O_2$ molecules in the atmosphere. Note that ion-neutral collisions occur predominantly near the surface where the plasma flow speed $V$ is significantly reduced from the Jovian background flow speed $V_0$. Nevertheless, the collision frequency is only a weak function of $V$ since $\sigma_n$ scales approximately with $V^{-1}$ for elastic collisions in the polarization approximation.

The atmosphere is approximated with a hydrostatic model and a constant scale height $H$:
$$ n_n(r) = n_{n,0} \exp{\frac{R_G - r}{H}} $$

They choose a scale height $H = 250$ km even though the real scale height close to the surface is likely smaller.
With a estimated column density of $2\times10^{14} \text{cm}^{−2}$ and the chosen scale height, the estimated number density on the surface is about $n_{n,0} = N_n∕H \approx 8.0\times10^{12} \text{m}^{−3}$.

The **photo-ionization** process contributes to plasma mass loading. This process is characterized by a production rate
$$ P(r) = \nu_{\text{ion}}n_n(r). $$
For simplicity a globally averaged and constant solar radiation is assumed and the shadow caused by Ganymede’s body as well as the variability of Ganymede’s position on its orbit are neglected. Therefore, the production rate directly scales with the density of the atmosphere and thus only has a radial dependency. The photo-ionization rate is chosen to be $\nu_\text{ion} = 2.2\times10^{−8} \text{s}^{−1}$.

Plasma can also be lost through **dissociative recombination**. The occurrence of recombination depends on the thermal energy of the electrons and consequently the recombination rate is a function of the plasma particle density $n = \rho∕m_i$ and the electron temperature $T_e$.
An empirical dissociative recombination rate coefficient is applied
$$ \alpha = 1.6 \Big(\frac{300\,\text{K}}{T_e}\Big)^{0.55}\times 10^{13} \text{m}^3/\text{s}$$
of gaseous oxygen for temperatures higher than 1200 K. An electron temperature of $k_B T_e = 0.1\,\text{eV}\approx 1160\,\text{K}$ is used and results in $\alpha \approx 7.8\times10^{-14}\,\text{m}^3/\text{s} $.
Since the real electron temperature is unknown, whichever yields a reasonable ionospheric mass density is chosen.
To avoid the ion plasma density decreases below the mostly atomic background ion density $n_0 = \rho_0∕m_i$, the loss rate is modified by
\[
L(\mathbf{r},t) =
\begin{cases}
\alpha n(\mathbf{r},t)(n(\mathbf{r},t) - n_0) & \text{for } n(\mathbf{r},t) > n_0,\\
0 & \text{for } n(\mathbf{r},t) \le n_0.
\end{cases}
\]

When equalizing the production and loss rate to receive the plasma number density at the surface in chemical equilibrium,
$$ n_s = \sqrt{\frac{\nu_\text{ion}n_{n,0}}{\alpha}}. $$

The estimated surface density the therefore around $n_s\approx 1500\, \text{cm}^{-3}$, which is higher than previous observation and close to another model estimation.

## Aurora Estimation, 2015

Payan

## MHD-EPIC, 2016

Tóth

| Variables | Inner Boundary | Outer Boundary (upstream, downstream) | Outer Boundary (sides)|
|---|---|---|---|
| $\rho$       | float  | fixed | float |
| $P$          | float  | fixed | float |
| $\mathbf{V}$ | absorb | fixed | float |
| $\mathbf{B}$ | float for $\mathbf{B}_{1\theta}$ and $\mathbf{B}_{1\phi}$, reflect for $\mathbf{B}_{1r}$ | fixed | float |

$[-128,128]R_G$, smallest cell size is $1/32R_G$ in a box $x\in [-3,4],y\in [-3,3], z\in[-2,2]$ total 8.5 million cells.

simple fixed inflow and zero-gradient outflow BCs (typically used for the solar wind around planetary magnetospheres)do not work for the subsonic and sub-Alfv\'{e}nic Jovian wind.

Hall effect region: $|x|<4R_G,\ |y|<3 R_G,\ |z|<2R_G$ box.

The flows shown in Fig.5 in $z=0$ cut is very strange. This is Hall MHD results.

The standoff distance is 6% larger than observation.

## Hybrid Model

###

[Parallel hybrid multi-grid model](https://www.sciencedirect.com/science/article/pii/S0021999116000061)

The incident plasma is injected at the entry plane following a Maxwellian velocity distribution.

Particle BC:
* periodic boundary conditions are used to deal with particles coming from the incident plasma flow;
* planetary particles are lost when leaving the simulation domain.

The BCs are not fully described in the paper.

| Variables | Surface Boundary ($r=1R_G$) | Outer Boundary (upstream) | Outer Boundary (downstream)| Outer Boundary (side)|
|---|---|---|---|---|
| Particle | fixed, 0 | Maxwellian | float | particle-dependent |
| $\mathbf{E}$ | ? | fixed, $-\mathbf{V}\times\mathbf{B}$ | float | periodic   |
| $\mathbf{B}$ | ? | fixed | float | periodic |


###

[Fatemi](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1002/2016GL068363)

They do not specify the inner boundary conditions in the published paper.
While they have kinetic ions in their model, only the simulated electric and magnetic fields are used in another test particle model to compute the precipitation fluxes for the energetic particles. This probably means that there are some issues with the hybrid model itself, otherwise why not use the information from the model directly?

## Wang, 2018

10-moment equation model.

## Ionosphere Model, 2019

This is a test particle model built in the same group as the first hybrid model by [Carnielli+ 2019](https://www.sciencedirect.com/science/article/pii/S0019103517307054)

## MHD-EPIC, 2019-2020

Zhou

| Variables | Core Boundary ($r=0.5R_G$) | Surface Boundary ($r=1R_G$) | Outer Boundary (upstream, downstream) | Outer Boundary (sides)|
|---|---|---|---|---|
| $\rho$       |        | fixed, $550 \text{amu}/cm^3$   | fixed | float |
| $p$          |        | fixed, $0.115\textnormal{nPa}$ | fixed | float |
| $p_e$        |        | fixed, $0.01\textnormal{nPa}$  | fixed | float |
| $\mathbf{V}$ |        | $\mathbf{V}\perp\mathbf{B}$    | fixed | float |
| $\mathbf{B}$ | dipole |                                | fixed | float |
