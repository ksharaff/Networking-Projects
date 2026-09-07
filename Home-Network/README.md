# Home Network Packet Tracer Project

## Overview

For this project, I used **Cisco Packet Tracer** to design and simulate a home network for a two-story house. The idea was to take a typical household setup — two desktops and a laptop — and get everything connected to the internet and to each other, while actually understanding what each piece of equipment is doing under the hood rather than just clicking "connect" and hoping it works.
I wanted a hands-on way to understand the basics of how a home network is actually put together — modems vs. routers, how devices get IP addresses automatically, and how a domain name like `google.com` turns into something a computer can actually use. Packet Tracer let me build and test all of that without needing real hardware.

## Key Concepts I Worked With

**Modem** — Acts as the bridge between the house and the ISP. In this setup it connects over a coax cable and is responsible for grabbing a public IP address, basically the "mailing address" my home network uses to talk to the outside world.

**Router** — Sits behind the modem and creates the actual local network. It hands out the internet connection to every device in the house and also handles Wi-Fi, so the laptop doesn't need to be wired in.

**DHCP (Dynamic Host Configuration Protocol)** — This is what saves you from manually assigning an IP address to every single device. In my setup, DHCP operates on two levels:
- The ISP hands the modem a public IP address.
- The home router hands out private IP addresses to the desktops and laptop, keeping everything organized inside the network.

**DNS (Domain Name System)** — Basically the internet's phonebook. Computers don't understand `google.com`, they only understand numeric IP addresses like `208.67.200.200`. When a device tries to reach a website, the DNS server looks up the name and translates it into the correct IP address behind the scenes.

## Network Layout

- **Ground Floor:** A desktop (PC0) sits in the living room, connected into the network.
- **First Floor:** A second desktop (PC1) is wired directly into the router using a gigabit ethernet cable for a fast, stable connection. A laptop nearby connects wirelessly instead, joining the network over Wi-Fi through an SSID configured on the router.
- **Server:** A central server plays two roles — it stands in as the "google.com" website for testing, and it also runs the DHCP and DNS services for the rest of the network.
- **Everything upstream:** The router connects to a cable modem, which connects out through a simulated ISP cloud to the server, mimicking a real home-to-internet connection.

<img width="1325" height="614" alt="Screenshot 2026-08-11 203022" src="https://github.com/user-attachments/assets/a2e2dd47-bd57-41cd-a7e2-b24042a067a7" />

*(Diagram of the full setup — modem, router, wired/wireless devices, and the ISP/server side)*

## Testing

Once everything was wired and configured, I tested connectivity by pinging the server from each device on the network. Below is the result from the laptop, which was connected over Wi-Fi:

<img width="1663" height="951" alt="Screenshot 2026-08-11 202146" src="https://github.com/user-attachments/assets/3241a04c-dc35-42fe-8220-2d4a6a8a4c10" />

Every device on the network was able to successfully ping the server, which confirmed DHCP, DNS, and routing were all working correctly and the network was reliable end to end.

## Tools Used

- Cisco Packet Tracer

## What I Learned

Working through this made concepts like DHCP and DNS click in a way that just reading about them never did. Seeing the actual `ipconfig` output — the assigned IP, the gateway, the DHCP and DNS server addresses — and connecting that back to "oh, this is why my laptop can reach google.com without me typing in a number" made the whole client-server / networking model much more concrete.

