# On Linux

For Linux you will see a deb and rpms, install the appropriate one.
For testing purposes you can run the client on the same machine as
the server if you like.

The process depends on your environment, if you have a
mechanism such as puppet, then building as a Deb package and deploying
that way makes the most sense. Alternatively you can deploy using ssh:

    scp agent_version.deb host:/tmp/
    ssh host sudo dpkg -i /tmp/agent_version.deb

On MacOS X, the same process applies, use puppet or equivalent if you
have, or use ssh.

# Uninstalling GRR

This is a quick manual on how to remove the GRR client completely from a machine.

On Linux the standard system packaging (deb, pkg) is used by default.
Use the standard uninstall mechanisms for uninstalling.

    dpkg -r grr

This might leave some config files lying around, if a complete purge is necessary, the list of files to delete is:

    /usr/lib/grr/*
    /etc/grr.local.yaml
    /etc/init/grr.conf

On GRTE machines GRR is distributed as a .par file, the .par is

    /usr/sbin/grrd

The GRR service can be stopped using

    sudo service grr stop