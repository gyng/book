# Disabling 2.4GHz on ASUS PCE-AC66 in Windows

I've been having issues with the card autoconnecting to the 2.4GHz network and having awful speeds in general. It's time for a replacement, but until then, I'm going to live with it.

The super-old utility can't force a connection to the 5GHz network.

Disabling the 802.11g/b band in the drivers seemed to help.

1. Device manager
2. Network adaptesr
3. ASUS PCE-AC66
4. Properties
5. Advanced > Disable bands
6. Value: Disable 802.11g/b
