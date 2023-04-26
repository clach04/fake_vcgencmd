# Fake vcgencmd for generic Linux, Armbian, Odroid, Pine64, Rock64 and other SBCs

Shell script vcgencmd partial clone to allow Raspberry Pi tools/scripts to run
unmodified on SBCs. Works with Armbian (and probably works with x86 too).

Works with Android app https://github.com/eidottermihi/rpicheck

Some Armbian [builds](https://github.com/armbian/build/tree/main/config/boards)
already include this script. However, the script can be used as-is on many
systems. In case Armbian does not include this script in their build for your
board, but you have tested that this script works properly, you can
[request Armbian](https://github.com/armbian/build/issues) to include it for
 your board.

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
 
## Adding support for new parameters

Add the following to the end of the script `vcgencmd` for quick and easy debug logs:

    exit
    # remove/comment out exit about for debug logging
    # NOTE may need allow permissions on file:
    #	sudo chmod a+w /var/log/vcgencmd.log


    # if we got here, unrecognized parameter
    # log it for debugging purposes

    # on this device /var/log is ramfs folder2ram
    LOG=/var/log/vcgencmd.log
    LOG=/tmp/vcgencmd.log


    date >> ${LOG}
    echo PARAM star ${*} PARAM >> ${LOG}
    echo PARAM one ${1} PARAM >> ${LOG}
    echo PARAM two ${2} PARAM >> ${LOG}
    echo '=============' >> ${LOG}
