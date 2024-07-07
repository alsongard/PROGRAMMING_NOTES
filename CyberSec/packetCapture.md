# TCPDUMP TOOL

# Description
the ``tcpdump`` is used to capture packets in a network.

## Syntax 
tcpdump -
## OPTIONS

** OUTPUT **
Use the option ``-c`` to determine the number of packets to be captured.
Command : ``tcpdump -c``

** INTERFACE **
To list the interface use the command ``-D`` which will provide a list of interface on your computer.
Command : ``tcpdump -D``
To use a specific interface use the flag ``-i``.
Command : ``tcpdump -i wlan0 | tcpdump -i eth0``

### FILE  OUTPUT
to output use the > or >> operator. If a file is new use the `>` to output to the file and use the ``>>`` to append data to a file.
 
