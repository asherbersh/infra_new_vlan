# infra_new_vlan

this ansible playbook allow adding new vlan to the company network infrastracture 
to implement the vlan installation the following data should be collected :

in network_devices file :

group - define what type of the device to be configured ( junos / cisco )

model - defines the device model ( ex3300/ex3400/qfx/nexus)

type - define if the device to be configured is a backbone or an access device 

in vlan_details file :

vlan_id - defines the vlan id to be configured 

vlan_name - is the name of the new vlan

is_layer3 - is the vlan should be configured as a layer 3 on the switch ( True/False)

subnet - vlan subnet

vlan_type - vlan type ( servers /users)

location - device location

site_id - the site id 

dhcp_server - the dhcp server ip address

is_dhcp - is the vlan should be dhcp ( True/False)



network_devices.xlsx file contains all devices we would like to take any data from .

vlan_details.xlsx - contains the information of the vlan to be added 
