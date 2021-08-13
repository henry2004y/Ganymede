@def title = "ULF Waves"
@def hascode = false
@def rss = ""
@def rss_title = "Review and research of ULF waves"
@def rss_pubdate = Date(2020, 11, 8)

# ULF Waves

[Menk, 2011][Menk2011]的综述文章只能硬着头皮看。太多从文章中抄出来的经验性总结了。

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

Theoretically, slow and fast MHD waves usually are quickly damped in collisionless plasmas with moderate to high plasma β (Barnes, 1966), leaving only outward propagating Alfvén waves.

2 types of origins:
* solar wind
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

strongly compressional, high azimuthal wave number m, attenuated on the ground.

## Physics

[^2]: Margy has done a lot in this field.

### Wave Generation and Propagation Mechanisms

One kind of wave types that I am not so familar with is called entropy wave. It is a comparessional wave (i.e., fluctuations in pressure and density) that can be either hydrodynamic or magnetohydrodynamic in which the internal energy and velocity remains constant.

anisotropy conditions

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

Electromagnetic Ion-Cyclotron Waves (EMICWs)

The waves are generally believed to be generated in the equatorial magnetosphere by ion-cyclotron resonance with unstable distributions of energetic ring current ions during the recovery phase of magnetic storms. The characteristic fine structure appearance of ‘pearl’
Pc1 waves was attributed to dispersive field-aligned wave packet propagation in the LH ion mode on successive bounces between hemispheres.
However, this still lacks observation support.
Spacecraft measurements have shown that EMICW propagation is almost exclusively away from the equator at latitudes greater than about
11◦, with minimal reflection at the ionosphere.

The MHD wave equations that describe the coupling between the fast compressional mode and the shear Alfvén mode are complicated and have not been completely solved analytically, even in a simple dipole geometry.

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
| 25 | 40[^3] |
| 0-50 | 20 |

[^3]: The larger oscillation amplitude for the input time series in the 25 mHz simulation is used to combat the effects of anumerical attenuation/filtering of higher‐frequency compo-nents in the LFM simulation.

In Figure 2 of this paper, you can clearly see the attentuation in shorter wavelengths beyond 15 mHz after propagating for 10 $\text{R}_E$.

A useful quantity called \emph{root-integrated power (RIP)} for a given time series:
\[
RIP = [\int_{f_a}^{f_b}P(f) df]^{1/2}
\]
where $P(f)$ is the power spectral density of the given time series and the integration is carried out over a given frequency band of interest, $[f_a, f_b]$.

In this paper, the RIPs are calculated for $E_r$ and $B_\phi$ under the cyclindrical polar coordinates (which I believe are the two compressional components?).

From Alfvén speed profiles, we can compute estimates to the natural oscillation frequency for a given field line. For example, the WKB estimate to the field line eigenfrequency is given by [Radoski, 1966][^4]
\[
f_n = n[2\int_S^N \frac{ds}{v_A(s)}]^{-1} \, \text{for } n=1,2,3,...
\]
where n is the harmonic number of the FLR, s is the arc length along the field line, and the integration is carried out from the southern field line foot point (S) to the northern foot point (N). This estimate to the field line eigenfrequency is essentially the inverse of the travel time for an Alfvén wave propagating along the magnetic field line to bounce off the reflecting ionospheres and return to its starting point. It is a good approximation for the higher harmonics (large n) and predicts a value about 20% higher than the actual fundamental mode. The factor of 2 in the above equation is due to the a forementioned "bouncing" and due to the perfectly conducting ionospheric boundary condition assumed in FLR theory.

[^4]: This WKB approximation assumes dipole field, but the real magnetic field is compressed on the dayside.

Figure 3 is the most important and informative plot. In order to reproduce this kind of plot, I need:
* field tracer
* density and magnetic field along the traced field line
* conversion from Cartesian to spherical coordinates

In later sections there are additional discussions about polarization and energy flux (Poynting vector), but those are minor details.

###

[Wright and Allan, 2008][WrightAllan2008]:
numerical simulations of MHD wave coupling in the magnetotail waveguide that suggested 5–20 min fast mode waves generated in the magnetotail waveguide by substorms may couple to Earthward propagating Alfvén waves and produce field-aligned currents resulting in narrow auroral arcs that move equatorward at ∼1 km/s.

self-written model with no name

###

Recent modeling efforts have focused on clarifying the locations and conditions for EMICW generation, including the effect of heavy ion populations, and explaining the modulated appearance of wave packets. However, there is no clear consensus on a dominant mechanism.
These are important questions since EMIC waves may control the precipitation of energetic ions and relativistic electrons.

Plasma density is one of the most important parameters controlling EMIC wave generation. Growth models which assume the total plasma is dominated by thermal plasma may not relate to regions where both cold plasmaspheric plasma and ring current ions are important.

[Gamayunov and Khazanov, 2008][GamayunovKhazanov2008] using a global RCEMIC simulation model suggests that suprathermal plasma plays a role in destabilizing the more energetic ring current and/or plasma sheet distributions to a high energy anisotropy.
It also suggests that for best data comparison the EMICW source is located at the equator and that waves reflect at off-equatorial latitudes at the bi-ion hybrid frequencies in conjugate hemispheres.

self-written model, no name, ray-tracing equations in plasma

###

[Lee+, 2008][Lee2008]: on the role of heavy ion hybrid resonances near the equator
full wave equations for a cold plasma

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
[Menk2011]: https://link.springer.com/chapter/10.1007/978-94-007-0501-2_13
[Claudepierre2008]: https://agupubs.onlinelibrary.wiley.com/doi/pdf/10.1029/2007JA012890
[Claudepierre2009]: https://doi.org/10.1029/2009GL039045
[Claudepierre2010]: https://doi.org/10.1029/2010JA015399
[WrightAllan2008]: https://doi.org/10.1029/2007JA012464
[GamayunovKhazanov2008]:  https://doi.org/10.1029/2008JA013494
[Lee2008]: https://doi.org/10.1029/2008JA013088
[Jordanova2007]: https://agupubs.onlinelibrary.wiley.com/doi/epdf/10.1029/2006JA012215
[Regi2016]: https://doi.org/10.4401/ag-7067
