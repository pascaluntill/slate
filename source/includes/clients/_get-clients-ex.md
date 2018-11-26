# GetClientsEx

Reads the list of Clients using additional filters. 

## The GetClientsEx Response 

See [The Client Object](#the-client-object)

## The GetClientsEx Request

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
Extra | [ExtraInfo] | Optional | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`id` | Long | Searches for active Client by Id (ModifiedSince is ignored when this extra is added).
`is_active` | 1 / 0 / -1 | 1: Active only, 0: Inactive only, -1: Both active and inactive.
`smartcard_uid` | String | Searches Clients by smartcard UID (ModifiedSince is ignored when this extra is added).
