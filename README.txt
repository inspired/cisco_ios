Copyright (C) 2013 Mikael Bjerkeland. All Rights Reserved.

App:              Cisco Networks App for Splunk Enterprise (previously Cisco IOS)
Current Version:  2.1.0
Last Modified:    2014-10-30
Splunk Version:   6.1+
Author:           Mikael Bjerkeland
CIM Compliance:   4.0 (Authentication, Change Analysis, Inventory, Network Traffic)

The Cisco IOS app includes dashboards, data models and logic for analyzing data from Cisco IOS, IOS XE, IOS XR and NX-OS devices

Install this app on your search head. Install the TA-cisco_ios app on your search head AND indexers/heavy forwarders.

Supported Cisco Devices:
*  Cisco Catalyst series switches (2960, 3650, 3750, 4500, 6500, 6800, 7600 etc.)
*  Cisco ASR - Aggregation Services Routers (900, 1000, 5000, 9000 etc.)
*  Cisco ISR - Integrated Services Routers (800, 1900, 2900, 3900, 4451 etc.)
*  Cisco Nexus Data Center switches (1000V, 2000, 3000, 4000, 5000, 6000, 7000, 9000 etc.)
*  Cisco Carrier Routing System
*  Other Cisco IOS based devices (Metro Ethernet, Industrial Ethernet, Blade Switches, Connected Grid etc.)

Preliminary support for:
*  Cisco WLC - WLAN Controller

Please contact me on Splunk Base if there is anything you would like to see in this app.


++ What's New

+++ 2.1.0 (2014-10-30)
Features:
* NAME CHANGED TO Cisco Networks App for Splunk Enterprise. Remove your old Cisco IOS app directories (cisco_ios and TA-cisco_ios)
* More filters in the dashboards
* DOT1X now with more graphs


+++ 2.0.0 (2014-09-19)
Features: 
* CIM 4.0 Compliance. MANY fields have changed names. You may need to change your custom searches
* Lots of new features. Dashboards have been fixed up, drilldowns enhanced, more Smart Call Home support
MAKE SURE YOU REMOVE EARLIER VERSIONS OF THE CISCO IOS APP BEFORE INSTALLING THIS VERSION!

+++ 1.6.0 (2014-07-21)
Features:
* Device/s dashboard changed. Includes data collected with Smart Call Home.

Bug fixes:
* Routing dashboard no longer auto refreshes
* Drilldown now works better in the Event Analysis!
* CSV file moved out of the TA to the main app

+++ 1.5.0 (2014-05-08)
Features:
* Added more fields to the data model
* Added an Event Analysis Dashboard to Auditing using the new lookups from TA-cisco_ios.
* Auditing -> Best Practice Deviations has been removed
* Map visualizations added to Security -> ACL

+++ 1.3.2 (2014-04-23)
Added a new overview page (overview_postprocess_searches_no_pivot)
as a workaround for users having problems with Data Model powered
searches not displaying (Splunk defect SPL-83310) - THIS IS SLOW!

Bug fixes:
* Removed some unneccessary files.
* Moved Performance panels into a common performance_dashboard
Features:
* Preliminary support for IP SLA events (Performance dashboard)
* Optical transceiver attenuation monitoring (Switching -> Dashboard)

+++ 1.3.1 (2014-04-17)
Bug fixes:
* 802.1x euthentications now renamed to 802.1x events, no longer a child of "User"
* Various small changes

+++ 1.3.0 (2014-04-04)
Features: 
* Now relies on Splunk 6! Data models are in use
Bug fixes:
* Device dashboard now fixed

+++ 1.2.1 (2014-02-17)
Features: Started work on a new Device dashboard

+++ 1.2.0 (2014-01-09)
Features:
* Moved props, transforms etc to the TA. 
  YOU NOW NEED THE TA ON YOUR SEARCH HEAD ALONGSIDE THE APP!

+++ 1.1.6 (2013-10-10)
Features:
* Started creating Data Models for Splunk 6.0

Bug fixes:
* Top ACL logs now counts num_packets

+++ 1.1.5 (2013-09-20)
Features:
* IOS XR support

+++ 1.1.4 (2013-08-27)
Features:
* Added a few Nexus snacks

+++ 1.1.3 (2013-08-12)
Bug fixes:
* Fixed bug that also captured events that were in the body of ACS events
* Now captures events from switches with a subfacility

+++ 1.1.2 (2013-07-22)
Features:
* Added wireless - more to come

+++ 1.1.1 (2013-05-27)
Features:
* Add a reliable_time=true/false based on presence of *:
* More CIM compliance
* Fixed ACL logging for log-input

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

Sourcetype(s):              cisco:ios
Supported Technologies:     Cisco IOS, IOS-XE, NX-OS, IOS XR devices
Supported Splunk versions:  6.1+

++ Installation Instructions

The Cisco IOS app can be downloaded, installed, and configured to receive Cisco IOS data by either using the Splunk app setup screen or by manually installing and configuring the app.
This app reads from the sourcetype cisco:ios defined in TA-cisco_ios


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
logging userinfo
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

5. (OPTIONAL) For MAC move notifications, STP logging, IP SLA logging etc:

--
mac address-table notification mac-move
spanning-tree logging
ip sla logging traps
ip dhcp limit lease log
ip dhcp conflict logging
ip nat log translations syslog
xconnect logging pseudowire status
--

6. (OPTIONAL) For DHCP utilization logging on your devices, do this for each pool
--
utilization mark high 80 log
--

7. (OPTIONAL) Nexus ACL logging
--
logging level acllog 6
acllog match-log-level 6
logging logfile messages 6
--

++ TODO

* IOS DHCP binding logging (file monitoring)
* Facility-Mnemonic by software version, by series, by model?
* Check drilldown for event analysis - cannot drilldown on specific host/event for recommended action/explanation
* eventtype="cisco_ios-mac_flapping"  mnemonic=MACFLAP_NOTIF (src_mac, vlan osv funker ikke)

++ Getting Help

* Consult Splunk Answers
* Contact the author: mikael@bjerkeland.com
