# infra_new_vlan

this ansible playbook allow adding new vlan to the company network infrastracture 
to implement the vlan installation the following data should be collected :

## files: 
    network_devices.xlsx file contains all devices we would like to take any data from .
    vlan_details.xlsx - contains the information of the vlan to be added 

### network_devices file :
        group - define what type of the device to be configured ( junos / cisco )
        model - defines the device model ( ex3300/ex3400/qfx/nexus)
        type - define if the device to be configured is a backbone or an access device 

### vlan_details file :
        vlan_id - defines the vlan id to be configured 
        vlan_name - is the name of the new vlan
        is_layer3 - is the vlan should be configured as a layer 3 on the switch ( True/False)
        subnet - vlan subnet
        vlan_type - vlan type ( servers /users)
        location - device location
        site_id - the site id 
        dhcp_server - the dhcp server ip address
        is_dhcp - is the vlan should be dhcp ( True/False)

## Roles used 
    infra_new_vlan -power off all the network devices in the inventory file 


### infra_new_vlan role 
      tasks : 
        1. cisco_new_vlan_add - add new vlan to cisco device using cisco new vlan template  
        2. cisco_validation_check - varify before creating the vlan that the vlan does not esxist in the       infrastracture
        3. junos_new_vlan_add -add new vlan to junos device using junos new vlan template
        4. junos_validation_check -varify before creating the vlan that the vlan does not esxist in the       infrastracture
      template :
        1. cisco_new_vlan_template - template for adding new vlan to cisco based on the vlan details file
        2. junos_new_vlan_template - template for adding new vlan to junos based on the vlan details file
      description : 
        for each type of operation system this role would validate the new vlan does not exist and then would add it to the switch  

## main playbook
    prod_new_vlan  - configure new vlan to all operation system in production ( cisco /junos) 
    test_new_vlan  - configure new vlan to all operation system in test (test_junos) 


