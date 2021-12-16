The prelinking feature changes  binaries  in  an  attempt  to  decrease  their
startup  time.  Because  the  prelinking  feature  changes  binaries,  it  can
interfere with the operation of certain software and/or modes  such  as  AIDE,
FIPS, etc. This module will attempt to disable it.

# Installation
```
cfbs add prelinking-disabled
```

# Examples
Running CFEngine with this module in your policy set on  a  system  which  has
prelinking enabled should produce similar output as below:

```
# cf-agent -KI
    info: Replaced pattern '^\s*(PRELINKING\s*=\s*(?!no$).*|PRELINKING)$' in '/etc/default/prelink'
    info: replace_patterns promise '^\s*(PRELINKING\s*=\s*(?!no$).*|PRELINKING)$' repaired
    info: Edited file '/etc/default/prelink'
    info: Executing 'no timeout' ... '/usr/sbin/prelink -ua'
    info: Completed execution of '/usr/sbin/prelink -ua'
```

The prelink configuration file was changed in order to disable prelinking, and
the `prelink` binary was run in order to enforce the changes in configuration.

If you run cf-agent -KI again, the file will already be  correct,  no  changes
will be made and there will be no log messages. Of course, you don't  have  to
run the policy manually from the command  line.  As  long  as  the  module  is
included in your policy set and deployed to your policy  server,  it  will  be
automatically enforced in all your infrastructure.

# Authors
This  module  was  created  by   [larsewi](https://github.com/larsewi),   with
contributions from the CFEngine community. Thanks!

# Contribute
Feel free to open pull requests to expand on this module.

# License
This software is licensed under the MIT License. See LICENSE in  the  root  of
the repository for the full license text.
