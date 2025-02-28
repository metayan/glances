===============================
Glances - An eye on your system
===============================

.. image:: https://img.shields.io/pypi/v/glances.svg
    :target: https://pypi.python.org/pypi/Glances

.. image:: https://img.shields.io/github/stars/nicolargo/glances.svg
    :target: https://github.com/nicolargo/glances/
    :alt: Github stars

.. image:: https://img.shields.io/docker/pulls/nicolargo/glances
    :target: https://hub.docker.com/r/nicolargo/glances/
    :alt: Docker pull

.. image:: https://pepy.tech/badge/glances/month
    :target: https://pepy.tech/project/glances
    :alt: Pypi downloads

.. image:: https://github.com/nicolargo/glances/actions/workflows/test.yml/badge.svg
    :target: https://github.com/nicolargo/glances/actions
    :alt: Linux tests (GitHub Actions)

.. image:: https://img.shields.io/appveyor/ci/nicolargo/glances/master.svg?maxAge=3600&label=Windows
    :target: https://ci.appveyor.com/project/nicolargo/glances
    :alt: Windows tests (Appveyor)

.. image:: https://scrutinizer-ci.com/g/nicolargo/glances/badges/quality-score.png?b=develop
    :target: https://scrutinizer-ci.com/g/nicolargo/glances/?branch=develop

.. image:: https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&link=https://github.com/sponsors/nicolargo
    :target: https://github.com/sponsors/nicolargo

.. image:: https://img.shields.io/twitter/url/https/twitter.com/cloudposse.svg?style=social&label=Follow%20%40nicolargo
    :target: https://twitter.com/nicolargo

Summary
=======

**Glances** is a cross-platform monitoring tool which aims to present a
large amount of monitoring information through a curses or Web
based interface. The information dynamically adapts depending on the
size of the user interface.

.. image:: https://raw.githubusercontent.com/nicolargo/glances/develop/docs/_static/glances-summary.png

It can also work in client/server mode. Remote monitoring could be done
via terminal, Web interface or API (XML-RPC and RESTful). Stats can also
be exported to files or external time/value databases.

.. image:: https://raw.githubusercontent.com/nicolargo/glances/develop/docs/_static/glances-responsive-webdesign.png

Glances is written in Python and uses libraries to grab information from
your system. It is based on an open architecture where developers can
add new plugins or exports modules.

Requirements
============

- ``python>=2.7`` or ``python>=3.4``
- ``psutil>=5.3.0`` (better with latest version)
- ``defusedxml`` (in order to monkey patch xmlrpc)
- ``future`` (for Python 2 support)

*Note for Python 2.6 users*

Glances no longer supports Python 2.6. Please upgrade
to a minimum Python version of 2.7/3.4+ or downgrade to Glances 2.6.2 (last version
with Python 2.6 support).

*Deprecation warning note for Python 2.x users*

Glances version 4.0 will no longer supports Python 2.x.

Optional dependencies:

- ``bernhard`` (for the Riemann export module)
- ``bottle`` (for Web server mode)
- ``cassandra-driver`` (for the Cassandra export module)
- ``chevron`` (for the action script feature)
- ``couchdb`` (for the CouchDB export module)
- ``docker`` (for the Docker monitoring support) [Linux/macOS-only]
- ``elasticsearch`` (for the Elastic Search export module)
- ``graphitesender`` (For the Graphite export module)
- ``hddtemp`` (for HDD temperature monitoring support) [Linux-only]
- ``influxdb`` (for the InfluxDB version 1 export module)
- ``influxdb-client``  (for the InfluxDB version 2 export module) [Only for Python >= 3.6]
- ``kafka-python`` (for the Kafka export module)
- ``netifaces`` (for the IP plugin)
- ``py3nvml`` (for the GPU plugin) [Only for Python 3]
- ``pika`` (for the RabbitMQ/ActiveMQ export module)
- ``potsdb`` (for the OpenTSDB export module)
- ``prometheus_client`` (for the Prometheus export module)
- ``py-cpuinfo`` (for the Quicklook CPU info module)
- ``pygal`` (for the graph export module)
- ``pymdstat`` (for RAID support) [Linux-only]
- ``pysnmp`` (for SNMP support)
- ``pySMART.smartx`` (for HDD Smart support) [Linux-only]
- ``pyzmq`` (for the ZeroMQ export module)
- ``requests`` (for the Ports, Cloud plugins and RESTful export module)
- ``scandir`` (for the Folders plugin) [Only for Python < 3.5]
- ``sparklines`` (for the Quick Plugin sparklines option)
- ``statsd`` (for the StatsD export module)
- ``wifi`` (for the wifi plugin) [Linux-only]
- ``zeroconf`` (for the autodiscover mode)

Installation
============

There are several methods to test/install Glances on your system. Choose your weapon!

PyPI: The standard way
----------------------

Glances is on ``PyPI``. By using PyPI, you will be using the latest
stable version.

To install Glances, simply use ``pip``:

.. code-block:: console

    pip install --user glances

*Note*: Python headers are required to install `psutil`_, a Glances
dependency. For example, on Debian/Ubuntu you need to install first
the *python-dev* package (*python-devel* on Fedora/CentOS/RHEL).
For Windows, just install psutil from the binary installation file.

*Note 2 (for the Wifi plugin)*: If you want to use the Wifi plugin, you need
to install the *wireless-tools* package on your system.

You can also install the following libraries in order to use optional
features (like the Web interface, exports modules...):

.. code-block:: console

    pip install --user 'glances[action,browser,cloud,cpuinfo,docker,export,folders,gpu,graph,ip,raid,snmp,web,wifi]'

To upgrade Glances to the latest version:

.. code-block:: console

    pip install --user --upgrade glances
    pip install --user --upgrade glances[...]

If you need to install Glances in a specific user location, use:

.. code-block:: console

    export PYTHONUSERBASE=~/mylocalpath
    pip install --user glances

If you are administrator and want to install Glances for all users:

.. code-block:: console

    sudo pip install glances

The current develop branch is also published to the test.pypi.org package index.
If you want to test the develop version, enter:

.. code-block:: console

    pip install --user -i https://test.pypi.org/simple/ Glances


Glances Auto Install script: the easy way
-----------------------------------------

To install both dependencies and the latest Glances production ready version
(aka *master* branch), just enter the following command line:

.. code-block:: console

    curl -L https://bit.ly/glances | /bin/bash

or

.. code-block:: console

    wget -O- https://bit.ly/glances | /bin/bash

*Note*: This is only supported on some GNU/Linux distributions and Mac OS X.
If you want to support other distributions, please contribute to `glancesautoinstall`_.

Docker: the fun way
-------------------

Glances containers are availables. You can use it to monitor your
server and all your other containers!

Get the Glances container:

.. code-block:: console

    docker pull nicolargo/glances:<version>

Available versions on the Docker Hub repository:

- *nicolargo/glances:latest* for a basic Debian Glances image version with minimal dependencies
- *nicolargo/glances:alpine-latest* for a basic Alpine Glances image version with minimal dependencies
- *nicolargo/glances:latest-full* for a full Debian Glances image version with all dependencies
- *nicolargo/glances:alpine-latest-full* for a full Alpine Glances image version with all dependencies

You can also specify a version by replacing latest by 3.2.3 (for example).

Run last version of Glances container in *console mode*:

.. code-block:: console

    docker run --rm -v /var/run/docker.sock:/var/run/docker.sock:ro --pid host --network host -it nicolargo/glances:latest-full

Additionally, if you want to use your own glances.conf file, you can
create your own Dockerfile:

.. code-block:: console

    FROM nicolargo/glances:latest
    COPY glances.conf /glances/conf/glances.conf
    CMD python -m glances -C /glances/conf/glances.conf $GLANCES_OPT

Alternatively, you can specify something along the same lines with
docker run options:

.. code-block:: console

    docker run -v `pwd`/glances.conf:/glances/conf/glances.conf -v /var/run/docker.sock:/var/run/docker.sock:ro --pid host -it nicolargo/glances:latest-full

Where \`pwd\`/glances.conf is a local directory containing your glances.conf file.

Run the container in *Web server mode* (notice the `GLANCES_OPT` environment
variable setting parameters for the glances startup command):

.. code-block:: console

    docker run -d --restart="always" -p 61208-61209:61208-61209 -e GLANCES_OPT="-w" -v /var/run/docker.sock:/var/run/docker.sock:ro --pid host nicolargo/glances:latest-full

GNU/Linux
---------

`Glances` is available on many Linux distributions, so you should be
able to install it using your favorite package manager. Be aware that
when you use this method the operating system `package`_ for `Glances`
may not be the latest version.

FreeBSD
-------

To install the binary package:

.. code-block:: console

    # pkg install py38-glances

To install Glances from ports:

.. code-block:: console

    # cd /usr/ports/sysutils/py-glances/
    # make install clean

macOS
-----

If you do not want to use the glancesautoinstall script, follow this procedure.

macOS users can install Glances using ``Homebrew`` or ``MacPorts``.

Homebrew
````````

.. code-block:: console

    $ brew install glances

MacPorts
````````

.. code-block:: console

    $ sudo port install glances

Windows
-------

Install `Python`_ for Windows (Python 2.7.9+ and 3.4+ ship with pip) and
then run the following command:

.. code-block:: console

    $ pip install glances

Android
-------

You need a rooted device and the `Termux`_ application (available on the
Google Play Store).

Start Termux on your device and enter:

.. code-block:: console

    $ apt update
    $ apt upgrade
    $ apt install clang python
    $ pip install bottle
    $ pip install glances

And start Glances:

.. code-block:: console

    $ glances

You can also run Glances in server mode (-s or -w) in order to remotely
monitor your Android device.

Source
------

To install Glances from source:

.. code-block:: console

    $ wget https://github.com/nicolargo/glances/archive/vX.Y.tar.gz -O - | tar xz
    $ cd glances-*
    # python setup.py install

*Note*: Python headers are required to install psutil.

Chef
----

An awesome ``Chef`` cookbook is available to monitor your infrastructure:
https://supermarket.chef.io/cookbooks/glances (thanks to Antoine Rouyer)

Puppet
------

You can install Glances using ``Puppet``: https://github.com/rverchere/puppet-glances

Ansible
-------

A Glances ``Ansible`` role is available: https://galaxy.ansible.com/zaxos/glances-ansible-role/

Usage
=====

For the standalone mode, just run:

.. code-block:: console

    $ glances

For the Web server mode, run:

.. code-block:: console

    $ glances -w

and enter the URL ``http://<ip>:61208`` in your favorite web browser.

For the client/server mode, run:

.. code-block:: console

    $ glances -s

on the server side and run:

.. code-block:: console

    $ glances -c <ip>

on the client one.

You can also detect and display all Glances servers available on your
network or defined in the configuration file:

.. code-block:: console

    $ glances --browser

You can also display raw stats on stdout:

.. code-block:: console

    $ glances --stdout cpu.user,mem.used,load
    cpu.user: 30.7
    mem.used: 3278204928
    load: {'cpucore': 4, 'min1': 0.21, 'min5': 0.4, 'min15': 0.27}
    cpu.user: 3.4
    mem.used: 3275251712
    load: {'cpucore': 4, 'min1': 0.19, 'min5': 0.39, 'min15': 0.27}
    ...

or in a CSV format thanks to the stdout-csv option:

.. code-block:: console

    $ glances --stdout-csv now,cpu.user,mem.used,load
    now,cpu.user,mem.used,load.cpucore,load.min1,load.min5,load.min15
    2018-12-08 22:04:20 CEST,7.3,5948149760,4,1.04,0.99,1.04
    2018-12-08 22:04:23 CEST,5.4,5949136896,4,1.04,0.99,1.04
    ...

and RTFM, always.

Documentation
=============

For complete documentation have a look at the readthedocs_ website.

If you have any question (after RTFM!), please post it on the official Q&A `forum`_.

Gateway to other services
=========================

Glances can export stats to: ``CSV`` file, ``JSON`` file, ``InfluxDB``, ``Cassandra``, ``CouchDB``,
``OpenTSDB``, ``Prometheus``, ``StatsD``, ``ElasticSearch``, ``RabbitMQ/ActiveMQ``,
``ZeroMQ``, ``Kafka``, ``Riemann``, ``Graphite`` and ``RESTful`` server.

How to contribute ?
===================

If you want to contribute to the Glances project, read this `wiki`_ page.

There is also a chat dedicated to the Glances developers:

.. image:: https://badges.gitter.im/Join%20Chat.svg
        :target: https://gitter.im/nicolargo/glances?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge

Donation
========

If this project help you, you can give me a tip ;)

See the sponsors_ page.

Author
======

Nicolas Hennion (@nicolargo) <nicolas@nicolargo.com>

.. image:: https://img.shields.io/twitter/url/https/twitter.com/cloudposse.svg?style=social&label=Follow%20%40nicolargo
    :target: https://twitter.com/nicolargo

License
=======

Glances is distributed under the LGPL version 3 license. See ``COPYING`` for more details.

.. _psutil: https://github.com/giampaolo/psutil
.. _glancesautoinstall: https://github.com/nicolargo/glancesautoinstall
.. _Python: https://www.python.org/getit/
.. _Termux: https://play.google.com/store/apps/details?id=com.termux
.. _readthedocs: https://glances.readthedocs.io/
.. _forum: https://groups.google.com/forum/?hl=en#!forum/glances-users
.. _wiki: https://github.com/nicolargo/glances/wiki/How-to-contribute-to-Glances-%3F
.. _package: https://repology.org/metapackage/glances/packages
.. _sponsors: https://github.com/sponsors/nicolargo
