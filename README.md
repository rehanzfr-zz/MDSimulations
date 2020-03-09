# MD Simulations

This repository contains all the necessary information for running MD Simulations

# Installation of GROMACS

Here are the codes which can be given one after the other to install the latext version of [GROMACS](http://www.gromacs.org/) on any computer. The link to the related video is at the following link:

[https://www.youtube.com/watch?v=kA3SmMnphmI](https://www.youtube.com/watch?v=kA3SmMnphmI)

First of all open the terminal and issue the following command to update the system.

```bash
sudo apt-get update
```

After the completion of update, issue following command:

```bash
sudo apt-get upgrade
```

Now, we have to check that whether we have already installed `cmake` in our system. For this, we will check the version of the `cmake`.

```bash
cmake -version
```

Next, if we cannot see the version of `cmake`, then issue following command to install it.

```bash
sudo apt-get install cmake
```

Now, some other libraries for building the package are also required, which can be installed using this command in the terminal. Press `Y` when will be required.

```bash
sudo apt-get install swig
sudo apt-get install libboost-all-dev
sudo apt-get install cmake-data
sudo apt-get install liblog4cpp5-dev
sudo apt-get install libitpp-dev
sudo apt-get install libcppunit-dev
sudo apt-get install gnuradio-dev
sudo apt-get install build-essential
```

Now go to the `Downloads` folder. The following command will only work if you are in home.

```bash
cd Downloads/
```

Make a new directory over there in `Downloads` folder and name it `GromacsDownload`.

```bash
mkdir GromacsDownload
```

Change directory to `GromacsDownload` by issuing the following command.

```bash
cd GromacsDownload/
```

In this directory, you have to download two files from [http://manual.gromacs.org/documentation/2020/download.html](http://manual.gromacs.org/documentation/2020/download.html). For this, we can use `wget`.

```bash
wget http://gerrit.gromacs.org/download/regressiontests-2020.tar.gz
wget ftp://ftp.gromacs.org/pub/gromacs/gromacs-2020.tar.gz
```

Now we will issue following commands one by one to unzip/untar the compressed downloaded files in the same direcotry.

```bash
tar xvzf regressiontests-2020.tar.gz
tar xvzf gromacs-2020.tar.gz
```

After this, we have to install the FFTW on our system.

```bash
sudo apt-get install libfftw3-dev
```

Now, change your directory to `gromacs-2020` which was earlier uncompressed.

```bash
cd gromacs-2020/
```

Here, we will make a new directory with the name `build`.

```bash
mkdir build
```

change your directory to `build`.

```bash
cd build/
```

Now, issue this long command.

```bash
sudo cmake .. -DGMX_BUILD_OWN_FFTW=OFF -DREGRESSIONTEST_DOWNLOAD=OFF -DCMAKE_C_COMPILER=gcc -DREGRESSIONTEST_PATH=/home/rehan/Downloads/GromacsDownload/regressiontests-2020
```

Now issue this command.

```bash
sudo make check
```

Now install the gromacs using following command.

```bash
sudo make install
```

You have finally installed GROMACS, issue following command to source it. Without this command, you cannot call `gmx` directly in the terminal easily. Moreover, you want to use gromacs any time after restrating your computer. Please issue the same command before using `gmx`, otherwise, gmx will not be available.

```bash
source /usr/local/gromacs/bin/GMXRC
```

You can check the version and installation of gromacs by issuing the following command.

```bash
gmx pdb2gmx --version
```

> Note: Clerical mistakes are expected. Please suggest any changes in this document.
