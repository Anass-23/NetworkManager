
# Table of Contents

1.  [connection](#orgafae9fd)
    1.  [show](#org3b34431)
    2.  [up](#orgdde811c)
    3.  [down](#org17ac69d)
    4.  [add](#orge2ff720)
    5.  [modify](#org0e00cc1)
    6.  [clone](#org7b48fb8)
    7.  [edit](#org3d223ff)
    8.  [delete](#orge5b8a71)
    9.  [monitor](#org8fd8a9b)
    10. [reload (reload all connection files from disk)](#org80c0089)
    11. [load <filename> (not internanlly on nmcli)](#orga2d6e8b)
    12. [import [&#x2013;temporary] type <type> file <file to import>](#org9e35460)
    13. [export [id | uuid | path] <ID> [<output file>]](#orgfb1cb3b)
2.  [device](#orgff905d2)
    1.  [Show status for all devices](#orgaeb9fbe)
    2.  [Show details of device(s)](#orgae53f42)
    3.  [Set device properties.](#org6f496be)
    4.  [Connect the device.](#orgaffc473)
    5.  [Disconnect the device](#orgb3468d6)
    6.  [Modify one or more properties on an active device](#org9e3f7f0)
    7.  [Delete the software devices](#org3a0a4d2)
    8.  [wifi](#org6e7c0c3)
3.  [general](#orge565ebb)
    1.  [Show overall status of NetworkManager.](#org046a109)
4.  [networking](#orgff5d29a)
    1.  [Switch networking on.](#orgba518ee)
    2.  [Switch networking off.](#orge5ea632)
    3.  [Get network connectivity state.](#org91fb9f2)
5.  [radio](#orgacb06bf)
    1.  [Get status of **all** radio switches, or turn them on/off.](#orge60fc31)
    2.  [Get status of **Wi-Fi** radio switch, or turn it on/off.](#orgb531cb7)
    3.  [Get status of **mobile broadband** radio switch, or turn it on/off.](#org5a9ff17)

<div class="abstract">
This document contains the essential information for using
***<span class="underline">NetworkManager</span>***, a basic instruction guide set for operating with
***nmcli***.

For fully detailed information, please see ***man nmcli***.

</div>


<a id="orgafae9fd"></a>

# connection


<a id="org3b34431"></a>

## show


<a id="orgdde811c"></a>

## up


<a id="org17ac69d"></a>

## down


<a id="orge2ff720"></a>

## add


<a id="org0e00cc1"></a>

## modify


<a id="org7b48fb8"></a>

## clone


<a id="org3d223ff"></a>

## edit


<a id="orge5b8a71"></a>

## delete


<a id="org8fd8a9b"></a>

## monitor


<a id="org80c0089"></a>

## reload (reload all connection files from disk)


<a id="orga2d6e8b"></a>

## load <filename> (not internanlly on nmcli)


<a id="org9e35460"></a>

## import [&#x2013;temporary] type <type> file <file to import>


<a id="orgfb1cb3b"></a>

## export [id | uuid | path] <ID> [<output file>]


<a id="orgff905d2"></a>

# device


<a id="orgaeb9fbe"></a>

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


<a id="orgae53f42"></a>

## Show details of device(s)

    nmcli dev show [<ifname>]

The command lists details for all devices, or for a given device.


<a id="org6f496be"></a>

## Set device properties.

    nmcli dev set [ifname] ifname [autoconnect {yes | no}]
    nmcli dev set [ifname] ifname [managed {yes | no}]


<a id="orgaffc473"></a>

## Connect the device.

    nmcli dev connect [<ifname>]

NetworkManager will try to find a suitable connection that will be
activated.

It will also consider connections that are not set to
auto-connect. 


<a id="orgb3468d6"></a>

## Disconnect the device

    nmcli dev disconnect [<ifname>]

The command disconnects the device and prevents it from
auto-activating further connections without user/manual
intervention. 


<a id="org9e3f7f0"></a>

## Modify one or more properties on an active device

Modify one or more properties currently active on the device without modifying
the connection profile. The changes have immediate effect. 

    nmcli dev delete [<ifname>]

> ****<span class="underline">NOTE:</span>**** The changes do not modify the connection profile!


<a id="org3a0a4d2"></a>

## Delete the software devices

    nmcli dev delete [<ifname>]

The command removes the interfaces. It only works for software
devices like:

-   Bonds
-   Brigdes
-   etc.

> ****<span class="underline">NOTE:</span>**** Hardware devices cannot be deleted by the command!


<a id="org6e7c0c3"></a>

## wifi


<a id="orge565ebb"></a>

# general


<a id="org046a109"></a>

## Show overall status of NetworkManager.

    nmcli gen status

'status' is the default action, which means 'nmcli gen' calls
'nmcli gen status'


<a id="orgff5d29a"></a>

# networking


<a id="orgba518ee"></a>

## Switch networking on.

    nmcli net on


<a id="orge5ea632"></a>

## Switch networking off.

    nmcli net off


<a id="org91fb9f2"></a>

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


<a id="orgacb06bf"></a>

# radio


<a id="orge60fc31"></a>

## Get status of **all** radio switches, or turn them on/off.

    nmcli radio all [on | off]


<a id="orgb531cb7"></a>

## Get status of **Wi-Fi** radio switch, or turn it on/off.

    nmcli radio wifi [on | off]


<a id="org5a9ff17"></a>

## Get status of **mobile broadband** radio switch, or turn it on/off.

    nmcli radio wwan [on | off]

