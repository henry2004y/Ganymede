@def title = "Run in Action"
@def hascode = false
@def rss = ""
@def rss_title = "How to run the model"
@def rss_pubdate = Date(2021, 3, 17)
@def tags = ["syntax", "image"]

# How to run the SWMF model

Even though I have been working with SWMF for five years, I will forget how to use it after leaving it for a while or the latest development introduce some breaking changes to the setups.
This manual serves as a reference for myself and also other interesting researchers on how to reproduce the simulation.

The installation is thoroughly described in the official document. The following assumes you have a basic understanding of running a model in SWMF.

In principle, the GM module can run alone without compiling the PC module until the coupling is required.
However in practice I recommend run with the coupled executable from start to prevent further work in changing the parameter file at a later stage.

After SWMF is successfully installed, 
```
./Config.pl -v=Empty,PC/FLEKS,GM/BATSRUS -amrex
./Config.pl -o=GM:g=8,8,8,ng=2,u=Ganymede,e=MhdHypPe
```

If the syntaxes change in the future, you can check how it is configured in `Makefile.test`.

The run can be split into multiple stages:
* steady state ideal MHD
* quasi-steady state Hall MHD
* time-accurate (time-dependent) Hall MHD
* time-accurate (time-dependent) MHD-EPIC

It is not necessary to strictly follow this order: we do this only to speed things up assuming that the same solution will be reached given the same initial and boundary condition, no matter which timestepping mode or which numerical model is chosen in the intermediate stages.
The validity of this statement is hard to prove mathematically, but based on practical experience it generally works pretty well.

## Steady State Ideal MHD

```
Name     Root Last Stride
#LAYOUT
GM       0    99999   1
PC       0    99999   1

#PLANET
Ganymede                NamePlanet
2634000                 RadiusPlanet [m]
1.4819E+23              MassPlanet   [kg]
0.0                     OmegaPlanet  [radian/s]
0.0                     TiltRotation [degree]
DIPOLE                  TypeBField
4.                      MagAxisThetaGeo [degree]
291.05                  MagAxisPhiGeo   [degree]
-718.55E-9              DipoleStrength  [T]

#ROTATION
F                       UseRotation

#TIMEACCURATE
F                       DoTimeAccurate

#SAVERESTART
T                       DoSaveRestart
2000                    DnSaveRestart
-1.0                    DtSaveRestart


! Restart header for SWMF
INCLUDE
RESTART.in              NameRestartFile

#CPUTIMEMAX
20000.0                 CpuTimeMax

#CHECKSTOP
T                       DoCheckStop
1000                    DnCheckStop
-1.0                    DtCheckStop

#PROGRESS
200                     DnShowProgressShort
2000                    DnShowProgressLong

#COMPONENT
PC                      NameComp
F                       UseComp

#BEGIN_COMP GM ---------------------------------------------------------------

! Restart header for GM
INCLUDE
GM/restartIN/restart.H

#HYPERBOLICDIVB
T                       UseHyperbolicDivb
150.0                   SpeedHypDim
0.1                     HypDecay

#COORDSYSTEM
GSE                     TypeCoordinate

#BODY
T                       UseBody
0.5                     rBody      [rPlanet]
3.5                     rCurrents  [rPlanet]
39                      BodyNDim   [/cc]
2.32e5                  BodyTDim   [K]

#BODY
F

#PLASMA
14.0                    FluidMass [amu]
1.0                     AverageIonCharge [e]
1.0/18.0                ElectronTemperatureRatio

#SEMIKRYLOV
GMRES                   TypeKrylov  (GMRES, BICGSTAB, CG)
0.001                   ErrorMaxKrylov
100                     MaxMatvecKrylov

#MINIMUMPRESSURE
0.001                   pMinDim
0.001                   PeMinDim for electron pressure

#MINIMUMDENSITY
0.1                     RhoMinDim

#NONCONSERVATIVE
F                       UseNonConservative

#CONSERVATIVECRITERIA
0                       nConservCrit

#RESTARTOUTFILE
one                     TypeRestartOutFile

---------------grid structure-----------------
#GRIDGEOMETRY
spherical_lnr           TypeGeometry

#GRIDBLOCKALL
56000

#GRID
10                       nRootBlockX
8                        nRootBlockY
8                        nRootBlockZ
-100                     xMin
 100                     xMax
-100                     yMin
 100                     yMax
-100                     zMin
 100                     zMax

#LIMITRADIUS
0.5                     rMin
174.0                   rMax > (sqrt(100^2+100^2+100^2))

#GRIDLEVEL
3                       nLevelArea
initial                 NameArea

#GRIDLEVEL
3                       nLevelArea
box_gen                 TypeRegion
1.1                     rmin            xMinBox
0.0                     LonMin          yMinBox
-65.0                   LatMin          zMinBox
3.0                     rmax            xMaxBox
360.0                   LonMax          yMaxBox
65.0                    LatMax          zMaxBox

#GRIDLEVEL
1                       nLevelArea
box_gen                 TypeRegion
5.0                     rmin
-70.0                   LonMin
35.0                    LatMin
15.0                    rmax
70.0                    LonMax
65.0                    Latmax

#GRIDLEVEL
1                       nLevelArea
box_gen                 TypeRegion
5.0                     rmin
-70.0                   LonMin
-35.0                   LatMin
15.0                    rmax
70.0                    LonMax
-65.0                   LatMax
----------------end grid structure--------------

----------------BC-----------------
#OUTERBOUNDARY
fixedb1                 TypeCellBc1
none                    TypeCellBc2
periodic                TypeCellBc3
periodic                TypeCellBc4
periodic                TypeCellBc5
periodic                TypeCellBc6

#BOXBOUNDARY
fixed                   TypeBcXmin
fixed                   TypeBcXmax
float                   TypeBcYmin
float                   TypeBcYmax
float                   TypeBcZmin
float                   TypeBcZmax

#BOUNDARYSTATE
coord1max xminbox xmaxbox         StringBoundary
56.0                    BoundaryStateDim_V Rho
140.0                   BoundaryStateDim_V Ux
0.0                     BoundaryStateDim_V Uy
0.0                     BoundaryStateDim_V Uz
-10.0                   BoundaryStateDim_V Bx
-6.0                    BoundaryStateDim_V By
-86.0                   BoundaryStateDim_V Bz
0.0                     BoundaryStateDim_V Hyp
0.2                     BoundaryStateDim_V Pe
3.6                     BoundaryStateDim_V p

#SOLIDSTATE
T                       UseSolidState
user                    TypeBcSolid
sphere                  TypeSolidGeometry
1.0                     rSolid
5e-3                    SolidLimitDt

-------------end BC--------------

#RESISTIVITY
T                       UseResistivity
user                    TypeResistivity
0.0                     Eta0Si

#USERSWITCH
+init +ic +source       StringSwitch

#USERINPUTBEGIN --------------------

#INITTYPE
B1U1

#RESISTIVEPLANET
5                       nResistivePoints
1.05                    Radius
0.0                     Resistivity
0.95                    Radius
6e11                    Resistivity
0.7                     Radius
6e11                    Resistivity
0.65                    Radius
6e9                     Resistivity
0.55                    Radius
0.0                     Resistivity

#MASSLOADING
8.0e6                   NeutralDensity (cm^-3)
250                     ScaleHeight (km)
2.2e-8                  IonizationRate (1/s)
2e-15                   CollisionCrossSection (cm2)

#SOLIDBOUNDARY
3

#USERINPUTEND ----------------------

#TIMESTEPPING
2                       nStage
0.8                     CflExlp

#SCHEME
2                       nOrder (1 or 2)
Sokolov                 TypeFlux (Roe, Rusanov, Linde, Sokolov)
mc3                     TypeLimiter
1.2                     LimiterBeta

#SEMIIMPLICIT
T                       UseSemiImplicit
resistivity             TypeSemiImplicit

#COARSEAXIS
T
1

#SAVEINITIAL
F

#SAVELOGFILE
T                       DoSaveLogfile
RAW                     StringLogfile
1                       DnSaveLogfile
-1.                     DtSaveLogfile

#SAVETECBINARY
T                       DoSaveTecBinary

#SAVEPLOT
3                       nPlotFiles
y=0 VAR idl             StringPlot
5000                    DnSavePlot
-1.                     DtSavePlot
-1.                     Dx
{MHD} b1x b1y b1z divb eta              NameVars
box VAR idl             StringPlot
10000                   DnSavePlot
-1.                     DtSavePlot
GSE                     TypeCoord
-1.29                   x0
0.74                    y0
0.7225                  z0
0.57                    xLen
1/32                    dX
8.832                   yLen
1/32                    dY
0.147                   zLen
1/32                    dZ
0.                      xAngle
0.                      yAngle
0.                      zAngle
bx by bz                NameVars
{default}               NamePars
3d MHD tcp              StringPlot
50000                   DnSavePlot
-1.0                    DxSavePlot

#END_COMP GM --------------------------------------------------------------

#STOP
30000                   MaxIteration
-1.0
```

There are several things worth noticing here:
* Since `DoTimeAccurate = F`, all the corresponding time check parameters must switch to `Dn` but not `Dt`, i.e. parameters with `Dt` prefix must be negative and parameters with `Dn` prefix must be positive integers. This affects the restart control commands `SAVERESTART`,`CHECKSTOP` as well as output command `SAVEPLOT`.
* `CPUTIMEMAX` and `CHECKSTOP` together controls the running time, and may cause the simulation to stop gracefully before the time you request in a job.
* The `BODY` command is first turned on and then off to set the `rBody`. It will be recorded as a parameter in the output file that may be useful for plotting, but it won't affect anything in the simulation.
* The `PLASMA` command sets the average mass for the single fluid model, and the initial electron-ion temerature ratio that may change later as a function of time.
* The `SEMIKRYLOV` command sets the parameters for the semi-implicit solver. There is a similar command `KRYLOV` with identical input arguments for setting parameters for the full implicit solver.
* `MINIMUMPRESSURE` and `MINIMUMDENSITY` are used to avoid small discrete timesteps, which is a common trick in MHD and hybrid models. Physically, if the plasma density goes really low, the fluid description may fail to accurately represent the charged particles, which is my explanation of justifying these seemingly arbitrary thresholds. Having one uniform model to describe phenonemon across a wide range of scales is an impossible mission.
* Conservative vs. non-Conservative scheme: the former may be better at resolving shocks and discontinuities, as it follows the same path as the classical RH relation. This is not a critical factor.

* The `GRIDBLOCKALL` is a useful command for specifying the total number of blocks in the simulation for preallocating memory on each MPI process. There is a default value but it may just waste memory for your grid setup. Unfortunately it is not practical to know the total number of blocks before you run the model. What I usually do is first run the model once to get the total number of block counts, and then set this number slightly larger than that accordingly.
* The `GRIDLEVEL` command is used for setting AMR. One important control factor lies in the `initial` NameArea: the number listed here is the maximum level of AMR you can get, no matter what you specify later in each TypeRegion.

* It takes time for one to get used to the boundary settings. The official document of BATSRUS or `PARAM.XML` provides a detailed description of how these commands work together.
* The `SOLIDSTATE` command is a trick to solve only the magnetic diffusion-like equation in the mantle region. It looks pretty ugly in the code, so it is likely that this fragile part will potentially break in the future. Here in the steady state run, the useful parameter is `SolidLimitDt`, which provides a fixed timestep for the mantle cells for updating the magnetic field. The value listed here is only from experience, which tries to be close to the timestep in the MHD domain cell with 2 levels of refinement as prescribed with the above AMR settings right next to the surface. In the time dependent run, this parameter doesn't have an effect.

* In the `RESISTIVITY` command, we specify the `user` type resistivity, which is implemented in `user_set_resistivity`.

* There are several customized input arguments specified in `ModUserGanymede`.
  * `INITTYPE` gives the initial settings for B and U;
  * `RESISTIVEPLANET` sets a fixed resistivity profile as a function of planet radius;
  * `MASSLOADING` sets the parameters related to the ionospheric inner boundary I was testing before AGU2020. Details can be found in other pages;
  * `SOLIDBOUNDARY` sets the B, U, P values at the moon's surface. Definitely I cannot tell what 3 means even I wrote it myself...

* `COARSEAXIS` may help to overcome the tiny timestep issue at the polar cells. 1 means merge 2 cells into 1 in terms of updating.
* `SAVEINITIAL` determines whether or not to output at the beginning of the run. I set to false often because during restarts we don't need to save the same snapshot once again.
* In the `SAVEPLOT` command, several things may go wrong:
  * The first number, `nPlotFiles`, specifies how many output files there will be. It happens many time that I write a number smaller than the actual number of outputs I list afterwards so that some files are missing.
  * The box output is what I used to plot the G8 magnetic field comparisons. Saving it within a box has the advantage of shifting it slightly to get potentially better comparison. However, I think this is no longer necessary, so the `SATELLITEFILE` command may be a better substitution.


## Steady State Hall MHD

It is allowed to have multiple sessions in one PARAM.in file, separated with the `#RUN` command.
After the local timestepping ideal MHD is finished, what I would do is to create another input file with the following added to the end to the previous PARAM.in: 
```
#STOP
1                       MaxIteration
-1.0                    tSimulationMax

#RUN

#BEGIN_COMP GM ------------------------------------------------------------

#HALLRESISTIVITY
T                       UseHallResist (rest of parameters read only if true)
1.0                     HallFactorMax
0.1                     HallCmaxFactor

#HALLREGION
+hallbox -hallsphere -polars
0

#REGION
hallbox                 NameRegion
box tapered             NameHallRegion
-4                      xMinBox
-4                      yMinBox
-4                      zMinBox
4                       xMaxBox
4                       yMaxBox
4                       zMaxBox
0.5                     Taper

#REGION
hallsphere              NameRegion
sphere0 tapered         StringShape
1.05                    Radius
0.05                    Taper

#REGION
polars                  NameRegion
doubleconez0 tapered    StringShape
12                      Height
2.0                     Radius
0.2                     Taper

#END_COMP GM --------------------------------------------------------------

#STOP
30000                   MaxIteration
-1.0                    tSimulationMax
```

Also, remember to turn on the two `INCLUDE` commands, one for obtaining the restart files for SWMF, the other for GM.

* A `STOP` command is required at the end of the ideal MHD session due to an unknown bug related to restart in Hall MHD local timestepping mode. Hopefully someone will solve this in the future.
* Usually 30000 steps is more than enough for the transition.

To link the restart files,
```shell
./Restart.pl
```
if you haven't postprocessed the previous run into another folder.
If you have already done `./PostProc.pl RESULT/run_ideal`, then instead
```shell
./Restart.pl -i RESULT/run_ideal
```

## Time-accurate Hall MHD

Just change all the forementioned `Dn`, `Dt` parameters together with `TIMEACCURATE`.

## time-accurate MHD-EPIC

There are a bunch of new commands for coupling with PIC.