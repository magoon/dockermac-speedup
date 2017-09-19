# Docker for Mac performance improvement

Selectively mount only the volumes you're working on for a 2-5x
performance improvement, depending on project over-using host mounts

Use in place of docker-compose up -d service1 serviceN

Creates & invokes a temporary, more limited docker-compose yaml 
and also supports docker-compose.override.yml

Alternative to docker-machine, d4m-nfs, docker-sync.io

This will add "delegated" volume mount mode to the services
you invoke with the script and will also remove the volume mounts
to all other services. This means that container file systems will
not be linked to your source folders, except for the services you
specify. 

The delegated mode is new as of Docker for Mac 17.06 and
is highly performant, at the cost of consistency; the container's file
system is more trusted, and writes made on the container are not
guaranteed to be sync'd to the host quickly or reliably. If you do
not want to use "delegated" you can force "cached" or "consistent"
in your docker-compose.yml.

This has been tested with Docker for Mac 17.06 Stable.

# Install:

Place this script alongside docker-compose.yml, or symlink it to ~/bin

# Usage:

> speedup edit rover

http://github.com/magoon/dockermac-speedup

