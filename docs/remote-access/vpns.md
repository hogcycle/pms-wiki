# VPNs

VPNs are common place these days. Many folks use them to pretend to be in a country they are not to avoid geoblocks with streaming services or to connect to their place of work. They can also be used to hide your immediate identity online so are often used to sail the seven seas and should *definitely* be used on any kind of public wifi.

We can use VPNs for more than this though. By using a VPN to secure the traffic passing in and out of our firewall we largely avoid the need to open ports in our firewall which we already established is bad security practice unless absolutely neccessary.

## WireGuard VPN

WireGuard was first merged to the Linux kernel v5.6 in March 2020 [^1]. A relative newcomer to the VPN scene the project took a completely fresh approach to VPNs and aims to be "faster[^2], simpler[^3], leaner" than other VPN technologies. The OpenVPN codebase is approximiately 70,000 lines long[^4] compared just 4,000 with WireGuard.

## Tailscale

[Tailscale](https://tailscale.com/selfhosted/) is a new kid on the VPN block and it uses Wireguard under the hood to provide "VPN as a service". It works like an [overlay network](https://tailscale.com/blog/how-tailscale-works/) between the computers of your networks - using [NAT traversal](https://tailscale.com/blog/how-nat-traversal-works/).

Everything in Tailscale is Open Source, except the GUI clients for proprietary OS (Windows and macOS/iOS), and the control server.

The control server works as an exchange point of Wireguard public keys for the nodes in the Tailscale network. It assigns the IP addresses of the clients, creates the boundaries between each user, enables sharing machines between users, and exposes the advertised routes of your nodes.

A Tailscale network (tailnet) is private network which Tailscale assigns to a user in terms of private users or an organisations.

To assuage those worried about the control server being a hosted service there is Headscale. [Headscale](https://github.com/juanfont/headscale) aims to implement a self-hosted, open source alternative to the Tailscale control server. Headscale has a narrower scope and an instance of Headscale implements a single Tailnet, which is typically what a single organisation, or home/personal setup would use.

## OpenVPN

OpenVPN is pretty much limited to legacy infrastructure at this point. There is very little reason to consider standing up a new instance of OpenVPN.