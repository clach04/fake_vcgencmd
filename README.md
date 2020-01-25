# rock64_vcgencmd

vcgencmd partial clone for rock64 SBC to allow Raspberry Pi tools/scripts to run unmodified on rock64

Works with https://github.com/eidottermihi/rpicheck

Install vcgencmd into /usr/bin/vcgencmd and set execute bit. Example from
source checkout:

    cp vcgencmd /usr/bin/vcgencmd
    chmod a+x /usr/bin/vcgencmd

NOTE relies on rock64_health.sh - https://github.com/pfeerick/rock64-scripts

Install over the web:

    wget -O /usr/bin/vcgencmd https://raw.githubusercontent.com/clach04/rock64_vcgencmd/master/vcgencmd
    chmod a+x /usr/bin/vcgencmd

