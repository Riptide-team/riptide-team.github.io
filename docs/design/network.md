# Network

## Riptide access point

The Riptide is providing an wifi access point mainly to communicate with the Raspberry Pi at lab or during mission preparation. This access point is generally unavailable when the Riptide is at the sea surface due to attenuation of radio signals by water.

| ssid       | Password   |
|------------|------------|
| `Riptide1` | `Riptide1` |

| Ip Adress          | Device   |
|--------------------|----------|
| `192.168.0.100/24` | Computer |
| `192.168.0.101/24` | Riptide  |

## Tail network card

The `d_fin` of the Riptide is instrumented with a Wifi device. In this way, the Riptide is reachable at the sea surface through this internet interface.

This interface is configured to be connected to the network `RiptideNet` typically provided by an Ubiquity Bullet setup in the trial area.

| ssid         | Password     |
|--------------|--------------|
| `RiptideNet` | `RiptideNet` |

| Ip Adress          | Device   |
|--------------------|----------|
| `192.168.1.100/24` | Computer |
| `192.168.1.101/24` | Riptide  |
| {--`192.168.1.11/24`--} | TBSCrossfire |

## Ip Forwarding

To provide internet access to the Riptide, the following script is usefull. It let Riptide access internet through is wifi interface (wifi access point or tail interface) using the computer's internet access. The Riptide is configured witha a gateway at `192.168.0.100` or `192.168.1.100` depending on the internet device in use. It should then be launched on the computer with internet access on this ip address. 

```bash
_available_interfaces() {
    local cmd
    if [ "${1:-}" = -w ]; then
        cmd="iwconfig"
    elif [ "${1:-}" = -a ]; then
        cmd="ifconfig"
    else
        cmd="ifconfig -a"
    fi
    COMPREPLY=( $( eval $cmd 2>/dev/null | sed -ne 's|^\('$cur'[^[:space:][:punct:]]\{1,\}\).*$|\1|p'))
}

complete -F _available_interfaces ip-forwarding

# NAT
ip-forwarding() {
    sudo sysctl -w net.ipv4.ip_forward=1
    sudo /sbin/iptables -F;
    sudo /sbin/iptables -t nat -F;
    sudo /sbin/iptables -X;
    sudo /sbin/iptables -t nat -X;
    sudo /sbin/iptables -t nat -A POSTROUTING -o $1 -j MASQUERADE;
    sudo /sbin/iptables -A FORWARD -i $1 -o $2 -m state --state RELATED,ESTABLISHED -j ACCEPT;
    sudo /sbin/iptables -A FORWARD -i $2 -j ACCEPT;
}
```

To redirect internet flow from `wlo1` to `enx0` (if `wlo1` is connected to the Riptide and `enx0` is connected to internet) use

```bash
> ip-forwarding enx0 wlo1
```

## Troubleshooting

??? Question "Is the kernel detecting the internet device ?"
    Check there is no error in `dmesg`
    ```bash
    > sudo dmesg
    ...
    [ 1668.672012] usb 1-1.1: New USB device found, idVendor=148f, idProduct=5372, bcdDevice= 1.01                                                                                                                     
    [ 1668.672040] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3                                                                                                                                 
    [ 1668.672056] usb 1-1.1: Product: 802.11 n WLAN                                                                                                                                                                   
    [ 1668.672070] usb 1-1.1: Manufacturer: Ralink                                                                                                                                                                     
    [ 1668.758037] usb 1-1.1: reset high-speed USB device number 7 using xhci_hcd                            
    [ 1668.867767] ieee80211 phy2: rt2x00_set_rt: Info - RT chipset 5392, rev 0223 detected                  
    [ 1668.894218] ieee80211 phy2: rt2x00_set_rf: Info - RF chipset 5372 detected                            
    [ 1668.894544] ieee80211 phy2: Selected rate control algorithm 'minstrel_ht'                             
    [ 1668.967671] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'                                                                                                               
    [ 1668.969027] ieee80211 phy2: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36                                                                                                                
    [ 1669.233122] ieee80211 phy2: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -71                                                  
    [ 1669.257012] usb 1-1.1: USB disconnect, device number 7                                                                                                                                                          
    [ 1669.257327] ieee80211 phy2: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -19                                               
    [ 1669.785094] usb 1-1.1: new full-speed USB device number 8 using xhci_hcd                                                                                                                                        
    [ 1669.865333] usb 1-1.1: device descriptor read/64, error -32
    ...
    ```

    It very common to have corroded usb extension cable causing communication problems with wifi interface (No joke, trust me :sob:). A life-saving product in this case is Contact Cleaner, a spray on the plug and everything should be working again.
    
    !!! Quote "To avoid this corrosion problem, only one solution"
        Stop letting water get into the Riptide's body buddy!

??? Question "Is there a driver error ?"
    The driver is not always installed by default on the Raspberry Pi and depend on the Linux Kernel version which is regularly updated.

    To install the drivers corresponding to the current Linux Kernel version run:

    ```bash
    > sudo apt install linux-modules-extra-$(uname -r)
    ```

    There is also this upgrade-friendly command

    ```bash
    > sudo apt install linux-generic
    ```

    !!! Quote "Note about the latter command"
        It works for now, and it seems to do the same thing as the previous command! Let see if it surive a Kernel upgrade ...:fingers_crossed:

??? Question "Is the internet device available ?"
    To see if the internet device is available run

    ```bash
    > nmcli
    wlan0: connected to Riptide1                        
        "Broadcom BCM43438 combo and Bluetooth Low Energy"                                               
        wifi (brcmfmac), E4:5F:01:5D:F5:94, hw, mtu 1500                                                 
        ip4 default                                 
        inet4 192.168.0.101/24                      
        route4 192.168.0.0/24 metric 600            
        route4 default via 192.168.0.100 metric 600                                                      

    wlan1: connected to RiptideNet                      
            "Ralink RT5372"                             
            wifi (rt2800usb), 9C:EF:D5:FD:B0:BC, hw, mtu 1500                                                
            inet4 192.168.1.101/24                      
            route4 192.168.1.0/24 metric 601            
            route4 default via 192.168.1.100 metric 601                                                      
            inet6 fe80::ac66:5086:1c1a:a60b/64          
            route6 fe80::/64 metric 1024
    ...
    ```

    Here the `wlan1` is available and connected to RiptideNet. If not, there is probably a driver error, a cable issue or maybe too much water inside the Riptide ... :scream: 