PGA-SoC-Linux-Example-1-DE10-Nano
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
shell$ git clone FPGA-SoC-Linux-Example-1-DE10-Nano
shell$ cd FPGA-SoC-Linux-Example-1-DE10-Nano
```

### Install to FPGA and Device Tree

```console
shell# rake install
dtbocfg.rb --install uio_irq_sample --dts uio_irq_sample.dts
cp pump_axi4.rbf /lib/firmware/pump_axi4.rbf
dtbocfg.rb --install uio_irq_sample --dts uio_irq_sample.dts
/config/device-tree/overlays/uio_irq_sample/dtbo: Warning (unit_address_vs_reg): [25851.013494] fpga_manager fpga0: writing pump_axi4.rbf to Altera SOCFPGA FPGA Manager
Node /uio-irq-test@0 has a unit name, but no reg property
[25851.281944] udmabuf soc:fpga-region0:pump-udmabuf4: driver probe start.
[25851.302254] udmabuf udmabuf4: driver installed
[25851.306800] udmabuf udmabuf4: major number   = 244
[25851.311572] udmabuf udmabuf4: minor number   = 0
[25851.316173] udmabuf udmabuf4: phys address   = 0x3f100000
[25851.321618] udmabuf udmabuf4: buffer size    = 4194304
[25851.326793] udmabuf udmabuf4: dma coherent   = 0
[25851.331397] udmabuf soc:fpga-region0:pump-udmabuf4: driver installed.
[25851.338417] udmabuf soc:fpga-region0:pump-udmabuf5: driver probe start.
[25851.358070] udmabuf udmabuf5: driver installed
[25851.362507] udmabuf udmabuf5: major number   = 244
[25851.367319] udmabuf udmabuf5: minor number   = 1
[25851.371921] udmabuf udmabuf5: phys address   = 0x3f500000
[25851.377353] udmabuf udmabuf5: buffer size    = 4194304
[25851.382473] udmabuf udmabuf5: dma coherent   = 0
[25851.387113] udmabuf soc:fpga-region0:pump-udmabuf5: driver installed.
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

* Altera 15.1.0.185 Lite Edition 

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
