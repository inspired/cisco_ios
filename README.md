# Cisco Networks

[![GitHub contributors](https://img.shields.io/github/contributors/inspired/cisco_ios.svg)]()


## Table of Contents

### OVERVIEW

- About the Cisco Networks app
- Release notes
- Performance benchmarks
- Support and resources

### INSTALLATION

- Hardware and software requirements
- Installation steps 
- Deploy to single server instance
- Deploy to distributed deployment
- Deploy to distributed deployment with Search Head Pooling
- Deploy to distributed deployment with Search Head Clustering
- Deploy to Splunk Cloud 


### USER GUIDE

- Key concepts
- Data types
- Lookups
- Configure the Cisco Networks app
- Troubleshooting
- Upgrade
- Example Use Case-based Scenario

---
### OVERVIEW

#### About the Cisco Networks app

| Author | Mikael Bjerkeland |
| --- | --- |
| App Version | 2.5.0 |
| Vendor Products | Cisco Catalyst, ASR, ISR, Nexus, CRS and other IOS based switches, Wireless LAN Controller   |
| Has index-time operations | False |
| Create an index | False |
| Implements summarization | True: Data model, data model acceleration by default |

The Cisco Networks app allows a Splunk® Enterprise administrator to analyze and visualize data from Cisco IOS and WLC devices, helping investigate the root causes of problems, trends and providing insight into your Cisco environment.

##### Scripts and binaries

No scripts or binaries are included.

#### Release notes

##### About this release

Version 2.5.0 of the Cisco Networks app is compatible with:

| Splunk Enterprise versions | 6.5 |
| --- | --- |
| CIM | 4.6, 4.5, 4.4, 4.3, 4.2, 4.1, 4.0 |
| Platforms | Platform independent |
| Vendor Products | Cisco Catalyst, ASR, ISR, Nexus, CRS and other IOS based switches, Wireless LAN Controller|
| Lookup file changes | cisco_ios_messages.csv |

##### New features

Cisco Networks includes the following new features:

- Multi tenancy support (COMMERCIAL USERS ONLY)

##### Fixed issues

Version 2.5.0 of the Cicso Networks app fixes the following issues:

- Various small fixes removing deprecated features

##### Known issues

Version 2.5.0 of the Cisco Networks app has the following known issues:

- Unable to return raw events in Splunk Enterprise 6.3.0 using searches such as sourcetype=cisco:ios unless in Fast Mode. This is due to a bug in Splunk Enterprise 6.3.0 and the Vendor Message Lookup CSV file. Workarounds (choose one): 
  - Upgrade your servers to Splunk Enterprise 6.3.1 or higher
  - Rename TA-cisco_ios/default/limits.conf.example as TA-cisco_ios/default/limits.conf your Search Head and Indexers

##### Third-party software attributions

Version 2.5.0 of the Cisco Networks app incorporates the following third-party software or libraries.

- None

#### Performance benchmarks

No performance tests have been performed, but the app has proved to perform well with the Splunk reference hardware running Splunk version 6.2 on daily data volumes of up to 200 GB in distributed environments, but will most likely work in larger distributed environments.

##### Support and resources

**This app is community supported on a best effort basis. In case you have needs for professional support billed by the hour, please contact the author.

* Access questions and answers specific to the Cisco Networks app at http://answers.splunk.com/app/questions/1352.html

## INSTALLATION AND CONFIGURATION

### Hardware and software requirements

#### Hardware requirements

Cisco Networks supports the following server platforms in the versions supported by Splunk Enterprise:

- Windows 7, 8, and 8.1 (64-bit)
- Windows Server 2008, 2008 R2, 2012 and 2012 R2 (64-bit)
- Windows 7, and 8 and 8.1 (32-bit)
- Windows Server 2008 (32-bit)
- 2.6+ kernel Linux distributions (64-bit)
- 2.6+ kernel Linux distributions (32-bit)
- Solaris 10, 11 (64-bit)
- Solaris 10, 11 (SPARC)
- OSX 10.8 (Intel)
- OSX 10.9 (Intel)
- OSX 10.10 (Intel)
- FreeBSD 8, and 9 (64-bit)
- AIX 6.1, 7.1

#### Software requirements

To function properly, Cisco Networks requires the following software:

- Cisco Networks Add-on (TA-cisco_ios), 2.5.0 or higher

#### Splunk Enterprise system requirements

Because this add-on runs on Splunk Enterprise, all of the [Splunk Enterprise system requirements](http://docs.splunk.com/Documentation/Splunk/latest/Installation/Systemrequirements) apply.

#### Download

Download the Cisco Networks app at https://apps.splunk.com/app/1352/.

#### Installation steps

To install and configure this app on your supported platform, follow these steps:

1. In your Splunk Enterprise web interface, click on App(s) -> Manage Apps
1. Click on Install app from file
1. Select the file you downloaded, Click Upload, optionally selecting Upgrade app if you are upgrading from an earlier version. Restart Splunk if required

##### Deploy to single server instance

Follow these steps to install the app in a single server instance of Splunk Enterprise:

1. In your Splunk Enterprise web interface, click on App(s) -> Manage Apps
1. Click on Install app from file
1. Select the file you downloaded, Click Upload, optionally selecting Upgrade app if you are upgrading from an earlier version. Restart Splunk if required

##### Deploy to distributed deployment

**Install to search head**

1. In your Splunk Enterprise web interface, click on App(s) -> Manage Apps
1. Click on Install app from file
1. Select the file you downloaded, Click Upload, optionally selecting Upgrade app if you are upgrading from an earlier version. Restart Splunk if required

**Install to indexers**

This app should not be installed on indexers.

**Install to forwarders**

This app should not be installed on forwarders.

##### Deploy to distributed deployment with Search Head Pooling
Follow the same steps as *Install to search head*. In addition you should disable data model acceleration for the Cisco IOS Event data model OR scheduling in general on all but one search head.
##### Deploy to distributed deployment with Search Head Clustering
Follow the same steps as *Install to search head*.
##### Deploy to Splunk Cloud
Unknown



## USER GUIDE

### Key concepts for Cisco Networks

The Splunk Admin must know how to configure data inputs and how Splunk stores and searches data in different indexes and how roles apply to what indexes are searched. 


### Data types

This app provides search-time knowledge for the following types of data from Cisco IOS variants, NX-OS and WLC:

**Search-time**

- cisco:ios - Syslog events from your devices
- Cisco:SmartCallHome - Inventory data from your devices


These data types support the following Common Information Model data models:


| Source Type | CIM Data Models |
| --- | --- |
| cisco:ios | Change Analysis<br/>Authentication<br/>Network Traffic<br/>|
| Cisco:SmartCallHome | Inventory|

### Lookups

The Cisco Networks app contains 3 lookup files.

**cisco_ios_facility_categories.csv**

Provides the vendor's description of an event category based on the event's facility.

- File location: lookups/cisco_ios_facility_categories.csv
- Lookup fields: facility, vendor_category
- Lookup contents: See the file contents

**cisco_ios_messages.csv**

Provides the vendor's recommended actions, explanations and message texts based on the event's facility, severity_id and mnemonic,

- File location: lookups/cisco_ios_messages.csv
- Lookup fields: facility, severity_id, mnemonic, vendor_message_text, vendor_explanation, vendor_recommended_action
- Lookup contents: See the file contents

**cisco_ios_variable_representations.csv**

Not yet in use, but may be used to look up the variables from vendor_message_text to get a friendly explanation of the type of variable

- File location: lookups/cisco_ios_variable_representations.csv
- Lookup fields: vendor_variable_field, vendor_variable_type_of_information
- Lookup contents: See the file contents

### Configure Cisco Networks

Details of any configurations a user must make in order to get the app running.

### Troubleshoot Cisco Networks

***No data seen in the app***

***Cause***

* Cicso devices not configured or incorrectly configured for logging
* Cisco Networks Add-on not installed

***Resolution***
* Check the device configuration
* Install the Cisco Networks Add-on

***Not seeing any inventory information?***

The app needs a feature called Cisco Smart Call Home (SCH) to be enabled on the devices.

***Cause***
* Smart Call Home Input not enabled
* Devices not configured to send Smart Call Home events at specific intervals
* ip http client source-interface SOURCE_INTERFACE not set on your device

***Resolution***
* Enable a TCP input for Smart Call Home using the instructions in the app's Help page
* Enable Smart Call Home logging on your devices using the instructions in the app's Help page.
* Set the correct source interface on your devices.

### Upgrade Cisco Networks
1. In your Splunk Enterprise web interface, click on App(s) -> Manage Apps
1. Click on Install app from file
1. Select the file you downloaded, Click Upload, selecting Upgrade app. Restart Splunk if required

### Example Use Case ###
* Find flapping ports
* View configuration changes
* View access list logs
* View events by Cisco access point MAC address
* View top events by device model, software and hostname
* Identify rare and common log messages by facility, mnemonic and device type
