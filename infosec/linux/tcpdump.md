# tcpdump

If you're attempting a command injection and want to confirm whether your commands are being executed on the target, you can always try pinging your machine and capture the ping using `tcpdump`.

```bash
sudo tcpdump -i tun0 icmp
```

* **`-i tun0`**: Specifies the network interface on which `tcpdump` should listen for traffic. In this case, `tun0` is typically associated with a VPN interface. Network interfaces for VPNs can vary based on the configuration and the software used. `tun0` is commonly used for configurations where traffic is routed through a tunnel interface, such as with OpenVPN.
* **`icmp`**: This is a filter to limit the output to ICMP packets only. ICMP is used by the `ping` utility to send echo requests and receive echo replies. Capturing ICMP packets helps in monitoring ping requests and responses which are used for diagnostics such as network reachability.

#### Checking Your Network Interface:

The command assumes you are using `tun0` as your network interface, but this might not be the case, especially if your system configuration differs or if you are using multiple VPNs or other network interfaces. You can check the available network interfaces and identify your VPN interface by running `ifconfig` ; the interface name could be `tun0`, `tun1`, `eth0`, etc.,&#x20;

