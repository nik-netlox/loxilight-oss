### Blue Field2 DPU firmware Inatallation
Bluefield-II already comes with a pre-loaded version of Ubuntu 20.04 but it is strongly recommended to install latest version of newly released DOCA package to enjoy the latest features. Follow these steps to upgrade the SmartNIC:

1. Download the latest version of Bluefield-2 DOCA software package from [here](https://duckduckgo.com).

2. Install the BFB file using rshim interface as
> Assuming RSHIM driver is already installed on the Host Server (If not, then download and install the rshim deb package from [here](https://developer.nvidia.com/networking/doca)). 

```
$ cat install.bfb > /dev/rshim<N>/boot
```
> Detailed steps about initialization and installation are mentioned [here](https://docs.mellanox.com/display/BlueFieldSWv36011699/Installation+and+Initialization#heading-DeviceFiles).

3. Install MLNX_OFED on the Host Server. Download the MLNX_OFED driver package tgz from [here](https://developer.nvidia.com/networking/doca#drivers). Unzip the package and install it as
```
$ ./mlnxofedinstall
$ /etc/init.d/openibd restart
```
> After this step, you will see Host PF/VF.
