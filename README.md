# sshim

An sshd for public services over ssh. It has the following defining features:

  The public key of the first user to login with a username is bound to it

  Subsequent logins to the username require the original public key

  A single unix user is utilized for unlimited logins



# Overview

`sshim` is a fairly simple ssh server written in Python. The main use-case is for hosting a specific program to users shelling into a host. `sshim` solves the problem of not needing to run a web-service or other registration mechanism. The first time any username used to login is immediately associated with the public key used for the connection. Every user logging in is forced to execute the shell of a single unix user on the host with those associated privileges.

# Installation

However preferred, install Python and the `twisted`, `pyasn1` and `pycrypto` libraries:

    pip install twisted pyasn1 pycrypto

Then just copy over the `sshim` script.

# Configuration

A system user will be needed for running the desired user shell:

    sudo useradd -s /path/to/shell sshim

# Running

The script will route all logins to whatever user appears in the `$USER` environment variable. If not directly set, this will be the user executing the script.

The service will be made available on port `2200` by default. Change it with `$PORT`.

# Public Keys

The public keys that are bound to usernames are stored as `~/.ssh/$USERNAME.pub` for which ever system is being used.


