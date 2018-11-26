# UpdateClients

Create or update clients in database. When Id is other than 0, client is updated, else new client is created.
When using this request, the fields AccountBalance and SavePoints are not updated. Use the ClientDeposit request for updating the AccountBalance.

## The Client Object

See [The Client Object](#the-client-object)

## The UpdateClients Response

> UpdateClients Response:

```xml
<return xsi:type="NS2:TUpdateClientsResponse">
    <AddedClients xsi:type="xsd:int">1</AddedClients>
    <UpdatedClients xsi:type="xsd:int">1</UpdatedClients>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
        <item xsi:type="NS3:TExtraInfo">
           <Key xsi:type="xsd:string">result_ids</Key>
           <Value xsi:type="xsd:string">20000156720, 20000156715</Value>
           <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
   </Extra>
</return>
```

Parameter | Type | Description
----------| ---- | -----------
AddedClients | Integer | Number of added Clients
UpdatedClients | Integer | Number of updated Clients
Extra | [ExtraInfo] | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`result_ids` | String | Comma separated list of Id's of created and/or updated Clients. The number of Id's returned is equal to the number of Clients sent in the request.

## The UpdateClients Request

> UpdateClients Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:UpdateClients soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TUpdateClientsRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <Clients xsi:type="urn1:TClientsArray" soapenc:arrayType="urn1:TClient[1]">
	            <item xsi:type="NS3:TClient">
				<Id xsi:type="xsd:long">0</Id>
				<Name xsi:type="xsd:string">John Doe</Name>
	    			<Phone xsi:type="xsd:string">585-924-1525</Phone>
	    			<Email xsi:type="xsd:string">brabtleater1957@rhyta.com</Email>
	    			<Address xsi:type="xsd:string">1951 Cherry Ridge Drive</Address>
	    			<BirthDate xsi:type="xsd:dateTime">1995-03-07T00:00:00.000+01:00</BirthDate>
	    			<CardNumber xsi:type="xsd:string">MjY3MDIwNjQ2OTU0RA==</CardNumber>
	    			<OnInvoice xsi:type="xsd:boolean">true</OnInvoice>
	    			<Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="NS3:TExtraInfo[1]">
	    				<item xsi:type="NS3:TExtraInfo">
	            			<Key xsi:type="xsd:string">smartcard_uid</Key>
	            			<Value xsi:type="xsd:string">48C44B8C</Value>
	            			<Extra xsi:type="SOAP-ENC:Array" soapenc:arrayType="NS3:TExtraInfo[0]"/>
	        			</item>
	    			</Extra>
	            </item>
	            <item xsi:type="NS3:TClient">
				<Id xsi:type="xsd:long">20000156715</Id>
				<Name xsi:type="xsd:string">Jane Doe</Name>
	    			<Phone xsi:type="xsd:string">314-657-2903</Phone>
	    			<Email xsi:type="xsd:string">broas1937@einrot.com</Email>
	    			<Address xsi:type="xsd:string">3618 Hawks Nest Lane</Address>
	    			<BirthDate xsi:type="xsd:dateTime">1999-06-15T00:00:00.000+02:00</BirthDate>
	    			<OnInvoice xsi:type="xsd:boolean">false</OnInvoice>
	            </item>
            </Clients>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:UpdateClients>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
Clients | [[Client]](#the-client-object) | Mandatory | List of Clients to be added or updated
