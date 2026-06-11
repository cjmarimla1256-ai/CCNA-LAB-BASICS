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

These commands are commonly used after configuration to verify device settings, identify neighboring Cisco devices, and check the operational status of network interfaces.

