# rename router or switch

Router(config)#hostname my-router ===> my-router(config)#

# return to the device's original hostname

my-router(config)#no hostname

# startup-config -> nvram or flash

# running-config -> ram

# view the current configuration stored in RAM

my-router#show running-config

# any configuration in the running-config that is not saved or transferred to NVRAM will be lost after a power outage or system reload

# save the running configuration

my-router#copy running-config startup-config

or

my-router#copy run start

or

my-router#write memory

or

my-router#wr

# view the configuration saved in NVRAM

my-router#show startup-config

# restart device

my-router#reload

Proceed with reload? [confirm] -> enter

# erase the startup configuration and boot the device with a clean configuration

my-router#write erase

# delete the configuration file from flash

Switch>en

Switch#conf t

Switch(config)#hostname sw1

sw1(config)#^Z

sw1#copy run start

sw1#wr

sw1#show flash:

Directory of flash:/

```
1  -rw-     4670455           <no date>  2960-lanbasek9-mz.150-2.SE4.bin

2  -rw-        1077           <no date>  config.text
```

64016384 bytes total (59344852 bytes free)

sw1#delete config.text
