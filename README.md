# Fake vcgencmd for generic Linux, Armbian, Odroid, Pine64, Rock64 and other SBCs

Shell script vcgencmd partial clone to allow Raspberry Pi tools/scripts to run
unmodified on SBCs. Works with Armbian (and probably works with x86 too).

Works with Android app https://github.com/eidottermihi/rpicheck

For Armbian can use script as-is or check out https://github.com/armbian/build/pull/5095

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
 
