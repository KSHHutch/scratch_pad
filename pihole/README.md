# Setup Notes For Pi Hole
- Image raspberry pi OS onto microSD using RaspberyPi imager utility
  - Be sure to setup SSH in the custom settings
- Connect RaspberryPi to network (ethernet is probably best here)
- Check router for RaspberryPi's IP address, SSH into RaspberryPi
```bash
ssh user@ip_address
```
- Update RaspberryPi
```bash
sudo apt update && sudo apt upgrade -y
```
- Set static IP address (https://www.tomshardware.com/how-to/static-ip-raspberry-pi)
  1. Get the pi's current IPv4 and IPv6 addresses
  ```bash
  hostname -I
  ```
  2. Get router's IP address (will be after "default via")
  ```bash
  ip r
  ```
  3. Get the IP address of DNS
  ```bash
  grep "namesever" /etc/resolv.conf
  ```
  4. Open /etc/dhcpcd.conf for editing in nano (pi doesn't have vim installed by default...)
  ```bash
  nano /etc/dhcpcd.conf
  ```
  5. Add this to the bottom of the file
  ```bash
  interface [INTERFACE]  #eth0 for ethernet
  static_routers=[ROUTER IP]
  static domain_name_servers=[DNS IP]
  static ip_address=[STATIC IP ADDRESS YOU WANT]/24
  ```
  6. Save the file by hitting CTRL + X and reboot