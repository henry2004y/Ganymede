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
simulation domain $10 R_G$ surrounding Ganymede. Outer boundary may have reflections that effect the inner solution, and the inner BC $\mathbf{v}=0$ is inconsistent with the flow measurements from Galileo Plasma Subsystem (PLS).

## Multifluid MHD, 2006

Paty & Winglee. They want to incorporate the effect of multiple ion species. However, the model has some issues with the configuration of the magnetosphere, such that the magnetic field comparison is not good.

## Single fluid MHD, 2008

4 Eqs. stretched spherical coordinates, leapfrog time marching, central differencing in space.

semi-implicit method: introduces a term into the momentum equation that effectively modifies the inertial of the short-wavelength modes, while accurately treating the long wavelengths, enabling the timestep to exceed CFL limit for Alfvén and magnetosonic waves. It achieves efficiency by removing short-wavelength high-frequency oscillations, which are on the scale of grid spacing.

preconditioned conjugate gradient methods are used to invert the matrices.

$0.5-40 R_G$ $131\times 132\times 128 (r,\theta,\varphi)$ grid points. finest grid resolution in $\widehat{r}\sim 0.01 R_G \approx 26\text{km}$, average within the magnetosphere $0.04 R_G\approx 100\text{km}$.

**Core BC**: the magnetic flux corresponding to dipole moment is set at $r=0.5R_G$. tangential $\mathbf{E}$ to be 0 (I don't know why.)

advance the magnetic field between inner BC and core BC by setting $\mathbf{v}=0$, so that there are only magnetic diffusion and numerical diffusion. make the diffusion time very long compared to the typical Alfvén timescale by adjusting $\eta$. $v_A=220\text{km/s}$, Lundquist number $\sim 4000$.

In plasma physics, the *Lundquist number* (denoted by S) is a dimensionless ratio which compares the timescale of an Alfvén wave crossing to the timescale of resistive diffusion.
It is a special case of the Magnetic Reynolds number when the Alfvén velocity is the typical velocity scale of the system, and is given by
$$ S=\frac{Lv_A}{\eta}, $$
where $L$ is the typical length scale of the system, $\eta$ is the magnetic diffusivity and $v_A$ is the Alfvén velocity.

High Lundquist numbers indicate highly conducting plasmas, while low Lundquist numbers indicate more resistive plasmas. Laboratory plasma experiments typically have Lundquist numbers between $10^2-10^8$, while in astrophysical
situations the Lundquist number can be greater than $10^{20}$. Considerations of Lundquist number are especially important in magnetic reconnection.

**Inner BC**: $r=1.05R_G$, ionosphere is treated as a finite-conductivity thin layer populated with cold dense plasma. uniform plasma density and pressure,
$$ n_{surf}=550\text{amu/cm}^3,\ n=39\text{cm}^3 $$

\begin{align}
T_{surf} = 20eV=20/(1.38\times10^{-23})\cdot 1.6\times10^{-19}=2.32\times10^5K, \\
p_{surf}=nk_B T=39\cdot 10^{6}\times k_B\times 20/k_B \cdot(1.6\cdot 10^{-19})\text{Pa}=0.125\text{nPa} .
\end{align}
 flows stop at this BC, $\mathbf{v}=0$. $\eta$ in this layer increases from the background value used far from Ganymede (nearly $0$, which means fully conducting) to the value assumed at the surface in order to mimic the finite electric conductance of the ionosphere. uncertain ionosphere conductance, height-integrated conductance $\Sigma=2S$ in the setup.

**Outer BC**: $r=20 R_G$, divided into upstream ($X\le 0$) and downstream ($X>0$). Fix $\rho,P,\mathbf{v},\mathbf{B},\mathbf{E}_t$ on all points at the upstream; non-reflecting BC, free-to-leave (float) at the downstream.
The flow speed in the reference frame of Ganymede is
$$ \mathbf{v}=140 \text{km/s} $$
The average plasma $n$ is around $4\text{ cm}^{-3}$ with a range from $1$ to $10\text{ cm}^{-3}$. Assuming that mass-charge ratio is $14$, and ions are singly charged. For G8 pass,
$$ P_t=3.8\text{nPa} $$
so that the solar wind temperature is
$$ T_{solar} = P/(nk_B)=3.8\text{ nPa}/(4*1.38\times10^{-23})/1.2=5.7367\times10^7 K $$
This is equivalent to about $250eV$. The coefficient $1.2$ corresponds to the original settings of ion/electron temperature ratio $5$.


It takes only $10$ mins for a quasi-steady state run. This is measured in time-accurate mode.

Magnetopause location is $10\%$ smaller than the observed one. (But this is for G28, not G8)

## Single fluid MHD, 2008
improved results for G8 pass by modifying BCs and adjusting other parameters in the simulation.

Modified BC at the inner boundary $r=1.05R_G$, where roughly represents the location of the peak ionospheric conductivity. In the 2008 work, the conductance of the moon's interior was set very high, which led to a total conductance (sum of interior and ionospheric conductances) that was too high, although the ionspheric contribution used was only $2S$.

Forcing the ionospheric flow to be zero is a reasonably good approximation for a highly conducting obstacle. However, the moon's mantle is most likely to be quite weakly conducting and the conductance of Ganymede's ionosphere is quite uncertain.


* Ionosphere can be considered as a reservoir populated with cold and dense plasma. $\rightarrow$ constant plasma density and pressure is applicable.
* BC1: $\mathbf{v}_r=0,\mathbf{v}_\theta$ and $\mathbf{v}_\phi$ continuous.$\rightarrow$ float. This allows the boundary to act as a hard wall with respect to the flow and prevents the plasma from penetrating the boundary. However, not allowing the flow go through the boundary is not appropriate for an ionosphere with finite conductance. Other issues about this BC
* BC2:  requires the component of the flow velocty perpendicular to the local magnetic field to be continuous at the inner boundary, $\mathbf{v}_{\perp1}=\mathbf{v}_{\perp2}$, where $\mathbf{v}_\perp=\mathbf{v}-\frac{\mathbf{v}\cdot\mathbf{B}}{B}\widehat{b}$

Resistivity profile: between the core boundary $r=0.5R_G$ and the moon's surface $r=1.0R_G$ is the insulating rocky mantle whose electrical conductivity is extremely low ($\sim 0$). No plasma flowing in this region, the model solves for a magnetic diffusion equation only. High numerical resistivity corresponding to a Lundquist number of $0.2$ in this region.

The flowing plasma outside the ionosphere ($r>1.05R_G$) is regarded infinitely conducting $\eta=0$. In terms of conductivity, the ionosphere, whose finite conductivity arises from neutral-ion collisions, can be considered as a transition layer between the insulating mantle and the highly conducting magnetosphere. In the setup, we let the ionospheric resistivity decrease monotonically from its value in the mantle to its background value outside the ionosphere.
$$ \eta=\eta(r) $$
An anomolous resistivity being setup to enable fast reconnection to occur in regions where magnetic shear is strong. It is introduced only outside the ionosphere and is turned on only at locations where the local current density exceeds some threshold.

The global flow pattern should be: plasma flow is brought into the magnetosphere mainly through reconnection on the upstream side and in turn convects over the polar cap into the downstream region. Then it is expected to partially return toward the moon and upstream at low latitude ($z=0$ cut).

## Aurora Estimation, 2015

Payan

## MHD-EPIC, 2016

Tóth

$[-128,128]R_G$, smallest cell size is $1/32R_G$ in a box $x\in [-3,4],y\in [-3,3], z\in[-2,2]$ total 8.5 million cells.

Absorbing inner BC: ($r-1.0R_G$) for inflow, zero gradient is applied (float for $n,p,\mathbf{v}$); for outflow, the radial component of the momentum is reversed. The transverse components of the velocity, the density, and the pressure always have zero gradients.

**magnetic BC**: ($r=1.0R_G$) 0 gradient for the transverse components of $\mathbf{B}_1$ and reflective for the radial component of $\mathbf{B}_1$.

simple fixed inflow and zero-gradient outflow BCs (typically used for the solar wind around planetary magnetospheres)do not work for the subsonic and sub-Alfv\'{e}nic Jovian wind.

Hall effect region: $|x|<4R_G,\ |y|<3 R_G,\ |z|<2R_G$ box.

The flows shown in Fig.5 in $z=0$ cut is very strange. This is Hall MHD results.

The standoff distance is 6% larger than observation.

## Hybrid Model

###

[Parallel hybrid multi-grid model](https://www.sciencedirect.com/science/article/pii/S0021999116000061)

###

[Fatemi](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1002/2016GL068363)

They do not specify the inner boundary conditions in the published paper.
While they have kinetic ions in their model, only the simulated electric and magnetic fields are used in another test particle model to compute the precipitation fluxes for the energetic particles. This probably means that there are some issues with the hybrid model itself, otherwise why not use the information from the model directly?

## Wang, 2018

10-moment equation model.

## Ionosphere Model, 2019

This is a test particle model built in the same group as the first hybrid model by [Carnielli+ 2019](https://www.sciencedirect.com/science/article/pii/S0019103517307054)
