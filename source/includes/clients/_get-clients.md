# GetClients

Read the list of Clients.

## The Client Object

> Client Object:

```xml
<item xsi:type="NS3:TClient">
    <Id xsi:type="xsd:long">65000353067</Id>
    <Number xsi:type="xsd:int">1</Number>
    <Name xsi:type="xsd:string">John Doe</Name>
    <Country xsi:type="xsd:string">United States</Country>
    <Phone xsi:type="xsd:string">585-924-1525</Phone>
    <Fax xsi:type="xsd:string"/>
    <Email xsi:type="xsd:string">brabtleater1957@rhyta.com</Email>
    <Website xsi:type="xsd:string"/>
    <Address xsi:type="xsd:string">1951 Cherry Ridge Drive</Address>
    <Info xsi:type="xsd:string"/>
    <BirthDate xsi:type="xsd:dateTime">1995-03-07T00:00:00.000+01:00</BirthDate>
    <CardNumber xsi:type="xsd:string">MjY3MDIwNjQ2OTU0RA==</CardNumber>
    <Code xsi:type="xsd:string"/>
    <OnInvoice xsi:type="xsd:boolean">true</OnInvoice>
    <PriceActive xsi:type="xsd:boolean">true</PriceActive>
    <Price xsi:type="xsd:long">65000333282</Price>
    <PromotionPrice xsi:type="xsd:long">0</PromotionPrice>
    <AccountBalance xsi:type="xsd:double">0</AccountBalance>
    <AccountLimit xsi:type="xsd:double">0</AccountLimit>
    <IsSharedAccount xsi:type="xsd:boolean">false</IsSharedAccount>
    <SharedAccount xsi:type="xsd:string"/>
    <SavePoints xsi:type="xsd:int">1636</SavePoints>
    <SaveAmount xsi:type="xsd:int">0</SaveAmount>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[4]">
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">last_update</Key>
            <Value xsi:type="xsd:string">2018.11.20 10:36:14</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">is_active</Key>
            <Value xsi:type="xsd:string">1</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">country_id</Key>
            <Value xsi:type="xsd:string">65000353071</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">smartcard_uid</Key>
            <Value xsi:type="xsd:string">48C44B8C</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
    </Extra>
</item>
```

Parameter | Type | Description
----------| -----| -----------
Id | Long | Internal Id of this Client
Number | Integer | Number of this Article
Name | String | Name of this Article
Country | String | Country name (Id of country is sent in Extras)
Phone | String | Client phone
Fax | String | Client fax
Email | String | Client email
Website | String | Client website
Address | String | Client address
Info | String | Client info
BirthDate | Timestamp | Client birthdate
CardNumber | String | Client cardnumber (Base64-encoded)
Code | String | Client code
OnInvoice | Boolean | True if Client is allowed to consume on invoice
PriceActive | Boolean | True if Client has a special price level assigned
PromotionPrice | Long | Returns the special price level Id assigned to this Client
AccountBalance | Decimal | Current Client balance
AccountLimit | Decimal | Client limit
IsSharedAccount | Boolean | True if this Client belongs to a Shared Account
SharedAccount | String | Shared Account name
SavePoints | Integer | Current savepoints balance
SaveAmount | String | Current saveamount balance
Extra | ExtraInfo[] | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description | Read | Write
--- | ----- | ----------- | ---- | -----
`is_active` | 1/ 0 | Activity flag. | Always | Optional, default = 1.
`country_id` | Long | Id of Country. | Always | Optional
`last_update` | Timestamp | When client was updated for the last time. | Always | -
`smartcard_uid` | String (Hex) | Smartcard UID. | If not null | Optional

## The GetClients Request

> GetClients Request:

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
