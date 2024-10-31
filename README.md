# My octoprint main page view
![image](https://github.com/user-attachments/assets/41ad190c-500d-4f96-941d-c1103b03fa24)

# For installation [continue on the oficial website](https://octoprint.org/download/) or use intractions below

<h1 id="octopi">OctoPi</h1>

<p><a href="https://github.com/guysoft">Guy Sheffer</a> maintains <a href="https://github.com/guysoft/OctoPi">“OctoPi”</a>,
a <a href="https://www.raspbian.org/">Raspbian (and thus Debian) based</a> SD card image for the Raspberry Pi
that already includes OctoPrint plus everything you need to run it:</p>

<ul>
  <li>OctoPrint plus its dependencies</li>
  <li><a href="https://github.com/jacksonliam/mjpg-streamer">MJPG-Streamer</a>
for live viewing of prints and timelapse video creation, compatible with various
USB webcams and the Raspberry Pi camera</li>
</ul>

<p><strong>Recommended hardware: Raspberry Pi 3B, 3B+, 4B or Zero 2. Expect print artifacts and long loading times with other 
options, especially when adding a webcam or installing third party plugins.</strong> Setups not using
recommended hardware are not officially supported.</p>

<p>Please note that the <strong>Raspberry Pi Zero and Zero W are not recommended explicitly</strong> since severe performance 
issues were observed, caused by the WiFi interface when bandwidth is utilized (e.g. the webcam is streamed), negatively 
impacting printing quality. <a href="https://github.com/guysoft/OctoPi/issues/318#issuecomment-284762963">See also here</a>. The Zero 2
however <em>is</em> recommended.</p>

<h2 id="installing-octopi">Installing OctoPi</h2>

<p>OctoPi is available through the <a href="https://www.raspberrypi.org/software/">Raspberry Pi Imager</a>, which you can use to download and setup OctoPi. You can install it yourself, or alternatively simply buy one of the available</p>

<h3 id="installing-octopi-using-the-raspberry-pi-imager">Installing OctoPi using the Raspberry Pi Imager</h3>

<blockquote>
  <p>🤚 <strong>Before you begin</strong></p>

  <p>Read and follow these instructions <strong>precisely</strong>.</p>
</blockquote>

<ol>
  <li>
    <p>If you haven’t already, <strong>download and install <a href="https://raspberrypi.org/software">Raspberry Pi Imager</a></strong> on your computer</p>
  </li>
  <li>
    <p><strong>Find the OctoPi image</strong> under “Choose OS”, by selecting “Other Specific Purpose OS” &gt; “3D printing” &gt; “OctoPi” and then the “stable” version.</p>
  </li>
  <li>
    <p><strong>Open advanced options</strong> by clicking on the button with the gear, or by using the keyboard shortcut <code>ctrl</code>+<code>shift</code>+<code>x</code> and then:</p>

  <ul>
    <li>
      <p><strong>Configure your wifi options</strong>: Set your SSID, password and WiFi country.</p>
    </li>
    <li>
      <p><strong>Change the <em>system</em> password</strong> in “Set username and password” by entering a new password to use for the system user “pi”. This is <em>not</em> the password you’ll use for logging into
OctoPrint but one that you’ll have to use to log into your Pi via SSH should you ever need to.</p>
      </li>
      <li>
        <p>Optionally: Change the configured timezone in “Set locale settings”</p>
      </li>
      <li>
        <p>Optionally: Change the hostname in “Set hostname”</p>
      </li>
    </ul>

  <p><img src="https://github.com/user-attachments/assets/c40d7407-13b1-43fd-aa2c-ea269bab3561" alt="Advanced options, showing the &quot;Set username and password&quot; box ticked and a new password set, and showing the &quot;Configure wireless LAN&quot; box ticked and an SSID and Password set."></p>
  </li>
  <li>
    <p><strong>Install the image to your SD card</strong>, then plug everything in to your Raspberry Pi and boot it up. <strong>Do not format the SD card after installing, even if prompted to do so.</strong> This will break the installation and you will have to start over!</p>
  </li>
  <li>
    <p><strong>Access OctoPrint from your browser</strong> via <code class="language-plaintext highlighter-rouge">http://octopi.local</code> or the hostname you 
chose (<a href="https://learn.adafruit.com/bonjour-zeroconf-networking-for-windows-and-linux/overview">if your computer supports bonjour</a>) 
or <code class="language-plaintext highlighter-rouge">http://&lt;your pi's ip address&gt;</code>. <code class="language-plaintext highlighter-rouge">https</code> is available too, with a self-signed certificate 
(which means your browser will warn you about it being invalid - it isn’t, it’s just not recognized by your browser).</p>
  </li>
</ol>

<p>Please also refer to <a href="https://github.com/guysoft/OctoPi">OctoPi’s README</a>, especially the <a href="https://github.com/guysoft/OctoPi#how-to-use-it">“How to use it” section</a>.</p>

<h3 id="alternative-initial-setup">Alternative Initial Setup</h3>

<p>If you decide against using the Raspberry Pi Imager, here are some alternative steps to get started:</p>

<ol>
  <li>
    <p><strong>Flash the image to your SD card</strong> through whatever alternative means you’ve chosen.</p>
  </li>
  <li>
    <p>With the SD card still attached to your computer, set up the Wifi connection using the <code class="language-plaintext highlighter-rouge">octopi-wpa-supplicant.txt</code> file
on the root of the installed card when using it like a thumb drive. 
<strong>Important: Do not use WordPad (Windows) or TextEdit (MacOS X)</strong>  for this, those editors are known to mangle
the file, making configuration fail. Use something like Notepad++, Atom or VSCode instead or at the very 
least heed the warnings in the file. If your computer doesn’t see the card right away after flashing, try
ejecting and inserting it again. <strong>Do not format the SD card after installing, even if prompted to do so.</strong> This will break the installation and you will have to start over!</p>

  <p>Please also refer take a look at the <a href="https://faq.octoprint.org/wifi-setup">full WiFi setup guide in the FAQ</a> that also includes troubleshooting tips.</p>
  </li>
  <li>
    <p><strong>Plug everything into your Raspberry Pi and boot it up</strong></p>
  </li>
  <li>
    <p><strong>Log into your Pi via SSH</strong> (it is located at <code class="language-plaintext highlighter-rouge">octopi.local</code>
<a href="https://learn.adafruit.com/bonjour-zeroconf-networking-for-windows-and-linux/overview">if your computer supports bonjour</a>
or the IP address assigned by your router), default username is <code class="language-plaintext highlighter-rouge">pi</code>, default password is <code class="language-plaintext highlighter-rouge">raspberry</code>.
Run <code class="language-plaintext highlighter-rouge">sudo raspi-config</code>. Once that is open:</p>

  <ol>
    <li>Change the password via “Change User Password”</li>
    <li>Optionally: Change the configured timezone via “Localization Options” &gt; “Timezone”.</li>
    <li>Optionally: Change the hostname via “Network Options” &gt; “Hostname”. Your OctoPi instance will then no longer be reachable under <code class="language-plaintext highlighter-rouge">octopi.local</code> but rather the hostname you chose postfixed with <code class="language-plaintext highlighter-rouge">.local</code>, so keep that in mind.</li>
  </ol>

  <p>You can navigate in the menus using the arrow keys and <key>Enter</key>. To switch to selecting the buttons at the bottom use <key>Tab</key>.</p>

  <p><strong>You do not need to expand the filesystem</strong>, current versions of OctoPi do this automatically.</p>

  <p><strong>You also do not need to manually enable the RaspiCam</strong> if you have one, that is already taken care of on the image as well.</p>
  </li>
  <li>
    <p><strong>Access OctoPrint</strong> through <code class="language-plaintext highlighter-rouge">http://octopi.local</code> (<a href="https://learn.adafruit.com/bonjour-zeroconf-networking-for-windows-and-linux/overview">if your computer supports bonjour</a>) 
or <code class="language-plaintext highlighter-rouge">http://&lt;your pi's ip address&gt;</code>. <code class="language-plaintext highlighter-rouge">https</code> is available too, with a self-signed certificate 
(which means your browser will warn you about it being invalid - it isn’t, it’s just not recognized by your browser).</p>
  </li>
</ol>

<p>Please also refer to <a href="https://github.com/guysoft/OctoPi">OctoPi’s README</a>, especially the <a href="https://github.com/guysoft/OctoPi#how-to-use-it">“How to use it” section</a>.</p>

<h2 id="image-downloads">Image Downloads</h2>

<p>Raspberry Pi Imager will download the latest version of OctoPi for you, but if you want to download the images 
yourself you can do so here.</p>

<h3 id="stable-octopi">Stable OctoPi</h3>

<div class="text-center">
    <a class="btn btn-large btn-primary btn-block" href="https://github.com/OctoPrint/OctoPi-UpToDate/releases/download/1.0.0-1.10.2-20240618085851/octopi-1.0.0-1.10.2-20240618085851.zip" data-analytics="&quot;Download Click&quot;, { &quot;props&quot;: { &quot;target&quot;: &quot;latest&quot;} }">
      OctoPi&nbsp;1.0.0 &amp; OctoPrint&nbsp;1.10.2
    </a>
    <small>SHA256: <code>756a7de8530777f40cd26d07d210ab1680fa49ef0ad795768a55000516c4018b</code></small><br>
    <small><strong>Raspberry Pi 3B, 3B+, 4B or Zero 2 strongly recommended, Raspberry Pi Zero/Zero W not officially supported, Raspberry Pi 5 currently unsupported!</strong></small><br>
    <small>Image compatible with Raspberry Pi 1A, 1A+, 1B, 1B+, 2B, 3A+, 3B, 3B+, 4B 1/2/4/8GB, Zero, Zero W, Zero 2 and 400.</small><br>
</div>

<h3 id="stable-octopi-with-new-camera-stack">Stable OctoPi with New Camera Stack</h3>

<p>The same OctoPi image with the <strong><a href="/blog/2023/05/24/a-new-camera-stack-for-octopi/">new camera stack</a></strong> can be found here:</p>

<div class="text-center">
    <a class="btn btn-large btn-block" href="https://github.com/OctoPrint/OctoPi-UpToDate/releases/download/1.0.0-1.10.2-20240618101629/octopi-1.0.0-1.10.2-20240618101629.zip" data-analytics="&quot;Download Click&quot;, { &quot;props&quot;: { &quot;target&quot;: &quot;latest_cam&quot;} }">
      OctoPi&nbsp;1.0.0 &amp; OctoPrint&nbsp;1.10.2 (new&nbsp;camera&nbsp;stack)
    </a>
    <small>SHA256: <code>87abc4cf58356d31a3c58bf8fdad8e1f22320cc4a82984d24d69f1eee76746a2</code></small><br>
    <small><strong>Raspberry Pi 3B, 3B+, 4B or Zero 2 strongly recommended, Raspberry Pi Zero/Zero W not officially supported, Raspberry Pi 5 currently unsupported!</strong></small><br>
    <small>Image compatible with Raspberry Pi 1A, 1A+, 1B, 1B+, 2B, 3A+, 3B, 3B+, 4B 1/2/4/8GB, Zero, Zero W, Zero 2 and 400.</small><br>
</div>

<h3 id="octopi-nightlies">OctoPi Nightlies</h3>

<p>You can also get the <a href="https://unofficialpi.org/Distros/OctoPi/nightly/">32bit nightlies here</a> or the <a href="https://unofficialpi.org/Distros/OctoPi/nightly-arm64/">64bit nightlies here</a>.</p>

<h2 id="further-resources">Further resources</h2>

<ul>
  <li>For customizing OctoPi, take a look at <a href="https://github.com/OctoPrint/CustoPiZer">CustoPiZer</a>.</li>
  <li>Scripts to build the image yourself can be found in <a href="https://github.com/guysoft/OctoPi">OctoPi’s Github repository</a>.</li>
</ul>

<hr>

### 3th Party Plugins
- [Camera Settings](https://plugins.octoprint.org/plugins/camerasettings/)
- [Exclude Region](https://plugins.octoprint.org/plugins/excluderegion/)
- [Navbar Clock](https://plugins.octoprint.org/plugins/navbarclock/)
- [OctoEverywhere!](https://plugins.octoprint.org/plugins/octoeverywhere/)
- [Octolapse](https://plugins.octoprint.org/plugins/octolapse/)
- [PrettyGCode](https://plugins.octoprint.org/plugins/prettygcode/)
- [PrintTimeGenius Plugin](https://plugins.octoprint.org/plugins/PrintTimeGenius/)
- [Slicer Thumbnails](https://plugins.octoprint.org/plugins/prusaslicerthumbnails/)
- [Tabinfo Plugin](https://plugins.octoprint.org/plugins/tabinfo/)
- [Themeify](https://plugins.octoprint.org/plugins/themeify/)
- [TouchUI](https://plugins.octoprint.org/plugins/touchui/)
- [WiFi Status](https://plugins.octoprint.org/plugins/wifistatus/)
