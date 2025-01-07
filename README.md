As you know, the DVB-T Receiver 820T2 can be physically modified and be able to receives low ham radio frequencies (f.ex. 1.8 – 14MHz).

1. Install procedure:

```
git clone git://git.osmocom.org/rtl-sdr.git

cd rtl-sdr/

mkdir build

cd build

{now here is the trick: please replace the 
rtl-sdr/src/rtl_tcp.c with a file downloaded and unpacked 
from archive available on the bottom of this site}

cmake ../ -DINSTALL_UDEV_RULES=ON

make

sudo make install

sudo ldconfig

sudo cp ../rtl-sdr.rules /etc/udev/rules.d/
```

2. How to use this ?
There is a new -i parameter available:


rtl_tcp, an I/Q spectrum server for RTL2832 based DVB-T receivers
Modified by Jakub/SP5TOF on 07.02.2017 for direct sampling support

Usage: [-a listen address]
 [-p listen port (default: 1234)]
 [-f frequency to tune to [Hz]]
 [-g gain (default: 0 for auto)]
 [-s samplerate in Hz (default: 2048000 Hz)]
 [-b number of buffers (default: 32, set by library)]
 [-n max number of linked list buffers to keep (default: 500)]
 [-d device index (default: 0)]
 [-P ppm_error (default: 0)]
 [-i direct sampling(1: I-ADC input enabled), 2: Q-ADC input enabled)]
 [-c AGC Mode(1: ON, 0: OFF), default: 1(ON)
 
 Example:

  rtl_tcp -i 1 -c 0 -g 49.6

By typing the command above, you will be able to launch the rtl_tcp process with support of hardware mod for direct sampling(the RF input can be directly connected to the I pad on the dongle’s PCB).

PLEASE BE AWARE THAT IT WORKS ONLY WITH RTL-SDR-0.5.3 DRIVER!
In case of any further driver releases comes from GIT, provided file will has to be rewritten!

More informations can be found : http://sp5tof.qrz.pl

