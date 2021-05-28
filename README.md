# Calculating stability parameters using SHARPpy

Author: Rebekah Esmaili, STC

The purpose of this code is to automatically calculate the stability parameters for NUCAPS profiles. This will eliminate the need to use the GUI and manually check the stability profiles for larger datasets. For smaller datasets, it's probably easier to use the GUI.

## How to install/run this code from the command line

To download the contents of this repository using git, use the following command:

```
git clone https://github.com/NUCAPS/stability_calcs.git
```
Change directories to the newly downloaded folder:

```
cd stability_calcs
```

Next, install a new environment with which will have all the dependent libraries:

```
conda env create -f environment.yml
```

This step may take a while. Once done, you can switch into this new environment using:

```
conda activate calc_cape
```

Before making any changes, make sure the test data works. You can use jupyter notebook or run the script for the command line. To run the script from the command line, type:
```
python cape calcs.py
```

If you do not have any errors and two new png files are produced, the code ran successfully.

## Processing a different dataset

The program will read all text files in the j01 directory along with the csv "control file." The text files contain the profile temperature and moisture data. The csv file says where these profiles are located (lat/lon), the quality flag, and the cloud top pressure/fraction.

To run this script on another day, either remove the files in the j01 directory or create a new folder. If you create a new folder, update the paths in the python script.

## Changing the stability parameters

To customize this script, you will have to familiarize yourself with some fo the available commands in the sharppy library. I recommend reading
[the user guide](https://sharppy.github.io/SHARPpy/scripting.html).

Right now, the script is only designed to make plots. It might be helpful to print the results to a file and store them for later.

The current version of the code is only calculating sfc cape. Here is a list of SOME of the available stability parameters:

```
pcl.pres - Parcel beginning pressure (mb)
pcl.tmpc - Parcel beginning temperature (C)
pcl.dwpc - Parcel beginning dewpoint (C)
pcl.ptrace - Parcel trace pressure (mb)
pcl.ttrace - Parcel trace temperature (C)
pcl.blayer - Pressure of the bottom of the layer the parcel is lifted (mb)
pcl.tlayer - Pressure of the top of the layer the parcel is lifted (mb)
pcl.lclpres - Parcel LCL (lifted condensation level) pressure (mb)
pcl.lclhght - Parcel LCL height (m AGL)
pcl.lfcpres - Parcel LFC (level of free convection) pressure (mb)
pcl.lfchght - Parcel LFC height (m AGL)
pcl.elpres - Parcel EL (equilibrium level) pressure (mb)
pcl.elhght - Parcel EL height (m AGL)
pcl.mplpres - Maximum Parcel Level (mb)
pcl.mplhght - Maximum Parcel Level (m AGL)
pcl.bplus - Parcel CAPE (J/kg)
pcl.bminus - Parcel CIN (J/kg)
pcl.bfzl - Parcel CAPE up to freezing level (J/kg)
pcl.b3km - Parcel CAPE up to 3 km (J/kg)
pcl.b6km - Parcel CAPE up to 6 km (J/kg)
pcl.p0c - Pressure value at 0 C  (mb)
pcl.pm10c - Pressure value at -10 C (mb)
pcl.pm20c - Pressure value at -20 C (mb)
pcl.pm30c - Pressure value at -30 C (mb)
pcl.hght0c - Height value at 0 C (m AGL)
pcl.hghtm10c - Height value at -10 C (m AGL)
pcl.hghtm20c - Height value at -20 C (m AGL)
pcl.hghtm30c - Height value at -30 C (m AGL)
pcl.wm10c - Wet bulb velocity at -10 C
pcl.wm20c - Wet bulb velocity at -20 C
pcl.wm30c - Wet bulb at -30 C
pcl.li5 = - Lifted Index at 500 mb (C)
pcl.li3 = - Lifted Index at 300 mb (C)
pcl.brnshear - Bulk Richardson Number Shear
pcl.brnu - Bulk Richardson Number U (kts)
pcl.brnv - Bulk Richardson Number V (kts)
pcl.brn - Bulk Richardson Number (unitless)
pcl.limax - Maximum Lifted Index (C)
pcl.limaxpres - Pressure at Maximum Lifted Index (mb)
pcl.cap - Cap Strength (C)
pcl.cappres - Cap strength pressure (mb)
pcl.bmin - Buoyancy minimum in profile (C)
pcl.bminpres - Buoyancy minimum pressure (mb)
```

... and there are more.
