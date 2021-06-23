+++
title="Debian"
date=2020-12-22

[taxonomies]
tags = ["Linux", "Debian"]
authors = ["Allan Phu"]
+++

## Enabling wifi on boot for hidden ssids

In **/etc/NetworkManager/NetworkManger.conf**, under the **[wifi]** section add **hidden=true**.

To test if the changes worked, you can do either of the following:

<ol>
    <li> Restart NetworkManager by running `sudo systemctl restart NetworkManager` </li>
    <li> Reboot your system by running `sudo reboot` </li>
</ol>

Your system should now automatically scan and connect to your hidden ssid!