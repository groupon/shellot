Shellot
==========

Slim terminal realtime graphing tool

Translates some typical "tail -f" cases into realtime graphs

For example, if you're able to create a continuous output of status codes like this:
```
$ ssh webserver.mydomain.com "tail -f /var/log/httpd/access_log"\
     | awk '/ "GET \/index.html / {print $9;fflush();}'
200
200
200
302
200
404
200
...

```

just pipe shellot at the end of command line and shellot will draw something like:

![](shellot.png?raw=true)

where every second it will plot how many events of each key it got

More info:
```
./shellot --help
```

### How to install ###
* fetch the one ruby file "shellot" from github to your laptop or any server
* add execution permission: chmod +x shellot
* test count of two events happening in random times:
```
for i in {1..10000}; do echo event$[($RANDOM % 2)]; sleep .001; done | ./shellot
```
* test average of random milliseconds:
```
for i in {1..10000}; do echo ms=$[($RANDOM % 20)]; sleep .001; done | ./shellot -a
```

### Requirements ###
* ruby >= 1.8, no gem dependencies. This means, almost any Linux/Mac

License
-------

    Copyright (c) 2013, Groupon, Inc.
    All rights reserved.

    Redistribution and use in source and binary forms, with or without
    modification, are permitted provided that the following conditions are
    met:

    Redistributions of source code must retain the above copyright notice,
    this list of conditions and the following disclaimer.

    Redistributions in binary form must reproduce the above copyright
    notice, this list of conditions and the following disclaimer in the
    documentation and/or other materials provided with the distribution.

    Neither the name of GROUPON nor the names of its contributors may be
    used to endorse or promote products derived from this software without
    specific prior written permission.

    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS
    IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED
    TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A
    PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
    HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
    SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED
    TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR
    PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF
    LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING
    NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
    SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

Tests
-----
In Ruby 1.8 and Ruby 1.9:
```
./shellot --test
./shellot --help
for i in {1..10000}; do echo event$[($RANDOM % 2)]; sleep .001; done | ./shellot
for i in {1..10000}; do echo ms=$[($RANDOM % 20)]; sleep .001; done | ./shellot -a

```
