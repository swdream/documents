SSLyze 0.13.5
=============

Fast and full-featured SSL scanner for Python 2.7.

Description
-----------

* SSLyze is a Python tool that can analyze the SSL configuration of a server by connecting to it.

* It is designed to be fast and comprehensive, and should help organizations and testers identify mis-configurations affecting their SSL servers.

Why SSLyze
----------

* Multi-processed and multi-threaded scanning: it's very fast.
* Support for all SSL protocols, from SSL 2.0 to TLS 1.2.
* **NEW:** SSLyze can also be used as a library, in order to run scans and process the results directly from Python.
* Performance testing: session resumption and TLS tickets support.
* Security testing: weak cipher suites, insecure renegotiation, CRIME, Heartbleed and more.
* Server certificate validation and revocation checking through OCSP stapling.
* Support for StartTLS handshakes on SMTP, XMPP, LDAP, POP, IMAP, RDP, PostGres and FTP.
* Support for client certificates when scanning servers that perform mutual authentication.
* Scan results can be written to an XML or JSON file for further processing.

Installation
------------

SSLyze can be installed directly via pip:

.. code-block:: console

    # pip install sslyze

Or clone the repository and the fetch the requirements:

.. code-block:: console

    $ git clone https://github.com/nabla-c0d3/sslyze.git
    $ cd sslyze
    $ sudo pip install -r requirements.txt --target ./lib


Usage
-----

The command line tool can be used to scan servers:

.. code-block:: console

    $ sslyze_cli.py --regular server

SSLyze has been tested on the following platforms: Windows 7 (32 and 64 bits), Debian 7 (32 and 64 bits), OS X El
Capitan.

How does it work ?
------------------

SSLyze is all Python code but it uses an
[OpenSSL wrapper written in C called nassl](https://github.com/nabla-c0d3/nassl) which was specifically developed for
allowing SSLyze to access the low-level OpenSSL APIs needed to perform deep SSL testing.

Where do the trust stores come from?
------------------------------------

The Mozilla, Microsoft, Apple and Java trust stores are downloaded using the following tool:
https://github.com/nabla-c0d3/catt/blob/master/sslyze.md .


For more detail, please refer to `here <https://pypi.python.org/pypi/SSLyze>`_.

