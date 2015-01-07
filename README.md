Airport TakeOff
==============

Airport TakeOff is a OS X kext module to inject the required information to use the BCM94352Z with OS X Yosemite.

It uses AppleMergeUSBNub to merge data into `IOPCIDevice`, `AirPort_Brcm4360` and `AirPort_Brcm4360_Interface`.

Even though [AppleUSBMergeNub](http://www.opensource.apple.com/source/IOUSBFamily/IOUSBFamily-630.4.5/AppleUSBMergeNub/Classes/AppleUSBMergeNub.cpp) is meant to merge properties in IOUSBDevices, it does allow merging into IOPCIDevice also.

Excerpt from AppleUSBMergeNub.cpp:
```cpp
OSDictionary *providerDict = (OSDictionary*)getProperty("IOProviderMergeProperties");
if (providerDict)
{
    //   provider->getPropertyTable()->merge(providerDict);		// merge will verify that this really is a dictionary
    MergeDictionaryIntoProvider( provider, providerDict);
}

return NULL;								// always fail the probe!
```
For the matching Airport_Brcm4360 Airport TakeOff merges the following properties:

 * `IOVendor` **Apple** _This makes the device appear as Apple Airport Extreme_

#### Credits

 * Toleda for [original bcm4352.kext](https://github.com/toleda/wireless_half-mini/tree/master/airport_kext_enabler)
 * Eps for [using AppleUsbMergeNub to inject IOPCIDevice properties](http://www.insanelymac.com/forum/topic/238332-devicemergenub-for-dsm-style-injection/page-3#entry1599569)


