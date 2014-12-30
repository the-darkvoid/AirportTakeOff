Airport TakeOff
==============

Airport TakeOff is a OS X kext module to inject the required information to use the BCM94352Z with OS X Yosemite.

It uses AppleMergeUSBNub to merge data into `AirPort_Brcm4360`, `AirPort_Brcm4360_Interface` and `IOPCIDevice`.

For the matching IOPCIDevice it merges the following properties:

 * `AAPL,slot-name` **Airport**
 * `revision-id` **03 00 00 00**
 * `subsystem-id` **34 01 00 00**
 * `subsystem-vendor-id` **6b 01 00 00**

For AirPort_Brcm4360:

 * `APChipRev` **3**
 * `APFeatures` **1**
 * `APTAPD` **1**
 * `IOLocale` **Worldwide**
 * `IOVendor` **Apple** _This makes the device appear as Apple Airport Extreme_

For AirPort_Brcm4360_Interface:

 * `IO80211CountryCode` **US** _Change card country code to enable 5ghz channels_
 * `IO80211Locale` **FCC** _Change card locale to enable 5ghz channels_
 * `IOBuiltin` **true**

#### Credits

 * Toleda for [original bcm4352.kext](https://github.com/toleda/wireless_half-mini/tree/master/airport_kext_enabler)
 * Eps for [using AppleUsbMergeNub to inject IOPCIDevice properties](http://www.insanelymac.com/forum/topic/238332-devicemergenub-for-dsm-style-injection/page-3#entry1599569)


