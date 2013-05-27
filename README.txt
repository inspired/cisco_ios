Copyright (C) 2013 Mikael Bjerkeland, Datametrix AS. All Rights Reserved.

App:               	Cisco IOS
Current Version:	1.1.1
Last Modified:		2013-05-27
Splunk Version:		4.2.x, 4.3.x, 5.0.x
Author:			Mikael Bjerkeland
Dependencies:		Sideview Utils

The Cisco IOS app sets different Cisco specific fields used for identifying data from Cisco IOS, IOS-XE, NX-OS
Install this app on your search head. Install the TA-cisco_ios app on your indexers

Please contact me on Splunk Base if there is anything you would like to see in this app.


++ What's New

+++ 1.1.1 (2013-05-27)
Features:
* Add a reliable_time=true/false based on presence of *:

+++ 1.1.0 (2013-05-16)
Features:
* Smart Install view added to Auditing
* Added FHRP to Switching (no extractions yet)

+++ 1.0.9 (2013-04-26)
Features: 
* Moved a few things around
* Etherchannel added to performance

+++ 1.0.8 (2013-04-23)
Features:
* Added Switching nav 
* Added Security nav
* Added extractions for DOT1X - this will be getting transaction tracking soon
Bug fixes:
* Fixed general extraction to handle integers in facility and mnmenonic

+++ 1.0.7 (2013-04-17)
Features:
* Regex support for WLC
* Added stack manager

+++ 1.0.6 (2013-04-12)
Features:
* Now extracts login successes and failures

+++ 1.0.5 (2013-04-05)
Features:
* Added device restart/boot table to Auditing dashboard. Thanks jaoui

+++ 1.0.4 (2013-04-04)
Bug fixes:
* Fixed subfacility extraction

+++ 1.0.3 (2013-03-28)
Bug fixes:
* Minor under the hood improvements

+++ 1.0.2 (2013-03-26)
Features:
* More extractions added, not yet in any views
Bug fixes:
* device_time extraction has been re-worked a bit to avoid pulling in the wrong values

+++ 1.0.1 (2013-03-25)
Bug fixes:
* Better time matching in place for the time drift view. Now matches numerous formats and is fast, but shows all results

+++ 1.0.0 (2013-03-21)
Features:
* The app has been split up into two parts, one App for the search head and a TA for indexers
* Added BGP, EIGRP and MPLS LDP extractions
* Added time drift in Auditing
 * Currently requires the device time to be in this format Mar 21 19:29:47.320 CET or Mar 21 19:29:47.320
 * The search is quite slow
* Added tags
* Added time picker for each view
* Host search added for config change transactions

+++ 0.1.7 (2013-03-05)
Features:
* OSPF adjacency change regex added: adjchg
* OSPF adjacency change panel added to Routing -> Dashboard
* CDP neighbor add/remove eventtypes and extractions for Nexus switches added
* CDP neighborhood panel for Nexus switches added to Datacenter -> Dashboard
* Added all events to index "ios"

Bug fixes:
* Interface matching fixed, didn't capture multi slot/chassis interfaces
* CIM compliance for src_ip, src_vlan and dest_vlan

+++ 0.1.2 (2013-02-03)
Initial release
Features:
* Identify flapping ports
* Identify error disabled interfaces
* Show syslog severity distribution
* Identify top and rare messages (mnemonics)
* Identify ACL hits
* Identify diagnostic messages
* Change Management and see system reloads
* Identify DSL bandwidth performance (tested on 8xx routers)
* Identify duplex and Native VLAN mismatches


++ Application Details

Sourcetype(s):            cisco:ios
Supported Technologies:   Cisco IOS, IOS-XE and NX-OS devices


++ Installation Instructions

The Cisco IOS app can be downloaded, installed, and configured to receive Cisco IOS data by either using the Splunk app setup screen or by manually installing and configuring the app.
This app reads from the sourcetype cisco_ios defined in TA-cisco_ios

NOTE: This app might not work with the Splunk for Cisco Security Suite as it specifies a similar cisco:ios sourcetype.

+++ Setup and configuration

1. Install in $SPLUNK_HOME/etc/apps/cisco_ios

2. Restart Splunk


+++ Optional steps
1. For better change auditing add the following to the running-configuration on your devices:

--
archive
 log config
  logging enable
  logging size 200
  notify syslog contenttype plaintext
  hidekeys
!
login on-failure log
login on-success log
!
--

This ensures that all run commands are logged for Change Management. We sort them by the IOS event_id
See Auditing -> Configuration change transactions


2. If you do not want to show ACL hits by local management IPs, add the IPs or subnets to lookups/cisco_ios_acl_excluded_ips.csv


3. For the Auditing -> Time drift view to work correctly, add something along the following on your devices:

--
service timestamps log datetime msec localtime show-timezone
--

4. Add something along the following to monitor interface changes:

--
logging event trunk-status global
logging event link-status global
!
interface ra Gi1/0/1 - 52
 logging event trunk-status
 logging event spanning-tree
 logging event status
!
--


++ TODO

* Add Dot1x stuff to Security
* Add new nav: Switching
* Add summary indexing
* Add paginators for all panels
* Check CIM compliance
* Add tags, i.e. tag=network, tag=authentication
* Add a macro for specifying index to accomodate different users
* Add SNMP extractions

++ Troubleshooting the app



++ Getting Help

* Contact the author: mikael@bjerkeland.com
