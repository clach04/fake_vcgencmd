# Fake vcgencmd for generic Linux, Armbian, Odroid and Rock64

Shell script vcgencmd partial clone for rock64 SBC to allow Raspberry Pi tools/scripts to run unmodified on rock64
Works with Armbian (and probably works with x86 too).

Works with https://github.com/eidottermihi/rpicheck

Install vcgencmd into /usr/bin/vcgencmd and set execute bit. Example from
source checkout:

    sudo cp vcgencmd /usr/bin/vcgencmd
    sudo chmod a+x /usr/bin/vcgencmd

Originally relied on rock64_health.sh - https://github.com/pfeerick/rock64-scripts  now uses `/sys/` interface.

Install over the web:

    wget -O /usr/bin/vcgencmd https://raw.githubusercontent.com/clach04/rock64_vcgencmd/master/vcgencmd
    chmod a+x /usr/bin/vcgencmd

## What works

    vcgencmd version
    vcgencmd measure_temp
    vcgencmd measure_clock arm

    vcgencmd measure_volts core  # this is faked out and incorrect, just enough to satisfy rpicheck
    vcgencmd measure_clock core  # this is faked out and incorrect, just enough to satisfy rpicheck
 
