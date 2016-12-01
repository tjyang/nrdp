# Overview

NRDP (**N**agios **R**emote **D**ata **P**rocessor) is a simple, PHP-based passive result collector for use with Nagios. It is designed to be a flexible data transport mechanism and processor, with a simple and powerful architecture that allows for it to be easily extended and customized to fit individual users' needs.

By default, NRDP has the capability of allowing remote agents, applications, and Nagios instances to submit commands and host and service check results to a Nagios server. This allows Nagios administrators to use NRDP to configure distributed monitoring, passive checks, and remote control of their Nagios instance in a quick and efficient manner. The capabilities for NRDP can be extended through the development of additional NRDP plugins.

## Installation

1. Create a directory for the NRDP server files::

    mkdir /usr/local/nrdp
    
2. Copy over server NRDP files from installation directory::

    cd nrdp
    cp -r * /usr/local/nrdp
    
3. Set permissions on NRDP dir/files::

    chown -R nagios:nagios /usr/local/nrdp
    
4. Edit the NRDP server config file::

    vi /usr/local/nrdp/server/config.inc.php
    
    And add at least one token string to the $cfg['authorized_tokens'] 
    variable. Example::
    
    $cfg['authorized_tokens'] = array(
        "asd7fjk3l34",
        "df23m7jadI34"
    );
    
5. Configure Apache depending on the version and operating system you
    may need to change this location.:

    Apache on CentOS/RHEL::

    cp nrdp.conf /etc/httpd/conf.d
    /etc/init.d/httpd restart

6. The NRDP server has now been installed! You can now try out 
    the NRDP server API example by accessing::

    http://<ip address>/nrdp
