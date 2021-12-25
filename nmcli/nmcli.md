
# Table of Contents

1.  [1) connection](#orgf459d32)
    1.  [show](#org8bedf17)
    2.  [up](#orgbdb03fa)
    3.  [down](#org53b2218)
    4.  [add](#org1e7de75)
    5.  [modify](#orge9c8827)
    6.  [clone](#org7a65272)
    7.  [edit](#orgb6b7767)
    8.  [delete](#orga449276)
    9.  [monitor](#orgcde77ca)
    10. [reload (reload all connection files from disk)](#org0e02e87)
    11. [load <filename> (not internanlly on nmcli)](#org537e188)
    12. [import [&#x2013;temporary] type <type> file <file to import>](#org92331ca)
    13. [export [id | uuid | path] <ID> [<output file>]](#orgac13bcc)
2.  [2) device](#org876e7f0)
    1.  [Show status for all devices](#org9f98a41)
    2.  [Show details of device(s)](#orgb825339)
    3.  [Set device properties.](#org7f97af1)
    4.  [Connect the device.](#org0207bf2)
    5.  [Disconnect the device](#orgea3bc6e)
    6.  [Modify one or more properties on an active device](#org3ea0c17)
    7.  [Delete the software devices](#org53d718a)
    8.  [Perform operation on Wi-Fi devices](#orgaca22ad)
3.  [3) general](#org01006c1)
    1.  [Show overall status of NetworkManager.](#org9143184)
4.  [4) networking](#orgb08ddc0)
    1.  [Switch networking on.](#orgf3a5d0e)
    2.  [Switch networking off.](#orgb0bd871)
    3.  [Get network connectivity state.](#orgd2e52b1)
5.  [5) radio](#org6a306f7)
    1.  [Get status of **all** radio switches, or turn them on/off.](#orgc67e997)
    2.  [Get status of **Wi-Fi** radio switch, or turn it on/off.](#org03ee1b3)
    3.  [Get status of **mobile broadband** radio switch, or turn it on/off.](#orgc278177)

<div class="abstract">
This document contains the essential information for using
***<span class="underline">NetworkManager</span>***, a basic instruction guide set for operating with
***nmcli***.

For fully detailed information, please see ***man nmcli***.

</div>


<a id="orgf459d32"></a>

# 1) connection


<a id="org8bedf17"></a>

## show


<a id="orgbdb03fa"></a>

## up


<a id="org53b2218"></a>

## down


<a id="org1e7de75"></a>

## add


<a id="orge9c8827"></a>

## modify


<a id="org7a65272"></a>

## clone


<a id="orgb6b7767"></a>

## edit


<a id="orga449276"></a>

## delete


<a id="orgcde77ca"></a>

## monitor


<a id="org0e02e87"></a>

## reload (reload all connection files from disk)


<a id="org537e188"></a>

## load <filename> (not internanlly on nmcli)


<a id="org92331ca"></a>

## import [&#x2013;temporary] type <type> file <file to import>


<a id="orgac13bcc"></a>

## export [id | uuid | path] <ID> [<output file>]


<a id="org876e7f0"></a>

# 2) device


<a id="org9f98a41"></a>

## Show status for all devices

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


<a id="orgb825339"></a>

## Show details of device(s)

    nmcli dev show [<ifname>]

The command lists details for all devices, or for a given device.


<a id="org7f97af1"></a>

## Set device properties.

    nmcli dev set [ifname] ifname [autoconnect {yes | no}]
    nmcli dev set [ifname] ifname [managed {yes | no}]


<a id="org0207bf2"></a>

## Connect the device.

    nmcli dev connect [<ifname>]

NetworkManager will try to find a suitable connection that will be
activated.

It will also consider connections that are not set to
auto-connect. 


<a id="orgea3bc6e"></a>

## Disconnect the device

    nmcli dev disconnect [<ifname>]

The command disconnects the device and prevents it from
auto-activating further connections without user/manual
intervention. 


<a id="org3ea0c17"></a>

## Modify one or more properties on an active device

Modify one or more properties currently active on the device without modifying
the connection profile. The changes have immediate effect. 

    nmcli dev modify <ifname> ([+|-]<setting>.<property> <value>)+

> ****<span class="underline">NOTE:</span>**** The changes do not modify the connection profile!


<a id="org53d718a"></a>

## Delete the software devices

    nmcli dev delete [<ifname>]

The command removes the interfaces. It only works for software
devices like:

-   Bonds
-   Brigdes
-   etc.

> ****<span class="underline">NOTE:</span>**** Hardware devices cannot be deleted by the command!


<a id="orgaca22ad"></a>

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


<a id="org01006c1"></a>

# 3) general


<a id="org9143184"></a>

## Show overall status of NetworkManager.

    nmcli gen status

'status' is the default action, which means 'nmcli gen' calls
'nmcli gen status'


<a id="orgb08ddc0"></a>

# 4) networking


<a id="orgf3a5d0e"></a>

## Switch networking on.

    nmcli net on


<a id="orgb0bd871"></a>

## Switch networking off.

    nmcli net off


<a id="orgd2e52b1"></a>

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


<a id="org6a306f7"></a>

# 5) radio


<a id="orgc67e997"></a>

## Get status of **all** radio switches, or turn them on/off.

    nmcli radio all [on | off]


<a id="org03ee1b3"></a>

## Get status of **Wi-Fi** radio switch, or turn it on/off.

    nmcli radio wifi [on | off]


<a id="orgc278177"></a>

## Get status of **mobile broadband** radio switch, or turn it on/off.

    nmcli radio wwan [on | off]

