# The Ubiquity airView application protocol

Ubiquiti devices like my NanoBridge M5 here include a nifty WLAN 
spectrum analyser, "airView". It is launched as a [JNLP](https://en.wikipedia.org/wiki/Java_Web_Start#Java_Network_Launching_Protocol_.28JNLP.29)
via the Ubiquiti web interface. @alex-eri also presents 
a [method](https://github.com/alex-eri/airview-ssh/blob/master/runairview.sh) 
to launch it over SSH.

I took a packet trace using [Wireshark](https://wireshark.org/) to 
look at the actual protocol used between the JNLP app and the device. 
In contrast to the administrative web interface which uses HTTPS (with 
a self-signed certificate though), the application-layer protocol 
between the spectrum analyser Java app and the device is not encrypted.

Once commanded to start via the web interface, the device listens on 
TCP port 18888 for the JNLP app to connect and request data. The 
protocol proceeds roughly like this (but please see the 
[packet trace](https://github.com/aaaaalbert/funkfeuer-sachen/blob/master/ubiquiti-airview/airview_session.pcapng) 
for details):

The app connects to the device.
> CONNECT: 

The device replies with a comman-separated list of hardware / firmware 
properties (including version numbers and MAC address), and seems to 
initialize the app's understanding of WLAN band names and frequency 
ranges. The format for freq ranges is ``lowerfreq|upperfreq|bandname'', 
fields are separated by ``|'' and records by ``~''.
> > CONFIGURATION: 2,XM.v5.5.6,Tue May 28 17:56:11 EEST 2013,0xe2b5,NanoBridge M5,NanoBridge M5,24A43CD27FA1,NB5,24A43CD27FA1,0,0xe2b5,XM.v5.5.6,Tue May 28 17:56:11 EEST 2013,5725000000|5825000000|5.725-5.825 (U-NII Upper Band)~5150000000|5250000000|5.150-5.250 (U-NII Lower Band)~5250000000|5350000000|5.250-5.350 (U-NII Middle Band)~5470000000|5725000000|5.470-5.725 (U-NII Worldwide)~4900000000|5000000000|4.900-5.000~5000000000|5100000000|5.000-5.100
(...)

Also, the [WLAN channels](https://en.wikipedia.org/wiki/List_of_WLAN_channels#5.C2.A0GHz_.28802.11a.2Fh.2Fj.2Fn.2Fac.29.5B17.5D)
are defined. The format is ``channelnumber|lowerfreq|bandwidth'', again 
field/record separated by ``|'' and ``~''.
> > 180|4900000000|20000000~181|4905000000|20000000~182|4910000000|20000000~183|4915000000|20000000~
(...)

Lastly, units of measurement, unknown data, and the supported frequency 
range in MHz follows:
> > ,,1,dbm,dBm - detected power per carrier,1,-150,4900,6400

The app then specifies which frequency range the device should analyse, 
followed by an acknowledgement by the device:
> REQUEST RANGE: 5725000000,5825000000
> > SCAN RANGE: 5725000000,5825000000

> START SCAN: 
> > RESULT: 0

The app then requests ``frames'' of measurements, and the device replies 
with the frame number, followed by dBm values for every frequency, 
comma-separated:
> GET FRAME: 1613
> > FRAME: 1614,-112,-126,-109,-118,-116,-116,-132,-118,-114,-125,
(...)

Finally, the app may stop the measurement:
> STOP SCAN: 

-----

Now wouldn't it be great to interface this with a browser-based 
spectrum analyser like http://websdr.org's?

