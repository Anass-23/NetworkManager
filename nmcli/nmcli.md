
# Table of Contents

- [Table of Contents](#table-of-contents)
- [1) connection](#1-connection)
  - [Show details of connection profiles](#show-details-of-connection-profiles)
  - [Up, activate a connection on a device](#up-activate-a-connection-on-a-device)
  - [Down, deactivate a connection from a device](#down-deactivate-a-connection-from-a-device)
  - [Add a new connection profile](#add-a-new-connection-profile)
  - [Modify one or more properties of a connection profile](#modify-one-or-more-properties-of-a-connection-profile)
  - [Clone an existing connection profile](#clone-an-existing-connection-profile)
  - [Delete a connection profile](#delete-a-connection-profile)
  - [Reload all connection files from disk](#reload-all-connection-files-from-disk)
  - [Load or reload one or more connection files from disk.](#load-or-reload-one-or-more-connection-files-from-disk)
- [2) device](#2-device)
  - [Show details of device(s)](#show-details-of-devices)
  - [Status for all devices](#status-for-all-devices)
  - [Set device properties.](#set-device-properties)
  - [Connect the device.](#connect-the-device)
  - [Disconnect the device](#disconnect-the-device)
  - [Modify one or more properties on an active device](#modify-one-or-more-properties-on-an-active-device)
  - [Delete the software devices](#delete-the-software-devices)
  - [Perform operation on Wi-Fi devices](#perform-operation-on-wi-fi-devices)
- [3) general](#3-general)
  - [Show overall status of NetworkManager.](#show-overall-status-of-networkmanager)
- [4) networking](#4-networking)
  - [Switch networking on.](#switch-networking-on)
  - [Switch networking off.](#switch-networking-off)
  - [Get network connectivity state.](#get-network-connectivity-state)
- [5) radio](#5-radio)
  - [Get status of **all** radio switches, or turn them on/off.](#get-status-of-all-radio-switches-or-turn-them-onoff)
  - [Get status of **Wi-Fi** radio switch, or turn it on/off.](#get-status-of-wi-fi-radio-switch-or-turn-it-onoff)
  - [Get status of **mobile broadband** radio switch, or turn it on/off.](#get-status-of-mobile-broadband-radio-switch-or-turn-it-onoff)

<div class="abstract">
This document contains the essential information for using
***<span class="underline">NetworkManager</span>***, a basic instruction guide set for operating with
***nmcli***.

For fully detailed information, please see ***man nmcli***.

</div>


<a id="org2f65c41"></a>

# 1) connection


<a id="org4f4b284"></a>

## Show details of connection profiles

    nmcli con show [--active, --show-secrets] [id | uuid | path] <ID>

The flag '&#x2013;active' will only show the profiles of the current
active profiles.

For displaying also the associated secrets use the '&#x2013;show-secrets'
option.


<a id="orgdc30008"></a>

## Up, activate a connection on a device

    nmcli con up ifname <ifname> [ap <BSSID>] [nsp <name>] [passwd-file <file with passwords>]


<a id="org52f4a5b"></a>

## Down, deactivate a connection from a device

    nmcli con down [id | uuid | path | apath] <ID>


<a id="org5669dd5"></a>

## Add a new connection profile


<a id="org98313e2"></a>

## Modify one or more properties of a connection profile

    nmcli con modify [id | uuid | path] <ID> ([+|-]<setting>.<property> <value>)+


<a id="orgaff9775"></a>

## Clone an existing connection profile

    nmcli con clone [--temporary] [id | uuid | path] <ID> <new name>


<a id="org14b2615"></a>

## Delete a connection profile

    nmcli con delete [id | uuid | path] <ID>


<a id="orgbb9d479"></a>

## Reload all connection files from disk

    nmcli con reload


<a id="orga87b878"></a>

## Load or reload one or more connection files from disk.

    nmcli con load <filename>


<a id="org2621cae"></a>

# 2) device


<a id="org6430a44"></a>

## Show details of device(s)

    nmcli dev show [<ifname>]

The command lists details for all devices, or for a given device.


<a id="orgf39a0e4"></a>

## Status for all devices

    nmcli dev status

By default, the following columns are shown:

-   DEVICE     - interface name
-   TYPE       - device type
-   STATE      - device state
-   CONNECTION - connection activated on device (if any)

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">DEVICE</th>
<th scope="col" class="org-left">TYPE</th>
<th scope="col" class="org-left">STATE</th>
<th scope="col" class="org-left">CONNECTION</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">ens33</td>
<td class="org-left">ethernet</td>
<td class="org-left">connected</td>
<td class="org-left">Wired connection 1</td>
</tr>


<tr>
<td class="org-left">lo</td>
<td class="org-left">loopback</td>
<td class="org-left">unmanaged</td>
<td class="org-left">--</td>
</tr>
</tbody>
</table>


<a id="org0ee6905"></a>

## Set device properties.

    nmcli dev set [ifname] ifname [autoconnect {yes | no}]
    nmcli dev set [ifname] ifname [managed {yes | no}]


<a id="org69f9aa3"></a>

## Connect the device.

    nmcli dev connect [<ifname>]

NetworkManager will try to find a suitable connection that will be
activated.

It will also consider connections that are not set to
auto-connect. 


<a id="org23ed6a9"></a>

## Disconnect the device

    nmcli dev disconnect [<ifname>]

The command disconnects the device and prevents it from
auto-activating further connections without user/manual
intervention. 


<a id="org8d54568"></a>

## Modify one or more properties on an active device

Modify one or more properties currently active on the device without modifying
the connection profile. The changes have immediate effect. 

    nmcli dev modify <ifname> ([+|-]<setting>.<property> <value>)+

> ****<span class="underline">NOTE:</span>**** The changes do not modify the connection profile!


<a id="org0e1e6be"></a>

## Delete the software devices

    nmcli dev delete [<ifname>]

The command removes the interfaces. It only works for software
devices like:

-   Bonds
-   Brigdes
-   etc.

> ****<span class="underline">NOTE:</span>**** Hardware devices cannot be deleted by the command!


<a id="orgc256782"></a>

## Perform operation on Wi-Fi devices

-   List available Wi-Fi access points
    
        nmcli dev wifi list [ifname <ifname>] [bssid <BSSID>] [--rescan yes|no|auto]
    
    The options 'ifname' and 'bssid' can be used for listing and
    showing APs (access points) for a particular 'ifname'. 
    
    The &#x2013;rescan flag tells if a new scan should be done for listing
    APs.

-   Connect to a Wi-Fi network specified by SSID or BSSID
    
        sudo nmcli dev wifi connect connect <(B)SSID> [password <password>] [wep-key-type key|phrase] [ifname <ifname>]
        		[bssid <BSSID>] [name <name>] [private yes|no] [hidden yes|no]
    
    The most common use would be:
    
        sudo nmcli dev wifi connect <"SSID"> password <"PASSWORD">
    
    And for security purposes, for not displaying the 'SSID' network
    password we should run:
    
        sudo nmcli --ask dev wifi connect <"SSID">

-   Re-scan for available access points.
    
        nmcli dev wifi rescan [ifname <ifname>] [[ssid <SSID to scan>] ...]
    
    The option 'ssid' allows scanning for a specific SSID, which is
    useful for APs with hidden SSIDs.
    
    > ****<span class="underline">NOTE:</span>**** Performing a rescan would not show the APs!

-   Create a Wi-Fi hotspot
    
        nmcli dev wifi hotspot [ifname <ifname>] [con-name <name>] [ssid <SSID>]
        		[band a|bg] [channel <channel>] [password <password>]
    
    Parameters:
    
    -   ***<span class="underline">ifname:</span>*** Wi-Fi device to use
    -   ***<span class="underline">con-name:</span>*** Hotspot connection profile name
    -   ***<span class="underline">ssid:</span>*** SSID of the hotspot
    -   ***<span class="underline">band:</span>*** Wi-Fi band to use
    -   ***<span class="underline">channel:</span>*** Wi-Fi channel to use
    -   ***<span class="underline">password:</span>*** Password for the hotspot
    
    > ****<span class="underline">NOTE:</span>**** Use 'connection down' or 'device disconnect' to stop
    >   the hotspot.

-   Show a password of an interface
    
        nmcli dev wifi show-password <ifname>


<a id="org3c92b97"></a>

# 3) general


<a id="org47550a0"></a>

## Show overall status of NetworkManager.

    nmcli gen status

'status' is the default action, which means 'nmcli gen' calls
'nmcli gen status'


<a id="org63d3805"></a>

# 4) networking


<a id="org4787862"></a>

## Switch networking on.

    nmcli net on


<a id="org0e5de5c"></a>

## Switch networking off.

    nmcli net off


<a id="orgccd248d"></a>

## Get network connectivity state.

    nmcli net connectivity [check]

The optional **check** argument makes NetworkManager re-check the
connectivity.

Possible states are:

-   ***<span class="underline">none:</span>*** The host is not connected to any network.

-   ***<span class="underline">portal:</span>*** The host is behind a captive portal and cannot reach the full Internet.

-   ***<span class="underline">limited:</span>*** The host is connected to a network, but it has no access to the Internet.

-   ***<span class="underline">full:</span>*** The host is connected to a network and has full access to the Internet.

-   ***<span class="underline">unknown:</span>*** The connectivity status cannot be found out.


<a id="org84b5f2c"></a>

# 5) radio


<a id="org247bfbd"></a>

## Get status of **all** radio switches, or turn them on/off.

    nmcli radio all [on | off]


<a id="orgde912c1"></a>

## Get status of **Wi-Fi** radio switch, or turn it on/off.

    nmcli radio wifi [on | off]


<a id="orgac2f503"></a>

## Get status of **mobile broadband** radio switch, or turn it on/off.

    nmcli radio wwan [on | off]

