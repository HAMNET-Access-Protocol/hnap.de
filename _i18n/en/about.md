# About

The initial HAMNET Access Protocol has been developed by Lukas Ostendorf during
his master thesis at Rohde & Schwarz Munich in 2019/2020.  
A first implementation is available for the ADALM Pluto SDR:
[HNAP4PlutoSDR](https://github.com/HAMNET-Access-Protocol/HNAP4PlutoSDR).

Available material for further reading:

* [Master thesis by Lukas Ostendorf: Design of a Radio Communications Protocol for
HAMNET Access in the 70cm Amateur Radio Band](/assets/pdf/Masterthesis - Design of a Radio Communications Protocol for HAMNET Access in the 70cm Amateur Radio Band.pdf)
* [Presentation: HNAP - The HAMNET Access Protocol](/assets/pdf/Presentation - HNAP4PlutoSDR.pdf)
* [Article about HNAP](/assets/pdf/Article - HNAP4PlutoSDR - HAMNET on 70cm with the PlutoSDR.pdf) ([deutsch](/assets/pdf/Artikel - HNAP4PlutoSDR - HAMNET auf 70cm mit dem PlutoSDR.pdf))
* [Talk about HNAP at the Software Defined Radio Academy 2020](https://www.youtube.com/watch?v=AMATF5XX71o&t=152)

# Background

As of today the end user RF access to the HAMNET is often limited to
line-of-sight conditions due to the use of wideband signals on the 13-cm- and
above amateur radio bands. In Germany, the use of a 200 kHz wide duplex radio
channel in the 70-cm band (439.700 Downlink / 434.900 Uplink) allows to
overcome this issue, however no commercial off-the-shelf (COTS) solution is
available at a reasonable price tag.

The open source implementation of the HAMNET Access Protocol for the ADALM
Pluto SDR (HNAP4PlutoSDR) allows to interface the end user's PC or network
(using an USB-to-LAN dongle) to RF:

![HNAP Setup](/assets/img/about/setup.jpg)

The community is invited to experiment and
to push the project to a real-world deployable solution for end user HAMNET
access on 70-cm.

# Status

We are able to transfer ~350 kbit/s in the lab from one ADALM Pluto SDR to
another. Connectivity to several clients is possible even with different
modulation and coding schemes.

# Agenda

* Implementation of a single carrier solution
* Longer distance tests with amplifiers (PTT already available through GPIO)
* Deployment of a real-world HAMNET-70 access point