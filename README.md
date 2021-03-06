pgpool-II plugin for munin
--------------------------

Perl version implementation of munin\_pgpool(Python) in repository https://github.com/vpetersson/munin_pgpool .

## SETUP
### Install

Copy __pgpool2_connections__ into munin plugins directory such as /usr/share/munin/plugins
and make symbolic link to the file like following commands:

    # install -o root -m 0755 ./pgpool2_connections /usr/share/munin/plugins
    # ln -s /usr/share/munin/plugins/pgpool2_connections /etc/munin/plugins/

## Configuration and Run

### Edit plugin config file
    # vi /etc/munin/plugin-conf.d/pgpool

    [pgpool2_*]
    env.host 127.0.0.1
    env.port 9898
    env.user munin
    env.userpwd password
    env.pcppath /path/to/pcp_pool_status

If "env.pcppath" is not defined, the plugin finds "pcp\_pool\_status" command 
from directories listed in $PATH environment variable. When the command is not
installed your system, for example installed pgpool-II is 3.0 or older, the plugin
gets the value of "num\_init\_children" from pgpool.conf file.

### Run with munin-run command
    # cd /etc/munin/plugins/
    # munin-run ./pgpool2_connections
    wait.value 32
    idle.value 88
    max.value 120

AUTHOR
------
azumakuniyuki

LICENSE
-------
The MIT License (MIT)

Copyright (c) 2013 azumakuniyuki

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

