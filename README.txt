CEFUtils - Common Event Format Extraction Utilities

The common event format is an event exchange syntax. A sample message formatted as CEF looks as follows:

CEF:0|Splunk|Test|1.0|signature:2|Test event|5|src_addr=10.0.0.0 dest_addr=20.0.0.2 src_port=32122 dest_port=80

It consists of a common prefix that always has to be present, followed by a flexible key-value extension. 

In order to parse CEF data correctly in Splunk, this add-on provides 4 transforms:
 * cefHeaders 		- use it to extract CEF headers
 * cefKeys    		- fixes multiword value extraction (by default Splunk would only extract key's values up to the first whitespace character)
 * cefLabelBeforeKey	- for custom field mapping, replacement for deprecated 'cefkv' command. For example those transforms will extract
   cefLabelAfterKey       key-value pair  custom_label="custom string value" from the following CEF event:
                          CEF:0|Splunk|Test|1.0|signature:2|Test event|5|cs1=custom string value cs1Label=custom label

USAGE
See props.conf example supplied with the app

Thanks: 
This add-on based on "Common Event Format - Field Extractions" by raffy and "jsonutils" by vbumgarner

Release Notes:

v1.5.4 
 * Added eventgen.conf to generate sample data for app tesing

v1.5.0
 * Added cefLabelBeforeKey,cefLabelAfterKey transforms
 * Deprecated cefkv command

v1.2.4
  * Fixed timestamp extraction (thanks to EhudB for bringing the bug to my attention)
