# Disable prelinking
Some Linux distrobutions may require prelinking to be installed,
but prelinking may conflict with some integrity checkers.
A workaround would be to disable prelinking.

This module disables prelinking by setting `PRELINKING=no` in the respective configuration file, if present.
Subsequently `/etc/cron.daily/prelink` is run - if promise is repaired - in order to enforce the changes.
