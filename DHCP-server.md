<h1>How to create and configurate A DHCP server</h1>

A DHCP (Dynamic Host Configuration Protocol) server is a network protocol whose role is to ensure automatic configuration of station or machine IP parameters. A DHCP server will allows automaticilly IP adress on devices when this last has connected. Here is a tutorial to create end configurate a DHCP server in a Linux envirorennement on Ubuntu distribution

<h1>Tutorial</h1>
To set up a DHCP server on Ubuntu, you can use the DHCPd service, which is a standard DHCP server available in Ubuntu's repositories. Here's how to proceed:

**Installing the DHCPd Server:**

1. Open a terminal on your Ubuntu server and ensure that you are logged in as a user with administrative privileges (or use sudo).

2. To install the DHCPd server, execute the following commands:

   ```bash
   sudo apt update
   sudo apt install isc-dhcp-server
   ```

   This will install the DHCPd service on your system.

**Configuring the DHCP Server:**

1. After the installation is complete, you need to configure the DHCP server by editing the main configuration file. Utilize a text editor to open the `/etc/dhcp/dhcpd.conf` file with administrative privileges, for instance:

   ```bash
   sudo nano /etc/dhcp/dhcpd.conf
   ```

2. You can tailor this configuration file to meet your specific requirements. Below is a simple example of a configuration for a basic DHCP server:

   ```dhcp
   subnet 192.168.1.0 netmask 255.255.255.0 {
       range 192.168.1.100 192.168.1.200;
       option routers 192.168.1.1;
       option domain-name-servers 8.8.8.8, 8.8.4.4;
   }
   ```
   Customize these values according to your network.

**Configuring the Network Interface:**

1. You also need to specify on which network interface the DHCP server should listen. Edit the `/etc/default/isc-dhcp-server` file:

   ```bash
   sudo nano /etc/default/isc-dhcp-server
   ```

2. Set the network interface on which you want the DHCP server to listen. For example:

   ```dhcp
   INTERFACESv4="eth0"
   ```

   Replace `eth0` with the name of your network interface.

**Starting and Enabling the Service:**

1. Once you have configured the DHCP server, start the service and enable it to start automatically at system boot:

   ```bash
   sudo systemctl start isc-dhcp-server
   sudo systemctl enable isc-dhcp-server
   ```

**Checking the Status:**

1. You can check the status of the DHCP server to ensure it's running correctly:

   ```bash
   sudo systemctl status isc-dhcp-server
   ```

   You should see a message indicating that the service is active and running.

Your DHCP server is now operational on your Ubuntu server. Make sure to configure it correctly according to your specific needs and network.
