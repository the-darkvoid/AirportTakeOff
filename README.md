Airport TakeOff
==============

Airport TakeOff is a OS X kext module to inject the required information to use the BCM94352Z with OS X Yosemite.

It uses AppleMergeUSBNub to merge data into `IOPCIDevice`, `AirPort_Brcm4360` and `AirPort_Brcm4360_Interface`.

Even though [AppleUSBMergeNub](http://www.opensource.apple.com/source/IOUSBFamily/IOUSBFamily-630.4.5/AppleUSBMergeNub/Classes/AppleUSBMergeNub.cpp) is meant to merge properties in IOUSBDevices, it does allow merging into IOPCIDevice also.

Excerpt from AppleUSBMergeNub.cpp:

    OSDictionary *providerDict = (OSDictionary*)getProperty("IOProviderMergeProperties");
    if (providerDict)
    {
        //   provider->getPropertyTable()->merge(providerDict);		// merge will verify that this really is a dictionary
        MergeDictionaryIntoProvider( provider, providerDict);
    }
    
    return NULL;								// always fail the probe!

For the matching IOPCIDevice Airport TakeOff merges the following properties:

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


