@def title = "Shocks"
@def hascode = true
@def rss = ""
@def rss_title = "Review and research of shocks"
@def rss_pubdate = Date(2021, 11, 8)

# Shocks

\toc

Let subscripts 1 and 2 refer to the upstream and downstream of the shock. All the basic derivations assume a 1D shock.

## MHD Regime

The basic RH relations are listed in [MHD shocks](https://en.wikipedia.org/wiki/Shocks_and_discontinuities_(magnetohydrodynamics)).

There are 6 scalar equations and 12 scalar variables ($\rho, v_t, v_n, p, B_t, B_n$ for both upstream and downstream). This means that given all the upstream quantities, the downstream values are deterministic[^mhdshock].

[^mhdshock]: I am not entirely sure.

The categories are shown in the following table. We refer the changes of the downstream compared with the upstream.

|     Type      | Particle Transport | $\rho$ | $\mathbf{v}$ | $p$ | $\mathbf{B}$ | T |
|:-------------:|:------------------:|:------:|:------------:|:---:|:------------:|:---:|
| Contact    | No | $\pm$  | continuous | continuous  | continuous | $\pm$ |
| Tangential[^pause] | No | $\pm$  | continuous | $\pm$  | $B_n$ = 0  | $\pm$ |
| Slow    | Yes | + | - | + | $B_t$ - | + |
| Intermediate[^special] | Yes | continuous | $\pm$ | $\pm$  | rotation?  | $\pm$ |
| Fast[^bow]    | Yes | + | - | + | $B_t$ + | + |

[^pause]: The Earth's magnetopause is generally a tangential discontinuity.

[^special]: A special case is called *rotational discontinuity*. All are isentropic. Their existence are still a matter of debate.

[^bow]: The Earth's bow shock is a fast mode shock.

## Double Adiabatic Theory

The classical approach by Chew, Goldberger, and Low [CGL][CGL1956] utilizes the MHD framework by assuming isotropic distributions parallel and perpendicular to the magnetic field, which results in scalar pressures on the two sides of the shock.

When we shift to the MHD with anisotropic pressure tensor

\[
P_{ij} = p_\perp \delta_{ij} + (p_\parallel - p_\perp)B_i B_j / B^2,  
\]

where $p_\perp$ and $p_\parallel$ are the pressures perpendicular and parallel w.r.t. the magnetic field, respectively.
For the strong magnetic field approximation, the two pressures are related to the plasma density and the magnetic field strength
by two adiabatic equations,

\begin{align}
\frac{d}{dt}\Big( \frac{p_\parallel B^2}{\rho^3} \Big) &= 0, \\
\frac{d}{dt}\Big( \frac{p_\perp}{\rho B} \Big) &= 0.
\end{align}

This is also known as the double adiabatic theory,[^note] which is also what many people remember to be the key conclusion from the CGL theory. Here I want to emphasize the meaning of *adiabatic* again: this assumes zero heat flux. If the system is not adiabatic, the conservation of these two quantities related to the parallel and perpendicular pressure is no longer valid, and additional terms may come into play such as the stochastic heating.

[^note]: These are constants at a fixed location in time: it is **not** correct to apply these across the shock!

The general jump conditions for discontinuities in a collisionless anisotropic magnetoplasma in the CGL approximation were derived by [Abraham-Shrauner 1967][Abraham-Sharuner1967].

The general jump conditions for an anisotropic plasma are given by [Hudson 1970][Hudson1970]

\begin{align}
[\![ \rho v_n ]\!] &= 0, \\
[\![ v_n\mathbf{B}_t - \mathbf{v}_t B_n ]\!] &= 0, \\
[\![ p_\perp + (p_\parallel - p_\perp)\frac{B_n^2}{B^2} + \frac{B_t^2}{8\pi} + \rho v_n^2 ]\!] &= 0, \\
[\![ \frac{B_n \mathbf{B}_t}{4\pi}\big( \frac{4\pi(p_\parallel - p_\perp)}{B^2} - 1 \big) +\rho v_n \mathbf{v}_t ]\!] &= 0, \\
[\![ \rho v_n\big( \frac{\epsilon}{\rho} + \frac{v^2}{2} + \frac{p_\perp}{\rho} + \frac{B_t^2}{4\pi \rho} \big) + \frac{B_n^2 v_n}{B^2}&(p_\parallel - p_\perp) \\
- \frac{\mathbf{B}_t\cdot\mathbf{v}_t B_n}{4\pi}\big( 1 - \frac{4\pi(p_\parallel - p_\perp)}{B^2} \big) ]\!] &= 0, \\
[\![ B_n ]\!] &= 0,
\end{align}

where ρ is the mass density, v and B are the velocity and magnetic field strength. Subscripts t and n indicate tangential and normal components with respect to the discontinuity. Quantities $p_\perp$ and $p_\parallel$ are the elements of the plasma pressure
tensor perpendicular and parallel with respect to the magnetic field. Quantity $\epsilon$ is the internal energy, $\epsilon = p_\perp + p_\parallel/2$, and $[\![ Q ]\!] = Q_2 - Q_1$, where subscripts 1 and 2 signify the quantity upstream and downstream of the discontinuity. These equations refer to the conservation of physical quantities, i.e. the mass flux, the tangential component of the electric field, the normal and tangential components of the momentum flux, the energy flux, and, finally, the normal component of the magnetic field. To solve the jump equations for anisotropic plasma conditions upstream and downstream of the shock, one has to use an additional equation, since the set of equations is underdetermined.

The following derivations originate from [Erkaev+ 2001][Erkaev2001].
Let us introduce two dimensionless parameters, $A_s$ and $A_m$, which are determined for upstream conditions as

\begin{align}
A_s &= \frac{p_{\perp 1}}{\rho_1 v_1^2} \\
A_m &= \frac{1}{M_A^2},
\end{align}

where $M_A$ is the upstream Alfvén Mach number. For common solar wind conditions, both of these parameters are quite small ($\sim 0.01$).

For shocks, the tangential components of the electric and magnetic fields are coplanar.[^coplanar] Thus, the components of the magnetic field upstream of the shock are given as $B_{n1} = B_1 \cos\gamma$ and $B_{t1} = B_1 \sin\gamma$, where γ is the angle between the magnetic field vector and the vector $\widehat{n}$ normal to the discontinuity. Similarly, the components of the bulk velocity upstream of the shock are chosen as $v_{n1} = v_1 \cos\alpha$ and $v_{t1} = B_1 \sin\alpha$, where α the angle between the bulk velocity and the normal component of the velocity. Furthermore, a parameter λ is used to denote the pressure anisotropy

\[
\lambda = p_\perp / p_\parallel,
\]

and another parameter x is used to denote the ratio of density

\[
x \equiv \frac{\rho_2}{\rho_1} = \frac{v_{n1}}{v_{n2}}.
\]

[^coplanar]: I still don't fully get it...

### Perpendicular Shock

For a perpendicular shock, $B_n = 0$, we have the conservation relations reduce to

\begin{align}
[\![ \rho v_n ]\!] &= 0, \\
[\![ v_n\mathbf{B}_t ]\!] &= 0, \\
[\![ p_\perp + \frac{B_t^2}{8\pi} + \rho v_n^2 ]\!] &= 0, \\
[\![ \rho v_n \mathbf{v}_t ]\!] &= 0, \\
[\![ \rho v_n\big( \frac{\epsilon}{\rho} + \frac{v^2}{2} + \frac{p_\perp}{\rho} + \frac{B_t^2}{4\pi \rho} \big) ]\!] &= 0.
\end{align}

The quantities downstream of the discontinuity are

\begin{align}
B_{t2} &= x B_{t1}, \\
v_{t2} &= v_{t1}, \\
p_{\perp 2} &= p_{\perp 1} + \frac{B_{t1}^2}{8\pi}(1-x^2) + \rho_1 v_{n1}^2\big( 1 - \frac{1}{x} \big). 
\end{align}

Substituting these into the energy equation leads to

\begin{align}
2 \lambda_1(3\lambda_2 +1)y^3 − \lambda_1(4\lambda_2 +1)(2A_S + A_M +2)y^2 \\
+ \lambda_2[2\lambda_1(4A_S + 1 + 2A_M ) + 2A_S ]y + A_M \lambda_1 = 0,
\end{align}

where $y = 1/x$.

Now we can do some simple estimations. Assume we have isotropic upstream solar wind with $n = 2 \textrm{amu/cc}$, $\mathbf{v} = [600, 0, 0] \textrm{km/s}$, $\mathbf{B} = [0, 0, -5] \textrm{nT}$ in GSM coordinates, and $T = 5\times 10^5 \textrm{K}$.
We want to estimate the downstream anisotropy given a density/tangential magnetic field jump of 3.

```julia
using Vlasiator: kB, μ₀, mᵢ

n1 = 2e6  # [m^3]
v1 = 6e5  # [m/s]
B1 = 5e-9 # [T]
T1 = 5e5  # [K]
λ1 = 1.0

As = kB * T1 / (mᵢ * v1^2)        # 0.011
Am = B1^2 / (μ₀ * mᵢ * n1 * v1^2) # 0.016

x = 3     # downstream/upstream jump density ratio
y = 1 / x

λ2 = (-2λ1*y^3 + λ1*(2As+Am+2)*y^2 - Am*λ1) /
   (6λ1*y^3 - 4λ1*(2As+Am+2)*y^2 + (2λ1*(4As+1+2Am)+2As)*y)

@show λ2
```

which shows $\lambda_2 \simeq 3.19$. In Vlasiator 2D I get 15 in the equatorial plane with spatial resolution 300 km downstream near the shock, which is much larger than this.

### Parallel Shock

Parallel shocks are more special in that the magnetic field strength remains unchanged so the equations effectively describe pure gasdynamic solutions.
[Kuznetsov & A.I.Osin, 2018][Kuznetsov2018] presents a simplified solution in a 1D parallel shock case with parallel and perpendicular thermal energy heat fluxes $S_\parallel$ and $S_\perp$ included. Note again the original CGL theory assumes 0 heat fluxes.

### Anisotropy in the solar wind

Observationally, Pioneer 6 showed that the ion temperature anisotropy in the solar wind at 1AU generally has $T_\parallel > T_\perp$[^pioneer6]. It may possibly be explained by the conservation of the 1st adiabatic invariant [Scarf+, 1967][Scarf1967][^oldpaper].

[^pioneer6]: There are 3 interesting discoveries from Pioneer 6 ARC plasma measurements:
1. high fluctuations of flow velocity outside the solar ecliptic plane;
2. anisotropic ion thermal distribution ($T_\parallel / T_\perp \sim [2,5]$);
3. presence of a 3rd species, helium, from charge-to-mass ratio analysis of the angular and energy distributions.

[^oldpaper]: I love this old paper. The pioneers in our field did real physics.

The magnetic moment

\[
\mu = \frac{m v_\perp^2}{2B}
\]

is conserved as the collisionless solar wind flows outward from the sun.
Near the solar equator the mean field magnitude declines with

\[
B_r(r) \simeq B_r(r_0)\Big( \frac{r_0}{r} \Big)^2
\]

and

\[
B_\phi(r) \simeq \frac{\Omega_r}{u(r)}B_r(r)
\]

from the Parker spiral solar wind model and $\Omega_r = 2.94\times 10^{-6}$ rad/s being the angular frequency of the rotation of the sun.

The adiabatic equation in the perpendicular direction indicates that the perpendicular thermal energy $\langle m v_\perp^2/2\rangle = k_B T_\perp$ declines with B. Assuming in the rest frame the distribution function is a bi-Maxwellian of the form

\[
f(v) = \Big( \frac{m}{2\pi}  \Big)^{3/2}\frac{1}{k_B T_\perp (k_B T_\parallel)^{1/2}} exp\Big( -\frac{mv_\perp^2}{2k_B T_\perp} -\frac{mv_\parallel^2}{2k_B T_\parallel} \Big),
\]

the conservation of the total thermal energy

\[
W = \int d^3v \frac{mv^2}{2}f(v)
\]

yields

\[
W = k_B T_\perp + k_B T_\parallel/2 = const.   
\]

These allows us to evaluate the variations in $T_\perp$ and $T_\parallel$ originating from isotropic distribution on the surface of the sun. Starting from $T_\perp(0.3 AU) = T_\parallel(0.3 AU)\simeq 1.3\times 10^{5}\textrm{K}$, the predicted anisotropy at Earth can go beyond 20! Therefore in fact, the reasonable question to ask is why the actual solar wind anisotropy factor is so small.[^upstream]

[^upstream]: This is new to me. Since I've been involved in the simulation reseach, we always apply isotropic distribution in the upstream solar wind condition, which I guess is primarily due to the fact that we are mostly using MHD. Should we now use more realistic distributions with the kinetic models?

Well, we know now when pressure anisotropy develops, two kinds of plasma instabilities can be triggered: firehose when $T_\perp < T_\parallel$ and mirror when $T_\perp > T_\parallel$. Further studies require kinetic theory to describe their behaviors.

On the other hand, the opposite case, $T_\perp > T_\parallel$, is also observed and believed to be related to local ion heating by macroscale compressions (e.g. high/low speed streams interaction) or plasma instabilities [Barne+ 1975][Barne1975].

Here I list the mirror instability criterion as an additional relation to determine the pressure anisotropy downstream of the shock from the book Plasma instabilities and nonlinear effects by Hasegawa 1975,

\[
1 + \sum_{\textrm{species}} \beta_\perp \big( 1 - \frac{\beta_\perp}{\beta_\parallel} \big) < 0.   
\]

### Earth bow shock

Using data from the AMPTE/IRM spacecraft, [Hill+ 1995][Hill1995] have shown that the double adiabatic equations
do not hold in the magnetosheath. Moreover, the thermal behaviour of the magnetosheath is studied by [Phan+ 1996][Phan1996]
using WIND spacecraft data. They report that most parts of the magnetosheath are marginally mirror unstable.[^wind]

[^wind]: WIND has electron observations and shows $T_{e\perp} / T_{e\parallel} \sim 1.3$ in the magnetosheath.


[CGL1956]: https://doi.org/10.1098/rspa.1956.0116
[Abraham-Sharuner1967]: https://doi.org/10.1017/S0022377800003366
[Scarf1967]: https://doi.org/10.1029/JZ072i003p00993
[Hudson1970]: https://doi.org/10.1016/0032-0633(70)90036-X
[Barne1975]: https://doi.org/10.1029/GL002i009p00373
[Hill1995]: https://doi.org/10.1029/94JA03194
[Phan1996]: https://doi.org/10.1029/96GL00845
[Erkaev2001]: https://doi.org/10.1017/S002237780000893X
[Kuznetsov2018]: https://doi.org/10.1016/j.physleta.2018.05.029