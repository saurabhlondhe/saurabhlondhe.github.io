---
layout: post
title:  "ManageIQ Database Backup and Restore"
date:   2018-08-30
desc: "ManageIQ Database configuration and restoring database"
keywords: "manageiq,hybridcloud,gh-pages,website,blog,postgresql,backup,restore"
categories: [Project]
tags: [manageiq,ansible,open source,automation,postgresql]
icon: icon-shell
---
# Hybrid-Cloud-Automation-Using-Ansible-ManageIQ
Now a days, Automation is the mother of all the inventions, that give rise to all the new technologies. Most of the latest technologies are the reason to automation. This project is one of our try to automate hybrid cloud using ManageIQ and Ansible.

A hybrid cloud is the one with the combination of both i.e. private as
well as public cloud with the specified specifications.

ManageIQ is an open source cloud management platform by Red Hat. It is written in Ruby with RoR (Ruby on Rails) as platform.

Ansible is software that automates software provisioning, configuration
management, and application deployment. Playbooks are Ansible’s
configuration, deployment, and orchestration language.

---
---
# Intorduction to ManageIQ
- ManageIQ is an Open Source Cloud management platform. The ManageIQ project founded by Red Hat In 2014 as a community  project. It is written in Ruby with RoR (Ruby on Rails) as platform.
- For getting started get a ManageIQ instanses from [here](http://manageiq.org/download/)

---
### Installation
- Using KVM/Qemu image

    - Download ManageIQ Image from [manageiq/downloads](http://manageiq.org/download/) choose QEmu/KVM

    - Install KVM and necessary packages

            # yum install qemu-kvm libvirt libvirt-python virt-install
    
    - Create ManageIQ VM using existing image
        - Create VM using ```virt-install``` command

                # sudo virt-install --virt-type kvm  --import --name ManageIQ  --memory 12288 --vcpus 4 --cpu host  --disk manageiq-openstack-gaprindashvili-5.qc2,format=qcow2,bus=virtio  --network default,model=virtio   --os-type=linux --os-variant=centos7.0   --graphics spice
    
    - Launch VM using ```virsh ```
            
            # virsh start ManageIQ
    - Login using ssh
            
            # ssh root@<ip_of_server>

        - user: _root_
        - password: _smartvm_

- [Using docker image](https://saurabhlondhe.github.io/project/open_source/linux/2018/08/31/Install-manageiq-in-docker.html)

---
### Appliance console and basic configuration

Running a command _appliance_console_  ot _ap_ to get into ManageIQ Virtual Appliance. It gives datails regarding ManageIQ Machine such as,
- hostname 
- IPv4 Address
- IPv4 Gateway
- IPv6 Address
- IPv6 Gateway
- Primary DNS
- Secondary DNS
- Search Order
- Mac Address
- TimeZone
- Local Database Server
- ManageIQ Server
- ManageIQ Database
- Database/Region
- External Auth
- ManageIQ Version

Pressing Enter will lead to the Advanced Settings

1. Configure Network
2. Set Timezone
3. Set Date and Time
4. Restore Database From Backup
5. Configure Database
6. Configure Database Replication
7. Logfile Configuration
8. Configure Application Database Failover Minitor
9. Configure External Authentication (httpd)
10. Update External Authentication Options
11. Generate Custom Encryption Key
12. Stop EVM server Processes
13. Start EVM server Processes
14. Restart Appliance
15. Shut Down Appliance
16. Summary Information
17. Quit

---
---

# ManageIQ database configuration

ManageIQ uses PostgreSQL Database. So while dealing with ManageIQ database we'll need to follow PostgreSQL commands and procedure to take a database dump as a backup and to restore it in another instance.


    Note: ManageIQ uses "vmdb_production" database  


---
This is list of steps followed to obtain a dump from a db then retsore it

### Dump the Postgres DB:

1. stop the appliance(s):
    
        # systemctl stop evmserverd
 
    This will stop the evmserverd.service from using database in background but no need to stop them, for creating backup the doesn't affects anywhere.

2. dump the database into file:

    
        # pg_dump -Fc vmdb_production > production.dump

3. Copy the dump file to the other ManageIQ instance where the database have to restore.

    We can use `scp` for that as follows:
        
        # scp production.dump root@ip_of_other_instance:/root/

### Import the Postgres dump

1. Take `production.dump` to the local machine.

2. Stop the backend processes

        # systemctl stop evmserverd
3. Drop existing database `vmdb_production` 

        # dropdb vmdb_production

4. create new database named `vmdb_production`

        # createdb vmdb_production

5. restore the database from dump file

        # pg_restore -d vmdb_production "/path/to/production.dump
6. change directory to `/var/www/miq/vmdb/tools` 

        # vmdb  #executing "vmdb" will take you to "/var/www/miq/vmdb/"
        # cd tools
        # bundle exec fix_auth.rb --v2 --invalid bogus
7. Start evm service

        # systemctl start evmserverd
        
This will do the task of restoring database manually.
