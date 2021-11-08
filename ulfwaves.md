@def title = "ULF Waves"
@def hascode = false
@def rss = ""
@def rss_title = "Review and research of ULF waves"
@def rss_pubdate = Date(2020, 11, 8)

# ULF Waves

\toc

Ultra-low frequency (ULF) wave, $f \in [0.001, 10]$ Hz, inside MHD regime, easily detected.

ULF waves were originally called micropulsations or magnetic pulsations since they were first observed by ground magnetometers. ULF pulsations are classified into two types: *pulsations continuous (Pc)* and *pulsations irregular (Pi)* with several subclasses (Pc1–5 and Pi1–2) according to their frequencies and durations.[^1]

| Notation | Period Range [s] |
|----------|------------------|
| Pc1      | 0.2 - 5          |
| Pc2      | 5 - 10           |
| Pc3      | 10 - 45          |
| Pc4      | 45 - 150         |
| Pc5      | 150 - 600        |
|          |                  |
| Pi1      | 1 - 40           |
| Pi2      | 40 - 150         |

[^1]: The Pc5 range originates from the Mariner 5 (1967) detection limitation to a Nyquist frequency of 1.67mHz, which corresponds to 600s. It roughly maps to $60^o\sim 70^o$ latitude on Earth's surface.

With respect to polarization, ULF waves can be categorized into three modes: poloidal ($\Delta B_r,\, \Delta E_\phi$), compressional ($\Delta B_\parallel,\, \Delta E_\phi$), and toroidal ($\Delta B_\phi,\, \Delta E_r$). Here, $B_r$ ($E_r$), $B\_parallel$, and $B_\phi$ ($E_\phi$) are the radial, parallel (or compressional), and azimuthal components in the local magnetic field system, respectively.

2 types of origins:

* from the solar wind
* within the magnetosphere

Hypothesis:
Near radial (?) IMF conditions -->
Alfvén/ion cyclotron and mirror modes in the magnetosheath --> 
Magnetospheric ULF waves: propagate without significant change to their spectrum

Electron and ion foreshocks are where ULF waves are generated.

Changing parameters:

* wind speed
* cone angle(?)

## Drivers

Driver in the solar wind: 

* periodic compressional fluctuations --> magnetopause surface waves
* Alfvénic fluctuations $\delta \mathbf{V}/ \mathbf{V}_A = \pm \delta \mathbf{B}/ \mathbf{B}_0$ direct excitation
* fast stream --> KHI on the magnetopause --> surface mode/waveguide

When the magnetopause can be described as a tangential discontinuity ($B_n = 0$), the MHD wave transmission is not efficient;
when the magnetopause is a rotational discontinuity ($B_n\neq 0$), MHD wave transmission can occur over a wide range of incident angle and that the transmitted waves are usually amplified. The favored ULF wave range may lie within Pc5.

The correlation between solar wind speed and ULF power in the magnetosphere suggests that the Kelvin-Helmholtz instability (KHI) resulting from the velocity shear at the magnetopause may be a significant source of ULF wave energy. KHI studies were very active in the 1980s, but since then nothing really significant has been reached.

Boundary layer thickness --> over-reflection modes at the magnetopause
*Over-reflection* occurs when the characteristic scales of the wave and the inhomogeneity are comparable, and may provide an efficient process for the extraction of energy from the magnetosheath to magnetospheric waveguide modes on the flanks during fast solar wind speed intervals.
This may explain the production of discrete frequency ULF waves in the magnetosphere and statistical correlations between Pc5 power on the ground and solar wind velocity

Opinion:
Alfvénic waves propagating along the magnetopause surface may develop into standing Alfvén waves on the boundary due to reflection from the conjugate ionospheres (i.e. Kruskal-Schwarzschild modes). The surface waves are likely due to magnetopause displacements as a result of local pressure perturbations in the magnetosheath, while the eigenfrequencies of the standing modes are determined by the magnetopause geometry and are strikingly similar to the Samson "magic" frequencies.
This combination of conditions suggests that the oscillations are more likely due to Kruskal-Schwarzshild modes than solar wind pressure perturbations or the KHI at the flanks.

Within the magnetosphere, there are two possible mechanics:

* drift-mirror instabilities (?) due to high $\beta$ pressure anisotropies
* drift-bounce resonance (?) with trapped energetic ions

From observation, $T_\perp / T_\parallel > 5$ is practically treated as high anisotropies.

strongly compressional, high azimuthal wave number m, attenuated on the ground.

## Wave Generation and Propagation Mechanisms

[Menk, 2011][Menk2011]的综述文章只能硬着头皮看。太多从文章中抄出来的经验性总结了,对于入门新手极不友好。

David Southwood, Margy Kivelson, and Steven Schwartz have done a lot in this field.

Quote from Steven Schwartz's paper:
> For most aspects of space plasmas, and certainly for the waves observed in the magnetosheath, fluid-based descriptions of any kind are inadequate, particularly under the $\beta > 1$ conditions found there. And we have not yet considered complications due to inhomogeneity and nonlinearity!

Given a background plasma state, a wave mode is a normal mode or eigenstate of the system.
The eigen-value is usually taken to be the (complex) wave frequency $\omega$, with the real wave-vector $\mathbf{k}$ prescribed.
The associated eigenvector is the set of fluctuating fields ($\delta\mathbf{E},\delta\mathbf{B}$) and plasma parameters ($\delta \rho, \delta\mathbf{u}, \delta P$ in the case of MHD or $\delta f_j(\mathb f{v})$ for kinetic waves where j stands for each species).
Mode identification is the process of comparing the observed eigenvalue/eigenvector with the possible theoretical ones and finding the one which matches.

The practical implementation of mode identification is strewn with pitfalls and complications, including:

* There is usually a mixture, possibly phase-coherent, of modes and/or frequencies, rather than an isolated mode.
* Frequencies are often Doppler shifted by an unknown, or poorly known, amount.
* Wave vectors are difficult to determine from the one-(or few-) point measurements available from spacecraft.
* The mode eigenstate can depend sensitively on the wave vector, plasma $\beta$, and temperature anisotropy, as well as on the contributions of multi-species or non-Maxwellian kinetic features.
* The temporal resolution and accuracy of some measurements, notably those related to particle populations and plasma moments, are often insufficient or marginal. Some important species or sub-population may not be measured at all. The result is that either or both the background state or fluctuations are not accurately known.
* Wave amplitudes are often large (of order unity), implying nonlinear processes may be present and distort the eigenstate from its linear form, or give rise to intrinsically nonlinear eigenstates.
* Similarly, inhomogeneities can distort the wave propagation or eigenstate in ways which have largely been unexplored.
* As we have seen, the theoretical wave properties depend on the framework in which the theory is performed. There is a trade-off between the simplicity/dubious applicability of MHD or fluid treatments and the complexity associated with the infinite degrees of freedom of kinetic theory.

Our ultimate goal, is to build a tool for identifying wave modes automatically. Steven has already envisioned two types of models (decision tree, N-dimensional distance sampling) in 1996. 20 years later, people would find it more appealing to use machine learning.

The propagation of magnetospheric ULF plasma waves has been described usually usually in the context of standing shear Alfvén mode field line oscillations with low azimuthal wavenumber that are driven by energy coupling from incoming compressional fast mode waves.

global eigenoscillations of the magnetosphere or the plasmasphere

termed the plasmaspheric global mode a virtual resonance (?)

The mathematical description of field line resonance (FLR) often assume a simple dipole magnetic field which is not appropriate to high latitudes where field lines experience significant temporal distortion.
This affects the _frequency_ and _polarization_ properties of the FLRs.
The latter is important because wave-particle energy transfer involves the wave electric field component parallel to the drift velocity of particle, i.e. the azimuthal field (poloidal mode) in a dipolar magnetic field.

The Poynting flux is field aligned and away from the equatorial plane. These waves likely arise from incoming compressional mode
waves coupling to guided Alfvén waves on the last closed field lines, exciting FLRs at lower latitudes.

Estimation on how much energy does a FLR deposit into the ionosphere, the energy dissipated into the ionosphere via Joule heating

Simply speaking, the nice math derivations does not work for nonideal magnetic field setup. Observers are clueless in knowing what is really going on.

The MHD wave equations that describe the coupling between the fast compressional mode and the shear Alfvén mode are complicated and have not been completely solved analytically, even in a simple dipole geometry.

Downstream of the quasi-perpendicular portion of the bow shock, solar wind protons and heavier ions (helium ions) are  preferentially heated in the perpendicular direction to the magnetic field.[^heating] This heating creates strong temperature anisotropies which lead to intense wave growth. Several kinds of instabilities can be triggered: mirror mode instability and L-mode electromagnetic ion-cyclotron instability (EMIC).
EMIC mode dominates when the plasma β is low while mirror mode dominates when the plasma β is high.
Slow modes may also be present within a transition layer close to the subsolar magnetopause, although they are expected to suffer strong damping.

[^heating]: Yuxi provides me with a nice starting point to think about this. The 1st adiabatic invariant, i.e. magnetic moment $\mu_m = \frac{1}{2}m v_\perp^2 / B$ is almost conserved if the gyromotion is not violated. Across the quasi-perpendicular shock, the strength of the magnetic field increases, so the perpendicular thermal velocities must increase to maintain the magnetic moment. Therefore the perpendicular direction is preferentially heated downstream of the shock. For example, if the B field is increased by a factor of 2, then the ion perpendicular thermal velocity should increase by a factor of $\sqrt{2}$, and the ion perpendicular pressure should also increase by a factor of 2? In my 2D equatorial run with $Bz=-5$ nT, at downstream $Bz=-15$ nT, but the pressure anisotropy ($P_\perp / P_\parallel$) reaches ~20. Why is that?

All mode identifications are based on _linearized_ theory in a _homogeneous_ plasma and there are clear indications, in both the data and in numerical simulations, that nonlinearity and/or inhomogeneity modify even the most basic aspects of some modes.

Turbulence is also frequently observed in the magnetosheath, i.e. O(1) fluctuations in density, bulk velocity, and magnetic field over a broad range of frequencies.

### Isotropic MHD waves

#### Fast/Slow wave

In linearized ideal isotropic MHD, fast, slow, and Alfvén mode are all linearly dispersive, i.e. phase velocity independent of the wavelength.

compressive, $P_B$ and $P_t$ in phase for fast mode and in anti-phase for slow mode

fast mode nearly isotropic for phase speed, while the slow mode is strongly guided by magnetic field direction

Theoretically, slow and fast MHD waves usually are quickly damped in collisionless plasmas with moderate to high plasma β (Barnes, 1966), leaving only outward propagating Alfvén waves.

Fast mode: ion/ion right-hand resonant

#### Alfvén wave

non-compressive, travels along the magnetic field, i.e. group velocity is field-aligned, $\delta{u} \parallel \delta{\mathbf{B}}$

ion/ion left-hand resonant

#### Entropy wave

There is a 4th zero-frequency mode from MHD theory, referred to as entropy mode, which is often ignored.
It is a compressional wave (i.e., fluctuations in pressure and density) that can be either hydrodynamic or magnetohydrodynamic in which the internal energy and velocity remains constant.
It represents a spatially structured medium in static equilibrium???

\[
\frac{Ds}{Dt} = \frac{\partial s}{\partial t} + \mathbf{u}\cdot\nabla{s} = 0
\]

and it travels at the bulk velocity.

### Anisotropic MHD waves

CGL theory (Chew+ 1956)

#### Firehose instability

The Alfvén wave remains transverse but becomes the firehose instability for $P_{0\parallel} > P_{0\perp} + B_O^2/\mu_0$.

ion/ion nonresonant

#### Fast mode

very similar to the isotropic case

#### Mirror mode wave

The slow magnetosonic mode becomes the mirror instability for anisotropies satisfying

\[
\frac{P_{0\perp}}{P_{0\parallel}} > 6 \Big( 1 + \frac{B_0^2}{2\mu_0 P_{0\perp}} \Big) = 6 \Big( 1 + \frac{P_B}{P_{0\perp}} \Big).
\]

The lowest threshold corresponds to wave-vectors perpendicular to the background magnetic field.

Since it originates from slow mode, the density and magnetic field fluctuations are in strict anti-phase.

Interestingly, the mirror mode is unstable in kinetic theory for temperature anisotropies satisfying

\[
\frac{T_\perp}{T_\parallel} > 1 + \frac{1}{\beta_\perp},
\]

which is similar to that found in mixed kinetic-fluid treatments, and disagrees by a factor of 6 with the result in CGS approximations given above. This relation confirms that the mirror mode is favored by large $\beta$.

As this threshold is reached, the first unstable mode hasaa wave vector $\mathbf{k}$ which is nearly perpendicular to $\mathbf{B}_0$. As the anisotropy is increased, however, the most unstable mode shifts to more oblique $\mathbf{k}^'$s, reaching $\theta_{kB_0} \simeq 60^o$ for $T_\perp / T_\parallel \ge 2$. Warm/hot electrons modify the instability threshold to some extent, and decrease the growth rate.

### Electromagnetic Ion-Cyclotron Waves (EMICWs)

Ion-cyclotron waves are driven by an ion temperature anisotropy $T_\perp / T_\parallel > 1$, as is commonly found in the magnetosheath. The instability is strongest for parallely propagating modes ($\theta_{kB_0} \sim 0^o$) and is weakly dependent on the ion $\beta$. The mode is left-hand polarized at parallel propagation in the plasma rest frame, being cyclotron resonant with  the ions. Maximum growth corresponds to wave numbers $k \simeq 0.5 - \omega_{pp}/c$, where $\omega_{pp}$ is the proton plasma frequency.

Ion-cyclotron wave can be derived in a Hall MHD framework: it comes as one of the two solutions from the dispersion relation, the other being electron-cyclotron wave, more commonly known as whistler wave.
In Schwartz's review paper, he always wrote Alfvén/ion-cyclotron modes together, most likely to stress the fact that ion-cyclotron wave is left-hand polarized.

[A dissertation on EMIC waves in the Earth’s Magnetosphere][Lee2014]

The waves are generally believed to be generated in the equatorial magnetosphere by

* ion-cyclotron resonance with unstable distributions of energetic ring current ions during the recovery phase of magnetic storms
* during compressions of the day-side magnetopause (??? Thorne 2013)

The characteristic fine structure appearance of ‘pearl’ Pc1 waves was attributed to dispersive field-aligned wave packet propagation in the LH ion mode on successive bounces between hemispheres. However, this still lacks observation support.
Spacecraft measurements have shown that EMICW propagation is almost exclusively away from the equator at latitudes greater than about 11◦, with minimal reflection at the ionosphere.

The preferential region of occurrence of EMIC waves is known to be the afternoon magnetic local time (MLT) sector from ∼12:00 to ∼18:00 MLT in the region near the plasmapause and the plasmaspheric plume.

Recent modeling efforts have focused on clarifying the locations and conditions for EMICW generation, including the effect of heavy ion populations, and explaining the modulated appearance of wave packets. However, there is no clear consensus on a dominant mechanism.
These are important questions since EMIC waves may control the precipitation of energetic ions and relativistic electrons.

Plasma density is one of the most important parameters controlling EMIC wave generation. Growth models which assume the total plasma is dominated by thermal plasma may not relate to regions where both cold plasmaspheric plasma and ring current ions are important.

[Gamayunov and Khazanov, 2008][GamayunovKhazanov2008] using a global RCEMIC simulation model suggests that suprathermal plasma plays a role in destabilizing the more energetic ring current and/or plasma sheet distributions to a high energy anisotropy.
It also suggests that for best data comparison the EMICW source is located at the equator and that waves reflect at off-equatorial latitudes at the bi-ion hybrid frequencies in conjugate hemispheres.

self-written model, no name, ray-tracing equations in plasma

Yoshiharu Omura and his students once had a proceeding about _Competition Between the Mirror Mode Instability and the L-Mode Electromagnetic Ion Cyclotron Instability_. They performend hybrid 1D-3D simulations and tried to explain the observation that mirror instability dominates the L-mode EMIC instability in the Earth's magnetosheath. This is puzzling since the EMIC instability generally has higher linear growth rate than that of the mirror instability.

[Shoji+2009][Shoji2009]

During the linear stage, they found that EMIC waves saturates at an earlier stage in higher dimensions, and mirror mode wave can gain more free energy from the temperature anisotropy.

During the nonlinear stage:
> In the 3D case mirror mode coalescence is much more rapid. Because of this rapid change, electric fields are induced, and the energy of the electromagnetic fields is converted to the thermal energy of particles. At the end of the nonlinear evolution, the 
structures in the 3D model collapse. On the other hand, in the 2D model, the large structure remains. Through the 
nonlinear evolution resulting plasma turbulence in the 3D model, the particles are heated by the induced electric field in the perpendicular direction. They are diffused in pitch angles to parallel direction and to make beta in the parallel 
direction larger.

简单点说就是虽然离子回旋波在线性阶段长得快，但它很容易饱和并且空间自由度越高饱和得越快。在饱和以后

particle scattering and trapping by waves. Hmm, I'm not familiar with these at all.

In the outer radiation belt, the frequency typically ranges between 0.1 to 5 Hz.

[Medeiros+ 2020][Medeiros2020] introduces a machine learning model for recognizing EMICWs from spectrograms. First she introduces the traditional approach of EMICW identification in near-Earth space via Fourier analyses of locally measured magnetic field data:

1. The Fourier power spectral density (PSD) in units of ${nT}^2 Hz^{−1}$ is plotted in a frequency-versus-time graph, yielding the so-called spectrogram.
2. Eye inspection of the wave packets' magnetic field amplitude, which in turn translates to (usually) localized, in both time and frequency, enhancements of PSDs relative to background values.
3. Computational techniques that interactively analyze the pixel intensities of the spectrogram's images against the background.

When wave packets are clearly distinct from the background, the interval can be considered as having a candidate EMIC wave event. Since the waves are in the 0.1–5 Hz frequency range, the data acquisition rate must be at least twice as high to resolve the wave packets.

我看到几个2Dshock模拟，都是选一个平行磁场一个垂直磁场（即GSM中的XZ平面）做的。根据我现在的理解，EMIC波在平行于背景磁场方向最为显著。有点怀疑在垂直磁场平面内我们能不能看到EMIC波......而且根据产生条件垂直方向温度大于平行方向温度，在一个2D垂直平面上，第三个方向也就是平行方向永远是周期性边界，我该怎么理解这件事情？在我们的模拟中，我的确看到了很强的垂直温度，所以理论上EMIC

## Observation

1. discrete magic frequencies
Field line resonance (FLR), which is phenonmenon about standing Alfvén waves excited on geomagnetic field lines (i.e closed field lines whose foot points lie in the ionosphere), are observed in the Pc5 range, with discrete frequencies at approximately 1.3, 1.9, 2.6, and 3.4 mHz. Possible mechanisim:
* MHD waveguide
* MHD cavity modes

In fact, the coupling of cavity or waveguide eigenmodes to FLRs may explain how discrete spectra are produced across a range of latitudes, including at the "magic" frequencies.
The global cavity modes _may be_ responsible for the appearance of ULF signals with multiple discrete spectral peaks at the "magic"
frequencies and spanning a range of latitudes, but it lacks observation support and is hard to detect with satellites. (This is interesting!)

In the 1970s, KHI is cited as the source of compressional energy required for the excitation of FLRs. However, later people have found that the same can be triggered by solar wind dynamic pressure fluctuation. 
Simultaneous measurements are applied to show that periodic fluctuations in the solar wind dynamic pressure drives ULF pulsations in the magnetosphere. A one‐to‐one correspondence was observed between the solar wind number density oscillation frequencies and oscillation frequencies in dayside magnetic field measurements from the GOES satellite. Even magnetotail lobe oscillations have been associated with upstream dynamic pressure fluctuation. One statistical study in 2009 by Viall+ is trying to argue that 50% of the ULF waves in the magnetosphere is driven by upstream solar wind dynamic pressure fluctuations. 

In [SouthwoodKivelson1990], they provide a theoretical work on the FLRs and cavity mode as magnetospheric response to solar wind dynamic pressure changes.

## Simulations

### Korean MHD Model

[Park+, 2002]: the interaction of solar wind density pulse with the bow shock.

spherical, $10 \text{R}_E$ < r < $40 \text{R}_E$, $10^o < \theta < 170^o$, $0^o < \phi < 180^o$.[^gridthought]

[^gridthought]: For bow shock and sheath study, this might be good enough since it's super-Alfvénic and super-sonic.

$n = 5$ amu/cc, $B_0 = 10$ nT with $45^o$ from the x axis, $T = 10^6$ K, $V = (-500,0,0)$ km/s, which turns to $M_A \sim 5$, $V_A \sim 100$ km/s, $\beta \sim 1.7$.

3 types of density pulses:

* density only, everything else constant
\[
\delta \rho = \rho_0 sin(\omega t) \text{for } 0 \le t \le T/2
\]
where $T = 2\pi/\omega \sim 100s$. Note that this perturbation is relatively large (max 100%).
* fast/slow mode
\begin{align}
\delta \rho = \rho_0 sin(\omega t) \\
\delta p = C_s^2 \delta\rho \\
\delta B_x = \delta B_z = 0, \delta B_y = \pm B_{y0}\delta \rho/\rho_0
\end{align}
where $C_s$ is the sound speed in the solar wind and the $+/-$ sign refers to the fast/slow type perturbation.
* density only, but stronger peak
\[
\delta \rho = 4\rho_0 exp[-(t-t_c)^8] 
\]
where $t_c$ is just an arbitrarily chosen parameter.

Interaction outcomes: fast mode --> shock, slow mode, entropy wave.

[Lee+, 2008][Lee2008]: on the role of heavy ion hybrid resonances near the equator
full wave equations for a cold plasma

### LFM

nonlinear TVD scheme switches to allow shock capturing

Boris correction is applied to the perpendicular component of the displacement current in the $\mathbf{J}\times\mathbf{B}$ force of the MHD momentum equation, but with an artifically low speed of light.

Single-fluid, ideal MHD, $\sim 0.25\, \text{R}_E$ resolution in the inner magnetosphere, upstream boundary at $x=30\, \text{R}_E$ in GSM coordinates. Fixed upstream solar wind condition ($B_x$, $V_x$), outflow on all other sides. They introduce an out-of-phase oscillation in the input sound speed time series (~ 40 km/s), so as to hold the thermal pressure constant in the upstream solar wind ($p_{th} \propto nC_S^2$). I don't quite understand this technique.

Inner boundary: 2D electrostatic model of the ionosphere, with electric potential obtained from Poisson's equation and then mapped along the dipole field lines back to the inner boundary of MHD at about $2\, \text{R}_E$. The ionospheric conductance, needed for the potential solver, is specified by an empirical extreme ultra-violet (EUV) conductance model and by a contribution from particle precipitation.

When starting the runs, they choose to flip the IMF direction multiple times which they call "precondition". Reason? Faster? Higher accuracy? Stability?

LFM model by [Claudepierre+, 2008][Claudepierre2008]:
The phase velocities of the modes were different but the frequencies were the same and depended on the solar wind driving velocity. For both modes the preferred wavenumber was related to the boundary thickness, so that the KH waves are monochromatic.

In [Claudepierre+, 2009][Claudepierre2009], LFM is used to study the magnetospheric response to only a fluctuating upstream dynamic pressure. The changing of dynamic pressure is done through changing number density while keeping bulk velocity constant.
The input dynamic pressure has frequency components spreading across Pc3 to Pc5 ranges:

| Frequency (mHz) | Relative Oscillation Amplitude (%) |
|----------|------------------|
| 5 | 20 |
| 10 | 20 |
| 18 | 30 |
| 25 | 40[^3] |
| 0-50 | 20 |

Background $\rho = 5$ amu/cc, $B = (0, 0, -5)$ nT, and $V = (-600, 0, 0)$ km/s. In Figure 1, the authors demonstrate the filtering/attenuation of the higher frequency spectral components, which is an expected artifact of the numeric solver, unfortunately. I haven't checked the shift or attenuation of frequency in Vlasiator (numerical Vlasov solver), but obviously the amplitude decreases.

Results:

1. Strong peak signal observed around 10 mHz in the continuum band input run.
2. PSD of $B_z$, $E_\phi$, the two compressional components of EM fields along the noon-meridional line, shows strong $B_z$ signals near the magnetopause.
3. They argue that the outputs represent MHD cavity modes, which in the simplest interpretation, can be thought of as standing waves in the electric and magnetic fields between a cavity inner and outer boundary. [Kivelson and Southwood, 1985]
The cavity frequency in a simple box geometry configuration with perfect conductor boundary conditions:
\[
f_n = \frac{V_A}{2a}n,\, \text{for} n = 1,2,3,...
\]
where a is the box length in x direction.

In [Claudepierre+, 2010][Claudepierre2010], they show that the monochromatic solar wind dynamic pressure fluctuations drive toroidal mode field line resonances (FLRs) on the dayside at locations wherethe upstream driving frequency matches a local field line eigenfrequency.

| Frequency (mHz) | Relative Oscillation Amplitude (%) |
|----------|------------------|
| 10 | 20 |
| 15 | 20 |
| 25 | 40[^4] |
| 0-50 | 20 |

[^4]: The larger oscillation amplitude for the input time series in the 25 mHz simulation is used to combat the effects of anumerical attenuation/filtering of higher‐frequency compo-nents in the LFM simulation.

In Figure 2 of this paper, you can clearly see the attentuation in shorter wavelengths beyond 15 mHz after propagating for 10 $\text{R}_E$.

A useful quantity called *root-integrated power (RIP)* for a given time series:
\[
RIP = [\int_{f_a}^{f_b}P(f) df]^{1/2}
\]
where $P(f)$ is the power spectral density of the given time series and the integration is carried out over a given frequency band of interest, $[f_a, f_b]$.

In this paper, the RIPs are calculated for $E_r$ and $B_\phi$ under the cyclindrical polar coordinates (which I believe are the two compressional components?).

From Alfvén speed profiles, we can compute estimates to the natural oscillation frequency for a given field line. For example, the WKB estimate to the field line eigenfrequency is given by [Radoski, 1966][^5]
\[
f_n = n[2\int_S^N \frac{ds}{v_A(s)}]^{-1} \, \text{for } n=1,2,3,...
\]
where n is the harmonic number of the FLR, s is the arc length along the field line, and the integration is carried out from the southern field line foot point (S) to the northern foot point (N). This estimate to the field line eigenfrequency is essentially the inverse of the travel time for an Alfvén wave propagating along the magnetic field line to bounce off the reflecting ionospheres and return to its starting point. It is a good approximation for the higher harmonics (large n) and predicts a value about 20% higher than the actual fundamental mode. The factor of 2 in the above equation is due to the a forementioned "bouncing" and due to the perfectly conducting ionospheric boundary condition assumed in FLR theory.

[^5]: This WKB approximation assumes dipole field, but the real magnetic field is compressed on the dayside.

Figure 3 is the most important and informative plot. In order to reproduce this kind of plot, I need:

* field tracer
* density and magnetic field along the traced field line
* conversion from Cartesian to spherical coordinates
* outputs from a time series[^6]

[^6]: In order to obtain PSD, the total simulation time shall be much larger than the enforced frequency. In MHD simulations which are relatively cheap, it is quite easy to run for hours and look at PSD of frequency in the Pc3-5 range. For Vlasov simulation, even in 2D, up until now (2021/08/16) I only have ~300s, which is only 2 periods of the enforced perturbation in density. 

In later sections there are additional discussions about polarization and energy flux (Poynting vector), but those are minor details.

###

[Wright and Allan, 2008][WrightAllan2008]:
numerical simulations of MHD wave coupling in the magnetotail waveguide that suggested 5–20 min fast mode waves generated in the magnetotail waveguide by substorms may couple to Earthward propagating Alfvén waves and produce field-aligned currents resulting in narrow auroral arcs that move equatorward at ∼1 km/s.

self-written model with no name

###

[Jordanova+, 2007][Jordanova2007] used a global ring current-atmosphere interactions model (RAM) including a time-dependent plasmasphere to determine the EMIC growth rate with time. 


###

Ray tracing calculations by Chen et al. (2009) of ICW growth 

###

McCollough et al. (2009) using a 3-D test particle solver coupled to the time-dependent MHD fields produced by the global LFM code.

###

Test-particle simulations have shown that perturbations in electric and magnetic fields are induced across wide regions of the magnetosphere by global magnetospheric compressions due to ULF variations in solar wind dynamic pressure and presumably also FLRs and
magnetosonic waves (Ukhorskiy et al. 2006).

## Techniques

### ULF Wave Detection

ULF waves are MHD waves: Alfvén wave, fast wave and slow wave. One basic approach to identify waves is to check the correlation of quantity perturbations.

The phase speed of shear Alfvén wave is

\[
v_{pA} = \frac{\omega}{k} = v_A \cos{\theta}
\]

where $v_A$ is the Alfvén speed and $\theta$ is the angle between wave vector $\mathbf{k}$ and magnetic field $\mathbf{B}$.

The perturbed quantities of Alfvén waves follow the relations

\begin{align}
\frac{\delta \mathbf{v}}{v_A} &= \pm \frac{\delta \mathbf{B}}{B_0}, \\
\delta \rho &= 0,
\end{align}

where $\delta \mathbf{v}$, $\delta \mathbf{B}$, and $\delta \rho$ are perturbed plasma velocity, magnetic fields, and plasma density, respectively, and $B_0$ is the background magnetic magnitude.

For slow and fast waves, the phase speeds are

\[
v_{p\pm}^2 = \big(\frac{\omega}{k} \big) = \frac{1}{2}(V_s^2 + V_A^2) \pm \frac{1}{2}\Big[ (V_s^2 + V_A^2)^2 - 4V_s^2 V_A^2 \cos^2{\theta}\Big]^{1/2}
\]

The "+" is for fast waves and "−" for slow waves, and $V_S$ is the sound speed. The perturbed quantities for fast and slow waves are

\begin{align}
\delta \rho &= \frac{\rho_0}{v_p}\frac{v_A^2\sin\theta}{B_0 (v_p - v_s^2/v_p)}\delta B, \\
\delta \mathbf{v} &= -\frac{v_A^2 \cos{\theta}}{B_0 v_p}\delta\mathbf{B} + \frac{v_A^2 \sin{\theta}\delta B}{B_0 (v_p - v_s^2/v_p)}\frac{\mathbf{k}}{k}.
\end{align}

Thus generally the Alfvén wave is identified by the correlations between velocity and magnetic field perturbations, and the fast and slow waves are identified by the negative (for slow waves) or positive (for fast waves) correlations between either density and magnetic field perturbation or thermal pressure and magnetic pressure perturbation.

The second equation above can also be expressed in terms of magnetic and thermal pressure pertubations

\[
\delta P_B = \frac{\mathbf{B}_0 \cdot \mathbf{B}}{\mu_0} = \frac{V_A^2}{V_S^2}\left(1-\frac{k^2 V_S^{2} \cos^2\theta}{\omega^2}\right)\delta P_t
\]

See the [lecture notes](https://farside.ph.utexas.edu/teaching/plasma/lectures1/node65.html) for more details.

For the magnetosonic waves, consider using $\delta \mathbf{E}$ and $\delta \mathbf{B}$ for identifying speed. The slopes of the curves $\delta E∕\delta B$ correspond to the wave propagation speed in the spacecraft frame.

Transverse and shear Alfvén wave refer to actually the same thing: the descriptions arise from  $\mathbf{k}\cdot\mathbf{V} = 0$ and $\mathbf{V}\cdot\mathbf{B}_0 = 0$.

The fast and slow magnetosonic waves are associated with non-zero perturbations in the plasma density and pressure, and also involve plasma motion parallel, as well as perpendicular, to the magnetic field. The latter observation suggests that the dispersion relations $\omega = kV_{\pm}$ are likely to undergo significant modification in collisionless plasmas. In order to better understand the nature of the fast and slow waves, let us consider the cold-plasma limit, which is obtained by letting the sound speed $V_S$ tend to zero. In this limit, the slow wave ceases to exist (in fact, its phase velocity tends to zero) whereas the dispersion relation for the fast wave reduces to

\[
\omega = kV_A.
\]

This can be identified as the dispersion relation for the compressional-Alfvén wave. Thus, we can identify the fast wave as the compressional-Alfvén wave modified by a non-zero plasma pressure.

In the limit $V_A\gg V_S$, which is appropriate to low-β plasmas, the dispersion relation for the slow wave reduces to

\[
\omega \simeq k\,V_S\,\cos\theta.
\]

This is actually the dispersion relation of a sound wave propagating along magnetic field-lines. Thus, in low-β plasmas the slow wave is a sound wave modified by the presence of the magnetic field.

In reality, waves can be mixed together with mode conversions. Also, notice that the classical wave theory is based on spatially homogeneous plasma assumption, which is rarely the case in nature such as the magnetosphere.

A tricky part in practice is how to get the average through smoothing. Note that a real satellite moves both in time and space. Usually people do moving-box-average to get an average state within a short period.

A more careful analysis is called Walén test.

However, always keep in mind that the most reliable way of identifying waves is to calculate the dispersion relation.

### Polarization analysis

Singular Value Decomposition (SVD): [Lee & Angelopoulos][Lee2014b]

hodogram of field components

### Mean field aligned coordinates

The magnetic field satellite data are usually referred to geocentric coordinate reference frames such as geocentric solar ecliptic (GSE) frame. Conversely, the MHD waves modes in magnetized plasma depend on the ambient magnetic field, and is then useful to rotate the magnetic field measurements into the _mean field-aligned (MFA) coordinate system_. This reference frame is useful to study the ultra-low frequency magnetic field variations along and perpendicular to the direction of the mean field. 

The MFA coordinate system is a local coordinate system that relates to the geomagnetic field. In the ecliptic plane, the parallel direction is more or less aligned with z in GSE, the first perpendicular direction pointing from Earth to the region of interest, and the second perpendicular direction completing the right hand rule. 

In order to identify the mean magnetic field the classical moving average (MAVG) approach is usually adopted, but does not always give reliable performance.
In the solarwind, a technique widely used to study parallel and perpendicular magnetic field components of waves is the minimum variance analysis (MVA). However, the minimum variance direction does not necessarily coincide with that of the ambient magnetic field.

If a time scale separation exists within the magnetic field measurements, these time series can be thought as a superposition of  a slowly varying (amplitude) ambient field $\mathbf{B}_0(t)$, an higher frequency signal $\mathbf{b}(t)$(or perturbation) and an incoherent noise $\mathbf{n}(t)$:

$$
\mathbf{B}(t) = \mathbf{B}_0(t) + \mathbf{b}(t) + \mathbf{n}(t).
$$

\fig{/assets/MFA_coordinate_magnetosphere.png}
MFA coordinate system in the magnetosphere: the MFA directions $\mathbf{\mu}$, $\mathbf{\phi}$ and $\mathbf{\nu}$ are showed together with the satellite position (red dot). The geomagnetic field line (blue line) is computed through T96 magnetosphere model [Tsyganenko 1995] during solar quiet conditions. [Regi+, 2016](Regi2016)

The MFA coordinates system, showed in the figure for an assigned position in the inner magnetosphere, is established by means of  the unit vectors defined as
\begin{align}
\mathbf{\mu}(t) = \mathbf{B}_0(t) / |\mathbf{B}_0(t)|, \\
\mathbf{\phi}(t) = \mathbf{r}(t) \times \mathbf{B}_0(t) / |\mathbf{r}(t) \times \mathbf{B}_0(t)|, \\
\mathbf{\nu}(t) = \mathbf{\mu}(t) \times \mathbf{\phi}(t),
\end{align}
where $\mathbf{\mu}$, $\mathbf{\phi}$ and $\mathbf{\nu}$ are usually associated with compressional, toroidal and poloidal ULF waves modes respectively, while $\mathbf{r}(t)$ represents the position vector of the spacecraft.

This definition may also be extended in upstream regions, but in this case the $\mathbf{\phi}, \mathbf{\nu}$ components are simply related with transverse oscillations in the interplanetary region (e.g. foreshock upstream waves).

Then we can define the instantaneous rotation matrix from geocentric to MFA reference frame as
\begin{align}
\mathbf{R}(t) = 
\begin{pmatrix}
\mu_x(t) & \mu_y(t) & \mu_z(t) \\
\phi_x(t) & \phi_y(t) & \phi_z(t) \\
\nu_x(t) & \nu_y(t) & \nu_z(t)
\end{pmatrix}
\end{align}
that allows us to project the instantaneous magnetic field vector from the original geocentric reference frame into the MFA one:
$$
\mathbf{B}^{MFA}(t) = \mathbf{R}(t)\mathbf{B}^{GSE}(t). 
$$

It is clear that in order to obtain the time series $\mathbf{B}^{MFA}(t)$ in the MFA reference system, the slowly varying mean field vector $\mathbf{B}_0(t)$ must be found through an appropriate filtering procedure. The moving average (MAVG) is a good  choice with respect to any low-pass filter, as it introduces no artifacts.
However in applying the MAVG method it is assumed that the characteristic fluctuation time $T_0$ related to $\mathbf{B}_0(t)$ is much greater than the period $T_b$ of the perturbation $\mathbf{b}(t)$. Moreover, $T_0$ depends on both satellite motion and natural magnetic field variation (e.g. high velocity stream, coronal mass ejections, corotating interaction regions), and could be related to nonlinear and non stationary phenomena.
Under these conditions the MAVG might be unsuitable in the rotation procedure, while a method such as the _empirical mode decomposition (EMD)_, is useful to identify nonlinear and nonstationary processes.

This is discussed thoroughly in [Regi+, 2016](Regi2016). I am going to write a script for implementing the ideas!

### Phase coherent technique

It is used to check the relation of one frequency oscillation to another.

### Fourier transform

It can be used for

* determining the energy spectrum density for waves in a certain range
* automated ULF wave detection algorithms.

### Wavelet transform technique

Wavelet Transform decomposes a function into a set of wavelets. A Wavelet is a wave-like oscillation that is localized in time.
Two basic properties of a wavelet are scale and location.

Key advantages of Wavelet Transform compared with Fourier Tranform:

* Wavelet transform can extract _local_ spectral and temporal information simultaneously, while FT only extract global information.
* There are various wavelets to choose from. In practice, if you have any prior knowledge to the signal you want to identify, you can find for an appropriate wavelet that is close to that shape.

A nice introduction can be found [here](https://towardsdatascience.com/the-wavelet-transform-e9cfa85d7b34).
A practical example of [R Wave Detection in the ECG](https://se.mathworks.com/help/wavelet/ug/r-wave-detection-in-the-ecg.html) using wavelet transform is given in Matlab.

For example, [Morlet/Gabor wavelet](https://en.wikipedia.org/wiki/Morlet_waveletsuper) is a wavelet composed of a complext exponential (carrier) multiplied by a Gaussian window (envelope).

### Superposed epoch analysis

A statistical tool to detect periodicities within a time sequence or to reveal a correlation in time between two time series.

1. Define each occurrence of an event in one data sequence as a key time.
2. Extract subsets of data from the other sequence within some time range near each key time.
3. Superpose all extracted subsets from series 2.

An example of sunspot analysis can be found [here](https://github.com/lkilcommons/sea_tutorial).
This sounds easy, or even too easy. I won't even consider it a standard method...


[SouthwoodKivelson1990]: http://www.igpp.ucla.edu/people/mkivelson/Publications/116-JA095iA03p02301.pdf
[Schwartz1997]: https://hal.archives-ouvertes.fr/hal-00316226/document
[Menk2011]: https://link.springer.com/chapter/10.1007/978-94-007-0501-2_13
[Claudepierre2008]: https://agupubs.onlinelibrary.wiley.com/doi/pdf/10.1029/2007JA012890
[Claudepierre2009]: https://doi.org/10.1029/2009GL039045
[Claudepierre2010]: https://doi.org/10.1029/2010JA015399
[WrightAllan2008]: https://doi.org/10.1029/2007JA012464
[GamayunovKhazanov2008]:  https://doi.org/10.1029/2008JA013494
[Lee2008]: https://doi.org/10.1029/2008JA013088
[Jordanova2007]: https://agupubs.onlinelibrary.wiley.com/doi/epdf/10.1029/2006JA012215
[Shoji2009]: (https://doi.org/10.1029/2008JA014038)
[Regi2016]: https://doi.org/10.4401/ag-7067
[Lee2014]: https://escholarship.org/uc/item/3dh4j07v
[Lee2014b]: https://doi.org/10.1002/2014JA020469
[Medeiros2020]: https://iopscience.iop.org/article/10.3847/1538-4365/ab9697