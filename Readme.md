FPGA-SoC-Linux-Example-1-DE10-Nano
=====================================

FPGA-SoC-Linux example(1) binary and project and test code for DE10-Nano

### Requirement

* Board: DE10-Nano
* OS: [FPGA-SoC-Linux](https://github.com/ikwzm/FPGA-SoC-Linux.git)

## Install

### Install python3-numpy

```console
shell# apt-get install python3-numpy
```

### Download FPGA-SoC-Linux-Example-1-DE10-Nano

```console
shell$ git clone https://github.com/ikwzm/FPGA-SoC-Linux-Example-1-DE10-Nano
shell$ cd FPGA-SoC-Linux-Example-1-DE10-Nano
```

### Install to FPGA and Device Tree

```console
shell# rake install
cp pump_axi4.rbf /lib/firmware/pump_axi4.rbf
dtbocfg.rb --install uio_irq_sample --dts uio_irq_sample.dts
<stdin>:17.13-22.20: Warning (unit_address_vs_reg): /fragment@1/__overlay__/pump-uio: node has a reg or ranges property, but no unit name
<stdin>:9.13-36.5: Warning (avoid_unnecessary_addr_size): /fragment@1: unnecessary #address-cells/#size-cells without "ranges" or child "reg" property
[  830.493939] fpga_manager fpga0: writing pump_axi4.rbf to Altera SOCFPGA FPGA Manager
[  830.697564] OF: overlay: WARNING: memory leak will occur if overlay removed, property: /soc/fpga-region0/firmware-name
[  830.731745] u-dma-buf udmabuf4: driver version = 3.0.1
[  830.736879] u-dma-buf udmabuf4: major number   = 245
[  830.741900] u-dma-buf udmabuf4: minor number   = 0
[  830.746680] u-dma-buf udmabuf4: phys address   = 0x3f100000
[  830.752287] u-dma-buf udmabuf4: buffer size    = 4194304
[  830.757628] u-dma-buf udmabuf4: dma device     = soc:amba:pump-udmabuf4
[  830.764218] u-dma-buf udmabuf4: dma coherent   = 1
[  830.769029] u-dma-buf soc:amba:pump-udmabuf4: driver installed.
[  830.792116] u-dma-buf udmabuf5: driver version = 3.0.1
[  830.797393] u-dma-buf udmabuf5: major number   = 245
[  830.802342] u-dma-buf udmabuf5: minor number   = 1
[  830.807115] u-dma-buf udmabuf5: phys address   = 0x3f500000
[  830.812722] u-dma-buf udmabuf5: buffer size    = 4194304
[  830.818078] u-dma-buf udmabuf5: dma device     = soc:amba:pump-udmabuf5
[  830.824669] u-dma-buf udmabuf5: dma coherent   = 1
[  830.829497] u-dma-buf soc:amba:pump-udmabuf5: driver installed.
```

## Run sample1 or sample2

### Compile sample1 or sample2

```console
shell# rake sample1 sample2
```

### Run sample1

```console
shell# ./sample1
time = 0.005702 sec
time = 0.005685 sec
time = 0.005668 sec
time = 0.005681 sec
time = 0.005690 sec
time = 0.005677 sec
time = 0.005698 sec
time = 0.005707 sec
time = 0.005662 sec
time = 0.005692 sec
```

### Run sample2

```console
shell$ ./sample2
time = 0.005713 sec
time = 0.005694 sec
time = 0.005688 sec
time = 0.005720 sec
time = 0.005708 sec
time = 0.005687 sec
time = 0.005693 sec
time = 0.005701 sec
time = 0.005723 sec
time = 0.005718 sec
```

## Run sample.py

```console
shell# python3 sample.py
elapsed_time:5.912[msec]
elapsed_time:5.847[msec]
elapsed_time:5.833[msec]
elapsed_time:5.839[msec]
elapsed_time:5.826[msec]
elapsed_time:5.841[msec]
elapsed_time:5.832[msec]
elapsed_time:5.842[msec]
elapsed_time:5.84[msec]
average_time:5.846[msec]
thougput    :179.374[MByte/sec]
udmabuf4 == udmabuf5 : OK
```

## Uninstall

```console
shell# rake uninstall
dtbocfg.rb --remove uio_irq_sample
[  476.886343] udmabuf udmabuf5: driver uninstalled
[  476.891485] udmabuf amba:fpga-region0:pump-udmabuf5: driver unloaded
[  476.899289] udmabuf udmabuf4: driver uninstalled
[  476.904421] udmabuf amba:fpga-region0:pump-udmabuf4: driver unloaded
```


## Build Bitstream file

### Requirement

* Intel Quartus Prime 18.1.0 Lite Edition 

### Download FPGA-SoC-Linux-Example-1-Base

```console
shell$ cd FPGA-SoC-Linux-Example-1-DE10-Nano
shell$ git submodule update --init --recursive
```

### Build DE10_NANO.rbf

Run SoC EDS Command Shell

```console
shell$ cd project
shell$ make rbf
```

### Copy DE10_NANO.rbf to pump_axi4.rbf

```console
shell$ cd project
shell$ cp DE10_NANO.rbf ../pump_axi4.rbf
```
