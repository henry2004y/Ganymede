@def title = "Extra"

# Extra


## Practical Issues

For quite a long time the problem I encounter is the off-set of the magnetopause position. Mine is larger than what's observed by Galileo at dayside magnetopause.

One of the issue I have right now is the unknown expansion of magnetosphere when I switch from Hall MHD to MHD-EPIC. This just shows the discrepancies between the models.

I made one mistake after another.

### Boundary values

This time, when I tried to use `#BOUNDARYSTATE` command, the initial guess is overwritten by the values I set. Previously it was set to be the solarwind condition. Obviously this is a problem, as you can see from the local timestep run of G2 flyby that the solution never converges but shows a periodic behavior. Mathematically, it is not guaranteed for the nonlinear system that the steady state is unique given the same boundary condition; let along in your case the inner boundary condition is modified to 0 $\mathbf{B}_1$ magnetic field.

It is very easy to forget turning on of the `#INCLUDE` command for restart runs.

### Order of schemes

I find that `nStage` and `nOrder` are related.

### Code performance

As a rough estimation, 2000 cores, 300s with one PIC region will require 1 day to run.

`DtCouple` controls how often GM and PC synchronize. It may effect the code's efficiency if you set it too small, or leads to inaccurate solution if you set it too large.

### Effect of grid resolution

I did a high PIC grid resolution run ($1/64R_G$) and a high particle density run ($8*8*8$) and compared the results with time-accurate Hall MHD. I still got the expansion, an increase of pressure inside the magnetosphere near the dayside reconnection region and a similar but slightly different density at the front.

So my initial conclusion is that increasing grid resolution helps to suppress the nonphysical oscillations at the upstream side, while I cannot tell the qualitative difference of all the other quantities.

### Coarse axis

`#COARSERAXIS` is applied for mediating the polar grid issue.

### Update check

The MHD part of my MHD-EPIC run still has an update check. Turn it off in time accurate runs for the sake of speed. However, this shouldn't have any effect on the face BC solution. The command that is useful is the coarse axis of fix axis one that relax the timestep at the polar region.

### Coordinate system

I found an error in the boundary-normal coordinates I used in plotting FTE. I should use right-hand rule to define my three main axis, but instead I used a left-hand system.

### Energy-conserving parameter

Using $\theta=0.51$ for the MHD-EPIC runs gives better electric field compared to $\theta=0.50$ cases. $\theta=0.5$ means exact energy conserving, but in practice this may not be the best option.

## PIC Analysis

Gabor has some function in IDL for transforming $P_{xx},P_{yy},P_{zz}$ to the local magnetic coordinate system.

## Visualizations

Yuxi told me a way to visualize FTEs. First, in practice we usually use $B_z=0$ to define magnetopause. We can trace along x axis and find the first cells satisfy $B_z=0$; then we project these cells onto the same plane and plot their other quantities to see if the pressure, density and other quantities are characteristic of FTE.
I think there are many problems with this method.
Also, he told me that the reconnection rate is often described with some kind of electric field.

Thinking about the 3D scenario: when I look at $y=0$ cut, it is only a cut. Because of the nonzero $B_y$ component in the upstream condition, the nose point of reconnection and related FTE is probably shifted!
The usual way I check FTEs are by looking at the cut contour plots. It is possible to miss some of the flux ropes.

Suddenly realize that the box output may be inaccurate. The resolution is $1/32 R_G$, but the actual grid resolution at the magnetopause (which I need to check today) is smaller than this. This means that the discontinuity is probably smoothed out at the magneopause. One option is to design a new grid with higher resolution at the magnetopause position.

Right now my grid resolution at $r=2$ in $\widehat{r}$ is about $0.05R_G$ in $z=0$ plane, and the resolution along the Galileo trajectory is about $0.06R_G$. The sharp increase of $B_z$ happens from $(-1.48,-1.13,0.728)$ to $(-1.452,-0.549,0.743)$ (about $0.582R_G$). In computing grid this covers about $10$ cells.

## Ghost cell filling

The problem with box, shell and tcp plots: because of interpolation of non-primitive variables (e.g. $j_x,phi_1$) and the missing of their ghost cell information, we can clearly see gaps in contour plot indicating the boundaries of blocks.

The fix for this is message passing after plotvar has been filled: instead of one stage, we do two stages: in the first stage, we set the plot variables and do message passing if needed; in the second stage, we will have already received the ghost cell values, and then we do the interpolation and write to files.


## Miscellaneous

**Example**:

Kalman filter is used when:
1. The variable of interest can only be measured indirectly.
2. Measurements are available from various sensors but might be subject to the presence of noise. (e.g. IMU, odometer and GPS for estimation of exact position)

State observer used as a feedback to measure the wanted variables indirectly.
