# NetHack-Patches
Ideas for NetHack that I coded, including new levels and a new starting inventory. 


https://jes.st/compiling-playing-nethack-360-on-ubuntu/ for compiling instructions:

It took me a while to figure out how to actually get nethack v3.6.0 running on Ubuntu, so I’ve shared what I learned for others.

Thanks to Jochen, we can also get this compiling on Debian Jessie.

Get setup
Install the dependencies
sudo apt-get install flex bison build-essential libncurses5-dev checkinstall
Get the source
Extract the source
tar xpvzf nethack-360-src.tgz
Prepare the source
Edit include/unixconf.h
Change /* #define LINUX */ to #define LINUX
Edit sys/unix/hints/linux to be as here.
For Debian Jessie, change the HACKDIR=... line to be HACKDIR=$(PREFIX)/lib/games/$(GAME)dir
If you want to enable Status Hilite’s;
Edit include/config.h
Change /* #define STATUS_VIA_WINDOWPORT */ to #define STATUS_VIA_WINDOWPORT
Change /* #define STATUS_HILITES */ to #define STATUS_HILITES
sh ./sys/unix/setup.sh sys/unix/hints/linux (sets up the Makefiles correctly)
Build & install
make all

sudo checkinstall (will create a package and install it for you)

Hit y to create default docs

Enter nethack 3.6.0 then hit <Enter> twice when prompted

At the options screen, change option 12 to say nethack-common. This avoids accidentally installing any old version from your package manager.

Hit <Enter> to continue

If you see an error ”Some of the files created by the installation are inside the home directory“;

Hit n (it’s just a temporary file), then

Hit y to continue (we do not want those files in our package).

Uninstallation
To uninstall, use your favourite package manager, or sudo dpkg -r nethack.
