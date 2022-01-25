# Upstream Data Instructions for Home Mining with a VPN
This guide aims to provide basic instructions for setting up a Virtual Private Network (VPN) for a Bitcoin home mining operation. There are several steps involved and setting up a VPN is not intuitive, however, this guide outlines the process step by step. So follow along and by the end you will have all the information you need to make your home network more secure and private. 

<p align="center">
  <img src="assets/TitleImage.jpg">
</p>       

## Scope
Bitcoin mining is carried out over a Stratum v1 protocol, which is un-encrypted and clear text internet traffic. This means that your Internet Service Provider (ISP) by default can not only see exactly what data is in your internet traffic but they can also see where that traffic is going, i.e., which mining pool you connect to. Likewise, the mining pool can see your Internet Protocol address (IP address), which can reveal who your ISP is and your approximate geographic location. Unless you take actions to guard your privacy then you are risking the security of your home mining operation. A few things that could go wrong without taking these precautions:

- Your ISP could siphon off a portion of your hashrate and steal your mining contributions.
- Your mining pool could log your IP address.
- You could be targeted if your government decides to clamp down on Bitcoin mining.

## Definitions
You may be exposed to some new terms during the course of this guide, it is important to clarify what these terms mean from the beginning so that you can have a better understanding of what is going on.

- VPN: Virtual Private Network, this establishes an encrypted tunnel for your internet traffic. This means your ISP cannot see the Stratum v1 data in your internet traffic. This also means that your ISP cannot see where your traffic is going and your mining pool cannot see your IP address. Your internet traffic will go straight to a VPN server before reaching the wide open internet.
- Firewall: The computer that sits between your modem and your home network. 
- Router: A device connected to your firewall that acts as a WiFi access point for your home network.  
- [pfSense](https://www.pfsense.org/): Open source firewall software, this will become the hub of your new home network. This firewall will be the link between your modem and your home network. This will also be the link between your home network and your VPN server and thus the wide open internet. 
- [WireGuard](https://www.wireguard.com/): An open source, light weight VPN protocol. WireGuard defines how the encrypted VPN tunnels are built. 
- [Mullvad](https://mullvad.net/en/): An open source VPN service provider, they do not collect any personal information and the subscription is €5 per month. Subscriptions can be paid for with bitcoin. Mullvad provides the servers in a variety of geographic locations that you can connect to so that all of your internet traffic comes from their servers when reaching the wide open internet.   
  
These are the tools that will be explained in this guide. You will see how these puzzle pieces fit together to help you guard your privacy and secure your Bitcoin home mining operation. These tools are not the only ones available, there are a range of firewall software projects, VPN protocols, and VPN providers. Feel free to explore what is out there and find what works best for you. There are also different ways in which to guard your privacy, for example setting up a router with DNScrypt and setting up a SOCKs5 proxy. 
  
The following is a straight forward and common sense approach to configuring a private and secure Bitcoin home mining network. Even with the other tools and approaches available, the trade off was added complication. The risk of introducing latency from the VPN connection is mitigated by automatically routing internet traffic over multiple VPN tunnels.   
  
If at any point in this guide you need more clarity, you can view the full and complete guide with many more details [here](https://www.econoalchemist.com/post/bitcoin-home-mining-network-privacy).  
