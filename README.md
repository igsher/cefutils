#  CEFUtils - Common Event Format Extraction Utilities Add-on for Splunk Enterprise

The common event format is an event exchange syntax. A sample message formatted as CEF looks as follows:  
`CEF:0|Splunk|Test|1.0|signature:2|Test event|5|src_addr=10.0.0.0 dest_addr=20.0.0.2 src_port=32122 dest_port=80`  
It consists of a common prefix that always has to be present, followed by a flexible key-value extension.

In order to parse CEF data correctly in Splunk, this add-on provides 2 transforms:

In order to parse CEF data correctly in Splunk, this add-on provides 4 transforms:
 * `cefHeaders`           \- use it to extract CEF headers
 * `cefKeys`              \- fixes multiword value extraction (by default Splunk would only extract key's values up to the first whitespace character)
 * `cefLabelBeforeKey`    \- for custom field mapping, replacement for deprecated 'cefkv' command.
 * `cefLabelAfterKey`     \- for custom field mapping, replacement for deprecated 'cefkv' command

This app is also available at <a href="https://splunkbase.splunk.com/app/487">SplunkBase</a>

## Example: 
`cefLabelBeforeKey` and `cefLabelAfterKey` transforms will extract key-value pair  `custom_label="custom string value`" from the following CEF event:
`CEF:0|Splunk|Test|1.0|signature:2|Test event|5|cs1=custom string value cs1Label=custom label`

## Installation in the Distributed Deployment 
 The add-on provides configurations that are used both at index time and at search time, so if you are installing the add-on in the distributed deployment you'll need to install it on the instances running the Parsing Pipeline (Heavy Forwarders or Indexers/Peers) and on the Search Heads. 

## USAGE
See props.conf example supplied with the app

## Credits   
This add-on is partially based on "Common Event Format - Field Extractions" by raffy and "jsonutils" by vbumgarner

## Release Notes:
v1.5.4
 * Added eventgen.conf to generate sample data for app tesing. To be used with <a href="https://splunkbase.splunk.com/app/1924/">Eventgen</a> app

v1.5.0
 * Added cefLabelBeforeKey,cefLabelAfterKey transforms
 * Deprecated cefkv command
