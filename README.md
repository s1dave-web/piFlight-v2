# piFlight releases

piFlight shows the aircraft flying over your home on a 64×32 LED matrix, run by a Raspberry Pi 3 Model A+.
This repository holds the ready-to-flash SD card images and the signed update files. Download them from
[Releases](https://github.com/s1dave-web/piFlight-v2/releases).

## New device: flash the SD card
1. Download `piflight-<version>-<date>.img.xz` from the latest release. To check the download, compare its
   SHA-256 with the `.sha256` file.
2. Flash it with [Raspberry Pi Imager](https://www.raspberrypi.com/software/): *Choose OS → Use custom*, pick
   the `.img.xz` file and choose the card. When Imager asks about **OS customisation, choose "No"**, because
   piFlight sets itself up.
3. Put the card in the Pi and switch it on. The first start takes about 2 minutes and restarts once.
4. The matrix shows a QR code. Scan it, or join the Wi-Fi network **PiFlight-Setup** (password `PiFlight`).
5. Open http://192.168.4.1 and log in with the password shown on the login page. You will be asked to
   change it.
6. Add your home Wi-Fi on the **Network** page. The Pi joins it, and the dashboard is then at
   http://piflight.local.
7. In **Settings**, enter your location, plus API keys if your weather provider needs one.

## Updating
On the dashboard, go to **Software Update → Check for update → Install**. The Pi downloads the latest
release from here, installs it, and checks that everything still runs. If it doesn't, the Pi switches back
by itself.

Without internet on the Pi, download the `piflight-update-<version>.pfu` file from a release and use
**Upload and install** on the same page.

Updates are signed: a piFlight device only installs files made with the piFlight release key. Re-flashing
an SD card with a newer image also works, but you then have to set the device up again.
