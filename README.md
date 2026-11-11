# piFlight releases

piFlight shows the aircraft flying over your home on a 64×32 LED matrix, run by a Raspberry Pi 3 Model A+.
This repository holds the ready-to-flash SD card images and the signed update files. Download them from
[Releases](../../releases).

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
6. Add your home Wi-Fi on the **Wi-Fi** page. The Pi joins it, and the dashboard is then at
   http://piflight.local.
7. On the **Zone** page, put the pin on your home and choose how far around it to look. In **Settings**, choose
   your weather service (and enter its API key if it needs one).

## Updating
On the dashboard, go to **Software update → Check for update → Install**. The Pi downloads the latest
release from here, installs it, and checks that everything still runs. If it doesn't, the Pi switches back
by itself.

Without internet on the Pi, download the `piflight-update-<version>.pfu` file from a release and use
**Install from a file** on the same card.

Updates are signed: a piFlight device only installs files made with the piFlight release key. Re-flashing
an SD card with a newer image also works, but you then have to set the device up again.

## Privacy and remote access
- **There is no shared or hidden login.** SSH is off, and the Pi's user account has no password until you
  choose one. Nobody else, including the piFlight author, can log in to your device.
- To use SSH yourself: dashboard → **Remote access** (in the top bar). Choose a password, optionally
  add your public key and refuse password logins ("Keys only"). Switch it off again on the same page.
- **Need help?** Use **Download diagnostics** on the same page and send the text file to whoever is helping you.
  It contains versions, temperature, service status and recent logs. Wi-Fi names and passwords, API keys and
  your location are left out, and you can read the whole file before you send it.
- What the Pi connects to on the internet: FlightRadar24 (flight data for your area), the weather provider you
  chose (Open-Meteo by default), time servers (pool.ntp.org, Cloudflare, Google), a ping to 8.8.8.8 / 1.1.1.1
  to check the internet is up, and GitHub, only when you click *Check for update*. No usage data is collected.
  The dashboard page loads its map tiles and two scripts straight into your browser.
