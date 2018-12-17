# Client Functions

## GetClients

Read the list of Clients.

### GetClients Request

> GetClients Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetClients soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetClientsRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetClients>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user

### GetClients Response

> GetClients Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetClientsResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetClientsResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Clients xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TClient[x]">...</Clients>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetClientsResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Clients | [[Client]](#client) | List of Clients
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetClientsEx

Reads the list of Clients using additional filters. 

### GetClientsEx Request

> GetClientsEx Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetClientsEx soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetClientsExRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <ModifiedSince xsi:type="xsd:dateTime">2018-10-01T08:00:00+02:00</ModifiedSince>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetClientsEx>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
ModifiedSince | Timestamp | Optional | Specify this value to return only clients added/updated since that date/time
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`id` | Long | Searches for active Client by Id (ModifiedSince is ignored when this extra is added)
`is_active` | 1 / 0 / -1 | 1: Active only, 0: Inactive only, -1: Both active and inactive
`smartcard_uid` | String | Searches Clients by smartcard UID (ModifiedSince is ignored when this extra is added)

### GetClientsEx Response 

> GetClientsEx Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetClientsExResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetClientsResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Clients xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TClient[x]">...</Clients>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetClientsExResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Clients | [[Client]](#client) | List of Clients
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## UpdateClients

Create or update clients in database. When Id is other than 0, client is updated, else new client is created.
When using this request, the fields AccountBalance and SavePoints are not updated. Use the ClientDeposit request for updating the AccountBalance.

### UpdateClients Request

> UpdateClients Request

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
Clients | [[Client]](#client) | Mandatory | List of Clients to be added or updated

### UpdateClients Response

> UpdateClients Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:UpdateClientsResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TUpdateClientsResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <AddedClients xsi:type="xsd:int">1</AddedClients>
            <UpdatedClients xsi:type="xsd:int">1</UpdatedClients>
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
      </NS1:UpdateClientsResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
AddedClients | Integer | Number of added Clients
UpdatedClients | Integer | Number of updated Clients
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key |Description
--- | -----------
`result_ids` | Comma separated String of Id's of created and/or updated Clients. The number of Id's returned is equal to the number of Clients sent in the request

## ClientAccountDeposit

Makes Deposit to Client Account.

### ClientAccountDeposit Request

> ClientAccountDeposit Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:ClientDeposit soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TClientAccountDepositRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <ClientId xsi:type="xsd:long">5000096068</ClientId>
            <PaymentId xsi:type="xsd:long">5000000055</PaymentId>
            <Amount xsi:type="xsd:double">10</Amount>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:ClientDeposit>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
ModifiedSince | Timestamp | Optional | Specify this value to return only clients added/updated since that date/time

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`get_receipt` | - | Instead of printing deposit receipt unTill sends it back in ClientAccountDepositResponse as plain text. The value of ExtraInfo with this key doesn’t matter


### ClientAccountDeposit Response

> ClientAccountDeposit Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:ClientDepositResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TClientAccountDepositResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <OldBalance xsi:type="xsd:double">40.0</OldBalance>
            <NewBalance xsi:type="xsd:double">50.0</NewBalance>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:ClientDepositResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
OldBalance | Decmial | Account balance before deposit
NewBalance | Decimal | Account balance after deposit
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`receipt_text` | String | Receipt in the form of a plain text returned in this ExtraInfo if `get_receipt` has been added in ClientAccountDepositRequest.Extra
