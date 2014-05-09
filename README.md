# dynip
Manage your dynamic IP (DNS) settings for one or more subdomains at
[FreeDNS](http://freedns.afraid.org).

## Installation
This application has been tested successfully on FreeBSD, Linux and
Windows 7/8, under Python versions 3.4, 3.3 and 2.7.  You should not
try Python 2.6 or earlier unless you install package argparse first.

### Step 0: Ensure Python 2.7 or later is installed
You can verify this by running ```python -V``` at a command prompt.  If
needed, download and
[install Python from here](https://www.python.org/downloads/).

### Step 1: Set up your account and subdomain(s) at FreeDNS
Follow their [ample guidance](http://freedns.afraid.org).

### Step 2: Configure this tool with your FreeDNS settings
Download and edit the ```freedns``` file, configuring the
three FREEDNS_* variables near the top, to record your username,
password and the subdomains you wish to manage from this location.

Separate each subdomain with any type of white space (including newlines)
between the triple quotes, like so:

```
FREEDNS_SUBDOMAINS = """
        xyz.mooo.com
        abc.afraid.org
"""
```

(If installing on Windows, you may also want to rename the file with a ```.py```
extension.  Otherwise, run it like ```python freedns```.  Neither of these
approaches are necessary for Linux, FreeBSD or OSX.)

### Step 3: (Optional) Schedule recurring updates
If you want to keep FreeDNS updated with your latest dynamic IP address, schedule this
script to run at regular intervals.  For example, a crontab entry like this
will cause checks/updates every four hours (substitute your actual installation path):

```
5  */4  *  *  *  /home/peter/bin/freedns
```

## Usage
Run with --help (or -h) to see usage instructions.

The tool has two primary modes:
+ update
+ status

### update
```
freedns
freedns update
freedns -d xyz.afraid.org
freedns update --domain xyz.afraid.org
```
Running with no arguments (or 'update') checks your current public IP address
against the settings at FreeDNS and sends an update only if needed.

You may optionally use ```--domain``` or ```-d``` to limit this operation to
just one of your configured subdomains.

### status
```
freedns status
```
The tool also keeps a cache of recent statistics (in your $HOME or %LOCALAPPDATA%
directory) that you can review using argument 'status', which provides output
similar to:

```
subdomain         IP-last-check    last-checked         unchanged-since      checks-since
-----------------------------------------------------------------------------------------
xyz.mooo.com      71.191.181.141   2014-05-05 21:24:08  2013-04-05 13:06:41        324018
abc.afraid.net    71.191.181.141   2014-05-05 21:22:40  2013-04-05 13:06:40        324013
```

## Feedback
Please ask any questions, report problems, and provide feedback to:  peterjpierce@gmail.com

Thank you!
