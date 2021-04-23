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
---
| Pi1      | 1 - 40           |
| Pi2      | 40 - 150         |

[^1]: The Pc5 range originates from the Mariner 5 (1967) detection limitation to a Nyquist frequency of 1.67mHz, which corresponds to 600s.

With respect to polarization, ULF waves can be categorized into three modes: poloidal ($\Delta B_r,\, \Delta E_\phi$), compressional ($\Delta B_\parallel,\, \Delta E_\phi$), and toroidal ($\Delta B_\phi,\, \Delta E_r$). Here, $B_r$ ($E_r$), $B\_parallel$, and $B_\phi$ ($E_\phi$) are the radial, parallel (or compressional), and azimuthal components in the local magnetic field system, respectively.

Theoretically, slow and fast MHD waves usually are quickly damped in collisionless plasmas with moderate to high plasma β (Barnes, 1966), leaving only outward propagating Alfven waves.

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
* periodic compressional fluctuations
* Alfvénic fluctuations

Observation: discrete magic frequencies

_Phase coherent technique_(?) is used to check the relation of one frequency oscillation to another.

The correlation between solar wind speed and ULF power in the magnetosphere suggests that the Kelvin-Helmholtz instability (KHI) resulting from the velocity shear at the magnetopause may be a significant source of ULF wave energy.

Boundary layer thickness --> over-reflection modes at the magnetopause
*Over-reflection* occurs when the characteristic scales of the wave and the inhomogeneity are comparable, and may provide an efficient process for the extraction of energy from the magnetosheath to magnetospheric waveguide modes on the flanks during fast solar wind speed intervals.
This may explain the production of discrete frequency ULF waves in the magnetosphere and statistical correlations between Pc5 power on the ground and solar wind velocity

Opinion:
Alfvénic waves propagating along the magnetopause surface may develop into standing Alfvén waves on the boundary due to reflection from the conjugate ionospheres (i.e. Kruskal-Schwarzschild modes). The surface waves are likely due to magnetopause displacements as a result of local pressure perturbations in the magnetosheath, while the eigenfrequencies of the standing modes are determined by the magnetopause geometry and are strikingly similar to the Samson ‘magic’ frequencies.
This combination of conditions suggests that the oscillations are more likely due to Kruskal-Schwarzshild modes than solar wind pressure perturbations or the KHI at the flanks.

Within the magnetosphere, there are two possible mechanics:
* drift-mirror instabilities (?) due to high $\beta$ pressure anisotropies
* drift-bounce resonance (?) with trapped energetic ions

strongly compressional, high azimuthal wave number m, attenuated on the ground.

## Physics

Margy has done a lot in this field.

### Wave Generation and Propagation Mechanisms

The propagation of magnetospheric ULF plasma waves has been described usually usually in the context of standing shear Alfvén mode field line oscillations with low azimuthal wavenumber that are driven by energy coupling from incoming compressional fast mode waves.

global eigenoscillations of the magnetosphere or the plasmasphere

In fact, the coupling of cavity or waveguide eigenmodes to FLRs may explain how discrete spectra are produced across a range of latitudes, including at the "magic" frequencies.

The global cavity modes _may be_ responsible for the appearance of ULF signals with multiple discrete spectral peaks at the "magic"
frequencies and spanning a range of latitudes, but it lacks observation support and is hard to detect with satellites. (This is interesting!)

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

automated ULF wave detection algorithms using FFT
wavelet transform technique(?)


## Simulations

### LFM

LFM model by [Claudepierre+, 2008][Claudepierre2008]:
The phase velocities of the modes were different but the frequencies were the same and depended on the solar wind driving velocity. For both modes the preferred wavenumber was related to the boundary thickness, so that the KH waves are monochromatic.

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

[Menk2011]: https://link.springer.com/chapter/10.1007/978-94-007-0501-2_13
[Claudepierre2008]: https://agupubs.onlinelibrary.wiley.com/doi/pdf/10.1029/2007JA012890
[WrightAllan2008]: https://doi.org/10.1029/2007JA012464
[GamayunovKhazanov2008]:  https://doi.org/10.1029/2008JA013494
[Lee2008]: https://doi.org/10.1029/2008JA013088
[Jordanova2007]: https://agupubs.onlinelibrary.wiley.com/doi/epdf/10.1029/2006JA012215
