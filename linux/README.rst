================================================================================
Linux
================================================================================

Useful tools, tips, and Bash commands for Linux, Ubuntu distribution.

.. contents::


Getting Host System Information
--------------------------------------------------------------------------------

Bash commands for getting Linux host system info.


* Print system information ::

    $ uname -a
    Linux hostname 5.15.90.1-microsoft-standard-WSL2 #1 SMP Fri Jan 27 02:56:13 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

* Print Linux version info: ::

    $ cat /proc/version
    Linux version 5.15.90.1-microsoft-standard-WSL2 (oe-user@oe-host) (x86_64-msft-linux-gcc (GCC) 9.3.0, GNU ld (GNU Binutils) 2.34.0.20200220) #1 SMP Fri Jan 27 02:56:13 UTC 2023
    
* Print Linux distribution info: ::

    $ cat /etc/os-release
    PRETTY_NAME="Ubuntu 22.04.2 LTS"
    NAME="Ubuntu"
    VERSION_ID="22.04"
    VERSION="22.04.2 LTS (Jammy Jellyfish)"
    VERSION_CODENAME=jammy
    ID=ubuntu
    ID_LIKE=debian
    HOME_URL="https://www.ubuntu.com/"
    SUPPORT_URL="https://help.ubuntu.com/"
    BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
    PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
    UBUNTU_CODENAME=jammy


Give User Sudo Abilities
--------------------------------------------------------------------------------
When trying to run :code:`sudo apt-get update`, the resulting output was: ::

    user_name is not in the sudoers file.  This incident will be reported.

See `this solution <https://stackoverflow.com/questions/47806576/linux-username-is-not-in-the-sudoers-file-this-incident-will-be-reported>`_
for more context.

At the top of the aforementioned /etc/sudoers file there's an info: ::

    "## This file MUST be edited with the 'visudo' command as root."

In order of doing as we're told, use: ::

    $ su
    > Enter root password: *******
    $ visudo -f /etc/sudoers

Find the following section of /etc/sudoers file and add your users privileges: ::

    # User privilege specification
    root    ALL=(ALL:ALL) ALL
    user_name ALL=(ALL) ALL

Save the file (press esc and type :x if vim is your default text editor, for nano press ctrl+o, enter and then ctrl+x).

Type exit to turn off the root shell, and enjoy the power of sudo with your username.


Linux Documentation
--------------------------------------------------------------------------------

Pull in relevant kernel documentation package (Debian): ::
    
    sudo apt install linux-doc

You’ll find all the documentation in text and HTML formats under :code:`/usr/share/doc/linux-doc/Documentation/`
and :code:`/usr/share/doc/linux-doc/html/` respectively.

Source: see `this response <https://unix.stackexchange.com/questions/658427/offline-documentation-of-kernel-org>`_
on StackExchange.

    TODO: add notes on how to build in Ubuntu 22.04.


Miscellanious
--------------------------------------------------------------------------------

Open a terminal
^^^^^^^^^^^^^^^
**Ctrl + Alt + T**

Compressing / uncompressing :code:`.gz` files in Bash
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    $ gzip -h
    Usage: gzip [OPTION]... [FILE]...
    Compress or uncompress FILEs (by default, compress FILES in-place).

Example (decompress :code:`file.gz`): ::

    $ gzip -d file.gz


Signal EOF from Bash
^^^^^^^^^^^^^^^^^^^^

To signal EOF from Bash shell: :code:`Ctrl-D`




TODO
--------------------------------------------------------------------------------

* Add notes on how to build in Ubuntu 22.04.
