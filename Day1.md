# **SYSTEM**

## **1.1. Network Diagram**

## **1.2. Internet service provider (ISP)**

* ### 3BB
  *  General Configuration
  
    | Public IP | Dynamic |
    | :------ | :----------- |
    | Host IP Address   | 192.168.20.254 |
    | Host Subnet Mask   | 255.255.255.0 |

    * DHCP configuration
  
    | Start IP Address | 192.168.20.40 |
    | :------ | :----------- |
    | End IP Address  | 192.168.20.240 |

* ### AIS
  *  General Configuration
 
    | Public IP | Dynamic |
    | :------ | :----------- |
    | Host IP Address   | 192.168.10.254 |
    | Host Subnet Mask   | 255.255.255.0 |

    * DHCP configuration
  
    | Start IP Address | 192.168.10.40 |
    | :------ | :----------- |
    | End IP Address  | 192.168.10.240 |

* ### Phone system
  *  DSG VoIP Diagram
     - Thailand <br> +66 52 072 092 <br> [052072092.png](http://dev.nodeca.com) <br> EX Receiver: 100 <br>

     - Hong Kong <br> +852 801 4532 <br> [85280145632.png](http://dev.nodeca.)<br> EX Receiver: 103 <br> <br> +852 3001 6345 <br>EX Receiver: 105 <br>

     - Australia <br> +612 80730593 (English) <br> [61280730593.png](http://dev.nodeca.com) <br> EX Receiver: 101 <br> <br> +612 88800304 (Tagalog)<br> [61288800304.png](http://dev.nodeca.com) <br>EX Receiver: 102 <br> <br> +653 159 1815 (English)<br> [6531591815.png](http://dev.nodeca.com) <br>EX Receiver: 101 <br>

     - Singapore <br> +653 159 1815 <br> [653 159 1815.png](http://dev.nodeca.com) <br> EX Receiver: 104 <br>

  *  DSG VoIP Information

        **VoIP Provider:** VoIP Thailand

        **Device:** Yealink (DHCP IP Configured)

        **VoIP Software:** 3CX
\
\
        **How to install softphone (VoIP)**
     - To download the application:
\
        [3CX Phone For Windows](http://dev.nodeca.com) (Click to download)
     - Once downloaded drag and drop the config file for the extension and then it will be set up.
     - DSG Staff Phone Extension Number:
        
        | Staff Name | Extension Number(Click to Download)|
        | :------: | :-----------: |
        | K. Dwight  | 200 |
        | K. Amp  | [100](http://dev.nodeca.com) |
        | K. Tangkwa, K.Pare  | [101](http://dev.nodeca.com) |
        | K. Bale  | [102](http://dev.nodeca.com) |
        | K. Noey  | [103](http://dev.nodeca.com) |
        | K. Jim  | [104](http://dev.nodeca.com) |

* ### IP DHCP
  * DSG VoIP Diagram
    * Internal IP address design:

        | Range IP | Device Type |
        | :------ | :----------- |
        | 192.168.1.1 - 192.168.1.20  | Server |
        | 192.168.1.21 - 192.168.1.30  | Printer |
        | 192.168.1.31 - 192.168.1.40  | Reserved |
        | 192.168.1.41 - 192.168.1.240  | DHCP |
        | 192.168.1.241 - 192.168.1.254  | Network Device |
    * [IP List Allocation](http://dev.nodeca.com) (Click to open)

* ### DNS
  * 192.168.1.254 (MikroTik Router)
  * 192.168.10.254 (3BB Router)
  * 192.168.20.254 (AIS Router)

* ### Device Redundancy

  * VRRP service
    
    Both DSG-HQ-LB01 and DSG-HQ-LB02 MiKroTik routers are configured load balancing with VRRP service, therefore the virtual IP from the service is up at IP address: 192.168.1.254 as the picture below:

    | Redundancy | Device Name | Device Model | Device Type |
    | :------ | :----------- | :------ | :----------- |
    | Primary/Active | **DSG-HQ-LB01** | MikroTik (CCR1009-7G-1C-1S+) | 255 |
    | Secondary/Standby | **DSG-HQ-LB02** | MikroTik (B4011iGS+RM) | 100 |

  * Failover: Switch
    | Failover | Device Name | Device Model |
    | :------ | :----------- | :------ |
    | Primary/Active | **DSG-HQ-SW01** | UBIQUITI Switch (US-16-150W) |
    | Secondary/Active | **DSG-HQ-SW02** | UBIQUITI Switch (US-16-150W) |
  * Switch LAN ports aggregation
    - Switch device aggregate configuration: Port 15 and Port 16 on DSG-HQ-SW01 switch 
   devices are aggregated to link with DSG-HQ-LB01 router devices and DSG-HQ-SW02 switch devices are aggregated to link with DSG-HQ-LB02 router devices.

* ### Firewall
  - IP NAT by router <br> **Chain:** Source NAT <br> **Mode:** Masquerade <br>

# **HARDWARE DEVICES**

| Device Name | Model | Units |
| :------ | :----------- | :------ |
| MikroTik Router | CCR1009-7G-1C-1S+ 18,290 (8Gb/s) | 1 |
| MikroTik Router | B4011iGS+RM 8,290 (2Gb/s) | 1 |
| Ubiquiti Switch | (US-16-150W) 16 Port with PoE + 2 port SFP | 2 |
| UBIQUITI Wireless Controller | Ubiquiti UniFi Cloud Key (UC-CK) | 1 |
| UBIQUITI Access Point | UAP-AC-LITE | 5 |
| UBIQUITI Access Point | UAP-AC-Pro | 1 |
| CCTV Controller | iDS-7204HQHI-M1 / S | 1 |
