Ordissimo/VZ6
=============

*"Installation procedure for the Ordissimo's VZ6 platform"*

# Download

```
$ git clone https://github.com/Ventto/gslx680-acpi.git
$ git clone https://github.com/Ventto/gsl-firmware.git
```

# Build

* Go into the module driver's repository:

```shell
$ cd gslx680-acpi
```

* From the development platform:

```shell
$ make KSRC=<path_to_ktree> ARCH=x86_64
```

* (Or) from the target:

```shell
$ make
```

# Install

* Copy the calibrated firmware for the gslx680\_ts\_acpi driver on the target:

```shell
$ scp ../gsl-firmware/firmware/ordissimo/vz6/silead_ts.fw \
    root@<target_ip>:/lib/firmware
```

* From the development platform:

```shell
$ make KSRC=<path_to_ktree> ARCH=x86_64
$ scp gslx680_ts_acpi.ko \
    root@<target_ip>:/lib/modules/<kernel_version>/kernel/drivers/gslx680_ts_acpi.ko
$ ssh root@<target_ip> depmod -a
```

* (Or) from the target:

```shell
$ make install
```
