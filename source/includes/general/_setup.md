# Setup

## Enabling TPAPI in unTill

To enable TPAPI interface, select “Common Data / Hardware / Computers” in Backoffice Navigation Tree, then open desired workstation and enable the checkbox “Enable TPAPI”.

## Enabling waiter to be available in TPAPI

Each call to the SOAP interface includes a waiter name and a TPAPI Password. To allow the waiter be used in TPAPI calls, a special “TPAPI Password” field must be specified in unTill Backoffice for this waiter. Also, when configuring the TPAPI user, ensure that the “POS password” field is specified and contains only digits.

## TPAPI-POS Entry Point

The TPAPI-POS WSDL consists of the hostname, port and looks like this:

<b>http://&lt;hostname&gt;:&lt;port&gt;/wsdl/ITPAPIPOS</b>

URL example: <a href="http://testapi.untill.com:3063/wsdl/ITPAPIPOS" target="_blank">http://testapi.untill.com:3063/wsdl/ITPAPIPOS</a>

This WSDL can be used to generate a client for the TPAPI web-service on any programming language. The default port is UNTILLSRV_PORT+3 but this may be redefined in untill.ini if required: 
    
<i>[common]<br>
soapport=7777</i>

The default UNTILLSRV_PORT is 3060, if not redefined in untill.ini with “port” setting.<br>

<aside class="warning">Do not specify “soapport” to values in the range of UNTILLSRV_PORT .. UNTILLSRV_PORT+5, because they can be blocked by other unTill services. Only UNTILLSRV_PORT+3 is always reserved for TPAPI.<br><br><center><strong>Please note that each individual location will has its own TPAPI-POS Entry Point.<br>There is no single (cloud) Entry Point which redirects all calls to client instances.</strong></center></aside>
