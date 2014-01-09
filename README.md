This is a fork of the DNSChef project v0.2.1 hosted at: http://thesprawl.org/projects/dnschef/

Overview
========

DNSChef is a highly configurable DNS proxy for Penetration Testers and Malware Analysts. A DNS proxy (aka "Fake DNS") is a tool used for application network traffic analysis among other uses. For example, a DNS proxy can be used to fake requests for "badguy.com" to point to a local machine for termination or interception instead of a real host somewhere on the Internet.

There are several DNS Proxies out there. Most will simply point all DNS queries a single IP address or implement only rudimentary filtering. DNSChef was developed as part of a penetration test where there was a need for a more configurable system. As a result, DNSChef is cross-platform application capable of forging responses based on inclusive and exclusive domain lists, supporting multiple DNS record types, matching domains with wildcards, proxying true responses for nonmatching domains,
defining external configuration files, IPv6 and many other features. You can find detailed explanation of each of the features and suggested uses below.

The use of DNS Proxy is recommended in situations where it is not possible to force an application to use some other proxy server directly. For example, some mobile applications completely ignore OS HTTP Proxy settings. In these cases, the use of a DNS proxy server such as DNSChef will allow you to trick that application into forwarding connections to the desired destination.

Version 0.2 introduces IPv6 support, large number of new DNS record types, custom ports and other frequently requested features.

Running DNSChef
===============

DNSChef is a cross-platform application developed in Python which should run on most platforms which have a Python interpreter. You can use the supplied dnschef.exe executable to run it on Windows hosts without installing a Python interpreter. This guide will concentrate on Unix environments; however, all of the examples below were tested to work on Windows as well.

Let's get a taste of DNSChef with its most basic monitoring functionality. Execute the following command as root (required to start a server on port 53):
```
# ./dnschef.py

          _                _          __  
         | | version 0.2  | |        / _| 
       __| |_ __  ___  ___| |__   ___| |_ 
      / _` | '_ \/ __|/ __| '_ \ / _ \  _|
     | (_| | | | \__ \ (__| | | |  __/ |  
      \__,_|_| |_|___/\___|_| |_|\___|_|  
                   iphelix@thesprawl.org

[*] DNSChef started on interface: 127.0.0.1 
[*] Using the following nameservers: 8.8.8.8
[*] No parameters were specified. Running in full proxy mode
```

Without any parameters, DNSChef will run in full proxy mode. This means that all requests will simply be forwarded to an upstream DNS server (8.8.8.8 by default) and returned back to the quering host. For example, let's query an "A" record for a domain and observe results:
```
$ host -t A thesprawl.org
thesprawl.org has address 108.59.3.64
```

DNSChef will print the following log line showing time, source IP address, type of record requested and most importantly which name was queried:
```
[23:54:03] 127.0.0.1: proxying the response of type 'A' for thesprawl.org
```

This mode is useful for simple application monitoring where you need to figure out which domains it uses for its communications.

DNSChef has full support for IPv6 which can be activated using -6 or --ipv6* flags. It works exactly as IPv4 mode with the exception that default listening interface is switched to ::1 and default DNS server is switched to 2001:4860:4860::8888. Here is a sample output:
```
# ./dnschef.py -6
          _                _          __
         | | version 0.2  | |        / _|
       __| |_ __  ___  ___| |__   ___| |_
      / _` | '_ \/ __|/ __| '_ \ / _ \  _|
     | (_| | | | \__ \ (__| | | |  __/ |
      \__,_|_| |_|___/\___|_| |_|\___|_|
                   iphelix@thesprawl.org

[*] Using IPv6 mode.
[*] DNSChef started on interface: ::1
[*] Using the following nameservers: 2001:4860:4860::8888
[*] No parameters were specified. Running in full proxy mode
[00:35:44] ::1: proxying the response of type 'A' for thesprawl.org
[00:35:44] ::1: proxying the response of type 'AAAA' for thesprawl.org
[00:35:44] ::1: proxying the response of type 'MX' for thesprawl.org
```

NOTE: By default, DNSChef creates a UDP listener. You can use TCP instead with the --tcp argument discussed later.


For more documentation see project webpage: http://thesprawl.org/projects/dnschef/
=======
DNSChef
=======

Lightweight DNS proxy written in python
>>>>>>> 46de2a240b763a70b959d0095327ececd864bbfa
=======
 
>>>>>>> 4676516875cb1b9e3987025a41d891729fa284d1
