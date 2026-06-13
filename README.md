Cisco Packet Tracer Commands Reference
1. enable
Purpose:
Switches from User EXEC Mode (>) to Privileged EXEC Mode (#), allowing access to monitoring, troubleshooting, and configuration commands.
Example:
Switch> enable
Switch#


2. configure terminal
Purpose:
Enters Global Configuration Mode, where device settings such as passwords, interfaces, and network configurations can be modified.
Example:
Switch# configure terminal
Switch(config)#


3. hostname <name>
Purpose:
Changes the device's name. Hostnames help identify routers and switches within a network and make configuration and troubleshooting easier.
Example:
Switch(config)# hostname S1
S1(config)#

Common Uses:
Identifying network devices
Improving network documentation
Simplifying troubleshooting

4. enable password <password>
Purpose:
Sets a password for accessing Privileged EXEC Mode. This method is less secure because the password can be viewed in plain text unless password encryption is enabled.
Example:
S1(config)# enable password cisco


5. enable secret <password>
Purpose:
Sets an encrypted password for Privileged EXEC Mode. This is the recommended method because it provides stronger security than enable password.
Example:
S1(config)# enable secret class

Note:
If both enable password and enable secret are configured, the device will use the enable secret password.

6. service password-encryption
Purpose:
Encrypts all plain-text passwords stored in the running configuration to prevent them from being easily read.
Example:
S1(config)# service password-encryption


7. no service password-encryption
Purpose:
Disables password encryption for future password entries. Existing encrypted passwords remain encrypted until reconfigured.
Example:
S1(config)# no service password-encryption


8. line console 0
Purpose:
Accesses the configuration settings for the console port, which is used for direct local management of the device.
Example:
S1(config)# line console 0
S1(config-line)#


9. password <password>
Purpose:
Assigns a password to the selected line (such as the console line).
Example:
S1(config-line)# password admin123


10. login
Purpose:
Enables password authentication on the configured line. Without this command, the configured password will not be enforced.
Example:
S1(config-line)# login


11. exit
Purpose:
Returns to the previous configuration level or mode.
Example:
S1(config-line)# exit
S1(config)#


12. show cdp neighbors
Purpose:
Displays information about directly connected Cisco devices discovered through Cisco Discovery Protocol (CDP).
Common Uses:
Identifying neighboring devices
Verifying physical connections
Troubleshooting network topology issues
Example:
S1# show cdp neighbors


13. show running-config
Purpose:
Displays the current active configuration stored in RAM.
Common Uses:
Verifying configurations
Reviewing passwords and interface settings
Troubleshooting device configuration issues
Example:
S1# show running-config


14. show ip interface brief
Purpose:
Provides a summarized view of all interfaces, including IP addresses and operational status.
Common Uses:
Checking interface status
Verifying IP address assignments
Identifying disconnected or disabled interfaces
Example:
S1# show ip interface brief

Sample Output:
Interface              IP-Address      OK? Method Status Protocol
FastEthernet0/1        unassigned      YES manual up     up
Vlan1                  192.168.1.1     YES manual up     up

15. switchport mode access
Purpose:
Configures a switch port as an Access Port, allowing it to carry traffic for only one VLAN. Access ports are typically connected to end devices such as PCs, printers, and servers.
Example:
S1(config)# interface fastethernet 0/1
S1(config-if)# switchport mode access

Common Uses:
Connecting PCs and other end devices
Assigning ports to a single VLAN
Preventing dynamic trunk negotiation

16. switchport mode trunk
Purpose:
Configures a switch port as a Trunk Port, allowing it to carry traffic from multiple VLANs between switches, routers, or other network devices.
Example:
S1(config)# interface fastethernet 0/24
S1(config-if)# switchport mode trunk

Common Uses:
Connecting switches together
Carrying multiple VLANs over a single link
Supporting VLAN communication across the network

17. switchport trunk encapsulation dot1q
Purpose:
Sets the trunking encapsulation method to IEEE 802.1Q (Dot1Q). This protocol adds VLAN tags to Ethernet frames so multiple VLANs can traverse a trunk link.
Example:
S1(config)# interface fastethernet 0/24
S1(config-if)# switchport trunk encapsulation dot1q

Note:
Available only on certain Cisco switch models.
Some switches support only 802.1Q and do not require this command.
Common Uses:
Configuring VLAN trunk links
Inter-switch communication
Router-on-a-Stick implementations

18. encapsulation dot1q vlan <VLAN_ID>
Purpose:
Configures a router subinterface to use 802.1Q VLAN tagging, allowing the router to communicate with a specific VLAN. This command is commonly used in Router-on-a-Stick configurations.
Example:
R1(config)# interface gigabitethernet 0/0.10
R1(config-subif)# encapsulation dot1q 10

Common Uses:
Inter-VLAN Routing
Router-on-a-Stick configurations
Connecting multiple VLANs through a single router interface
Sample Configuration:
R1(config)# interface gigabitethernet 0/0.10
R1(config-subif)# encapsulation dot1q 10
R1(config-subif)# ip address 192.168.10.1 255.255.255.0

R1(config)# interface gigabitethernet 0/0.20
R1(config-subif)# encapsulation dot1q 20
R1(config-subif)# ip address 192.168.20.1 255.255.255.0


VLAN Configuration Example
enable
configure terminal

interface fastethernet 0/1
switchport mode access

interface fastethernet 0/24
switchport trunk encapsulation dot1q
switchport mode trunk

exit

Router-on-a-Stick Example
enable
configure terminal

interface gigabitethernet 0/0.10
encapsulation dot1q 10
ip address 192.168.10.1 255.255.255.0

interface gigabitethernet 0/0.20
encapsulation dot1q 20
ip address 192.168.20.1 255.255.255.0

These commands are commonly used when configuring VLANs, trunk links, and Inter-VLAN Routing in Cisco Packet Tracer labs.


Status Indicators:
up/up – Interface is operational.
down/down – Interface is inactive or disconnected.
administratively down/down – Interface has been manually disabled using the shutdown command.

Typical Initial Device Configuration
enable
configure terminal

hostname S1

enable password cisco
enable secret class

service password-encryption

line console 0
password admin123
login
exit


Verification Commands
show cdp neighbors
show running-config
show ip interface brief

These commands are commonly used after configuration to verify device settings, identify neighboring Cisco devices, and check the operational status of network interfaces..

