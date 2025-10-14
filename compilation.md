@def title = "Compilation on Ubuntu"
@def hascode = false
@def rss = ""
@def rss_title = "Compilation"
@def rss_pubdate = Date(2024, 9, 16)
@def tags = ["syntax", "image"]


# How to compile the SWMF model

## SWMF

### Pre-requisites

- Start by updating the packages list:

```shell
sudo apt update
```

- Install the build-essential package by typing:

```shell
sudo apt install build-essential
```

The command installs a bunch of new packages including `gcc`, `g++` and `make`.

- To validate that the GCC compiler is successfully installed, use the `gcc --version` command which prints the GCC version:

```shell
gcc --version
```

Then we need an MPI support. We choose OpenMPI:

```shell
sudo apt-get update && sudo apt-get install infiniband-diags ibverbs-utils \
     libibverbs-dev libfabric1 libfabric-dev libpsm2-dev -y
sudo apt-get install openmpi-bin openmpi-common libopenmpi-dev libgtk2.0-dev
sudo apt-get install librdmacm-dev libpsm2-dev
```

The command installs a bunch of new programs including `mpiexec`, `mpif90`, and `mpicxx`.

### Downloading

The source code locates at: `https://github.com/SWMFsoftware/SWMF`

To download the code, we choose to clone through SSH:

```shell
git clone git@github.com:SWMFsoftware/SWMF.git
```

If you use HTTPS, you will encounter errors during installation. SSH connection requires setup in the terminal. Checkout this [GitHub post](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

### Compilation

```shell
./Config.pl
```

```shell
./Config.pl -install
```

Checkout the usage of `Config.pl` for switching compilers etc.

On Perlmutter, we need to manually add `-pthread` to the linking stage. Identify the following line in `Makefile.conf`:

```make
LINK.f90         = ${CUSTOMPATH_MPI}mpif90
```

Append `-pthread` to the end:

```make
LINK.f90         = ${CUSTOMPATH_MPI}mpif90 -pthread
```

### Testing

```shell
make -j test16_2d
```

## BATSRUS

```shell
git clone git@github.com:SWMFsoftware/BATSRUS.git
cd BATSRUS
./Config.pl -install
```

Here we try a simple KHI demo on Perlmutter.

```shell
/Config.pl -e=Hd -g=8,8,1 -u=KelvinHelmholtz
make -j
make PIDL
make rundir
cp Param/SHOCKTUBE/PARAM.in.kelvin_helmholtz run/PARAM.in
```

```shell
mv run ~/scratch # move the run folder to your workspace
```

Next we ask for an interactive job:
```shell
salloc --nodes 1 --qos interactive --time 00:10:00 --constraint cpu
```

After entering the interactive job, we go to the copied run directory.

```shell
srun -n 1 ./BATSRUS.exe | tee runlog
```

Then we postprocess the data into a new folder:

```shell
./PostProc RESULT/run1
```

The actual data is stored under `RESULT/run1/GM/`.
For plotting with Python, checkout flekspy demos [here](https://henry2004y.github.io/flekspy/idl_data.html).

```shell
import flekspy as fs
import matplotlib.pyplot as plt

file = 'z=0_hd_1_t00000320_n00001016.out'
ds = fs.load(file)
ds.Rho.plot.pcolormesh(x="x", y="y")

plt.savefig("test.png")
```
