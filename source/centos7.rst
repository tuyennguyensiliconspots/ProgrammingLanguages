CentOS 7
===============

1.  Setup
-----------------

Subsection 1.1.1 Title TEST
~~~~~~~~~~~~~~~~~~~~~~~~~~~

2. Configuration
-----------------

Enable GUI and RDP for CentOS 7
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Connect to VM using SSH command tool like Putty.exe
    Host name: centosrdp.cloudapp.net (or IP address)
    Port: 22
2. Type the following commands
    Gain root privileges::

    # sudo -s

    Install EPEL and nux Desktop repository rpms::

    # rpm -Uvh http://li.nux.ro/download/nux/dextop/el7/x86_64/nux-dextop-release-0-1.el7.nux.noarch.rpm

    after this is successful, continue by installing the GNOME desktop to get the graphical user interface you desire::

    # yum groupinstall "GNOME Desktop" "Graphical Administration Tools"

    the installation process will take sometime depending on your internet speed, after the installation is done, run the following command to change the reboot from CLI to GUI.::

    # ln -sf /lib/systemd/system/runlevel5.target /etc/systemd/system/default.target

    the next step is to install the xrdp to be able to RDP on the VM::

    # yum -y install xrdp tigervnc-server

    then start the xrdp service::

    # systemctl start xrdp.service

    then test the xrdp service by running the following command::

    # netstat -antup | grep xrdp

    now you can enable the xrdp service::

    # systemctl enable xrdp.service

    And then add a port in the machine firewall if it was activated, if not then there is no need for the next two commands.::

    # firewall-cmd --permanent --zone=public --add-port=3389/tcp
    # firewall-cmd --reload

3. Go to Azure, and Open Network Security Group, add Inbound Security Rule for this VM:
    Priority: 1010
    Name: RemoteDesktop
    Source: Any
    Destination: Any
    Service: RDP(TCP/3389)
    Action: Allow

4. Open Remote Desktop Connection and connect to VM.


