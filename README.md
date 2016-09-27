[![Build Status](https://travis-ci.org/singleplatform-eng/ansible-role-logrhythm.svg?branch=master)](https://travis-ci.org/singleplatform-eng/ansible-role-logrhythm)

ansible-role-logrhythm
=========

Ansible role for installing and configuring the LogRhythm System Monitor Agent for Linux

Role Variables
--------------

- `logrhythm_host`: host for Mediator 1 (this is required, unless you override the entire `logrhythm_config`)

- `logrhythm_client_address`: client address for Mediator 1 (default: 0)

- `logrhythm_package`: can be either a repository package or a path to a file (default: `scsm`)

        logrhythm_package: /tmp/scsm_7.1.2.8001_amd64.deb

- `logrhythm_config`: scsm.ini configuration

    Default:
    
        logrhythm_config:
            General:
                LogLevel: 4
            'Mediator 1':
                Host: "{{logrhythm_host}}"
                ServerPort: 443
                ClientAddress: "{{logrhythm_client_address}}"
                ClientPort: 3333

Example Playbook
----------------

    - hosts: all
      become: yes
      roles:
          - { role: ansible-role-logrhythm, logrhythm_host: 10.0.10.10 }

Author Information
------------------

[SinglePlatform Engineering](http://engineering.singleplatform.com/)

License
-------

BSD 3-Clause
