# rock64_vcgencmd

vcgencmd partial clone for rock64 SBC to allow Raspberry Pi tools/scripts to run unmodified on rock64

Works with https://github.com/eidottermihi/rpicheck

Install vcgencmd into /usr/bin/vcgencmd and set execute bit. Example:

    cp vcgencmd /usr/bin/vcgencmd
    chmod a+x /usr/bin/vcgencmd

NOTE relies on rock64_health.sh - https://github.com/pfeerick/rock64-scripts

