1. Clone the repo into some directory (~/rtl-433-openwrt for example)
2. To get the latest rtl-433 sources change PKG_SOURCE_VERSION
   in the Makefile
3. Adding src-link into the feeds.conf has never worked for me so
   I'm creting a symbolic link manually:

      ```bash
      cd package/feeds/packages/
      ln -s ../../../../rtl-433-openwrt/utils/rtl-433/ rtl-433
      ```

4. Compile

      ```bash
      make package/feeds/packages/rtl-433/compile V=99
      ```

5. Create the package in *bin/ar71xx/packages/packages/*

      ```
      make package/feeds/packages/rtl-433/install V=99
      ```

6. Copy created ipk package to the router and install it with:

      ```bash
      opkg install ./rtl-433*.ipk
      ```

      It will complain about missing *librtlsdr*. So install the library from the repository or compile and install it yourself before installing rtl-433 package.

7. rtl-sdr package could also be compiled or installed from the repository

      ```
      # Compile and create an ipk package
      make package/feeds/packages/rtl-sdr/compile V=99
      make package/feeds/packages/rtl-sdr/install V=99

      # Install from the repository
      # It will automatically install librtlsdr library
      opkg update
      opkg install rtl-sdr
      ```


