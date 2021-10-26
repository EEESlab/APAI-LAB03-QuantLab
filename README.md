# APAI-LAB03: QuantLab


## Prerequisite for the APAI Virtual Machine users: increase VM storage

To install QuantLab and `quantlib` on the APAI VM, you will first need to increase its storage.
This guide is written in the hypothesis that you are using VirtualBox to run your VM.

### Increase the size of the VM's storage peripheral

* Execute VirtualBox, but do not boot the APAI VM.
* Enter the `File` menu from VirtualBox's menu bar, and select the `Virtual Media Manager` option.
* In the newly-opened window, select the `pulp_box_2021_dory-disk1.vdi` item (i.e., the APAI VM image) and use the slider to increase its size from 20GB to 32GB; we found that 32GB are sufficient to run the exercise.
* Confirm the change by clicking the `Apply` button, then `Close` the window.

An alternative using the command line can be found [here](https://askubuntu.com/a/88651).

### Restructure the formatting of the VM's storage

* Boot the APAI VM.
* Once you have entered the user session on the VM, open a terminal emulator and install GParted by issuing `sudo apt install gparted`.
* Open the start menu and look for `GParted` using the search bar; execute the program.
* Select the `swap` partition and right-click on it; switch off memory swapping by selecting `Swapoff`.
* Select the `extended` partition and right-click on it; select `Resize` and move its right edge to the extreme right edge of the depicted VM storage peripheral.
* Select the `swap` partition and right-click on it; select `Move` and drag it to the right-most edge of the enclosing partition.
* Select the `extended` partition and right-click on it; select `Resize` and shrink it by moving its left edge as far right as you can.
* Select the `swap` partition and right-click on it; switch on memory swapping by selecting `Swapon`.
* Select the `ext4` partition and right-click on it; select `Resize` and move its right edge as far right as you can.
* Enter the `Edit` menu from GParted's menu bar and select `Apply All Operations`.

More information [here](https://askubuntu.com/a/802336).


## Install Miniconda

Anaconda is a distribution of the Python and R programming languages.
Anaconda collects many versions of the language interpreters and numerous packages, and enables the creation of self-contained virtual environments that avoid version conflicts and facilitate experiment replication.
Therefore, Anaconda is particularly useful for scientific computing.

When you install Anaconda on your machine, it creates a local index containing many commonly-used packages.
Therefore, it has considerable storage requirements, a fact that might not be desirable if you plan to save storage.
For this reason, the creators of Anaconda developed a lightweight version of the distribution called Miniconda.
Miniconda's local index is minimal: most of the packages that you will need to create your environments will be downloaded following a lazy policy, i.e., just when you will need them.

To install Miniconda, you need to take the following steps:
* download the installer for your OS from the [Miniconda installation page](https://docs.conda.io/en/latest/miniconda.html); we suggest that you follow the good practice of computing its digital siganture and comparing it with the one reported on the website; for example, on Linux you would run ```shasum -a 256 ~/Downloads/[installer_file]``` (supposing that you downloaded the installer to the `~/Downloads` folder);
* execute the installer; for example, in a session of the BASH interpreter you would execute ```bash ~/Downloads/[installer_file]```.


## Install QuantLab and `quantlib`

QuantLab and `quantlib` are available on the [GitHub page of the PULP project](https://github.com/pulp-platform).
You can obtain a copy by issuing the following commands:

```
$ cd ~
$ git clone https://github.com/pulp-platform/quantlab.git
$ cd quantlab
$ git submodule update --init
```

Then, install their dependencies by creating a dedicated Anaconda environment:
```
$ conda env create -f quantlab.yml
$ conda activate quantlab
(quantlab) $ cd quantlib
(quantlab) $ python setup.py install
(quantlab) $ conda deactivate
```


## Download the exercise and execute it

If you managed to followed the process so far, you should be able to execute the Jupyter notebook with the exercise.
First, clone a copy of this repository:
```
$ cd ~
$ git clone 
```

Before starting the exercise, download the checkpoint containing the pre-trained parameters of the VGG-9 network that is the subject of the notebook:
```
$ mkdir -p .../logs_vgg
$ cp ~/Downloads/... ~/.../logs_vgg
```

You are now ready to go through the notebook. Enjoy!
```
$ conda activate quantlab
(quantlab) $ cd ...
(quantlab) $ jupyter notebook APAI-LAB03-QuantLab.ipynb
```
