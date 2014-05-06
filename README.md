# dynip
Manage your dynamic DNS settings for one or more subdomains at
[FreeDNS](http://freedns.afraid.org).

## Installation
The current version requires Python 3 and has only been tested on Linux and
FreeBSD.  A Python 2 version will be released soon.


### Step 1: Set up your account and subdomain(s) at FreeDNS
Follow their ample instructions.

### Step 2: Configure FreeDNS
Download this repository, and edit the `freedns` file, configuring the three `FREEDNS_*`
variables near the top, to record your username, password and subdomains.

To list the subdomains you are managing, separate each with a newline between the triple
quotes, like so:

```
FREEDNS_SUBDOMAINS = """
        xyz.mooo.com
        xyz.afraid.org
""".split()
```

### Step 3: (Optional) Schedule recurring updates
If you want keep FreeDNS updated with your latest dynamic IP, schedule this
script to run at regular intervals.  For example, a crontab entry like this would
cause updates every four hours (substitute your installation location):

```
5  */4  *  *  *  /home/peter/bin/freedns
```

## Usage
Run with --help (or -h) to see usage instructions.

The tool has two primary modes:
+ update
+ status

# update
Running with no arguments (or 'update') checks your current public IP address
against settings at FreeDNS and attempts a change only if needed.

You may optionally use ```--domain``` to limit this operation to just one of
your configured subdomains.

# status
The tool also keeps a cache of recent statistics (in $HOME/.freedns.cache) which
you can review using argument 'status', which provides output similar to:

```
subdomain         IP-last-check    last-checked         unchanged-since      checks-since
-----------------------------------------------------------------------------------------
xyz.mooo.com      71.191.181.141   2014-05-05 21:24:08  2013-04-05 13:06:41        324018
abc.afraid.net    71.191.181.141   2014-05-05 21:22:40  2013-04-05 13:06:40        324013
```

## Donations
Encouragement is gratefully accepted:

+ BTC: `1CavTJLrtRXfWJ5MKZH53dudfq9aWa3z6E`
+ LTC: `LhdsXnNjZyMJF8TrvV7y1pSmhyQSs9RyB7`
+ GLD: `E3qqqrLejCXVPjZD9XnabYNXvJ8nDeHymF`

Thank you!
