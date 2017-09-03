1. Clone the repo into some directory (~/rtl-433-openwrt for example)
2. to get the latest rtl-433 sources change PKG_SOURCE_VERSION
   in the Makefile
3. Adding src-link into the feeds.conf doesn't work for me so
   I'm creting a symbolic link manually:
   cd package/feeds/packages/
   ln -s ../../../../rtl-433-openwrt/utils/rtl-433/ rtl-433
4. Compile
   make package/feeds/packages/rtl-433/compile V=99

   It might be also necessary to compile (and maybe also intall)
   the rtl-sdr package first:

   make package/feeds/packages/rtl-sdr/compile V=99
   make package/feeds/packages/rtl-sdr/install V=99

5. Create the package in bin/ar71xx/packages/packages/
   make package/feeds/packages/rtl-433/install V=99
6. Copy created ipk package to the router and install it with:
   opkg install ./rtl-433*.ipk
   ( rtl-sdr package should be installed first )

