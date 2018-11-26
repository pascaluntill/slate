# GetPricesInfo

Returns a list of the active Prices in the unTill database.

## The PriceInfo Object

> PriceInfo Object:

```xml
<item xsi:type="NS3:TPriceInfo">
    <PriceId xsi:type="xsd:long">5000000206</PriceId>
    <PriceName xsi:type="xsd:string">Normal</PriceName>
    <HqId xsi:type="xsd:string"/>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
PriceId | Long | Internal Id of this Price
PriceName | String | Name of this Price
HqId | String | Hq Id
Extra | [ExtraInfo] | List of extra fields

## The GetPricesInfo Request

> GetPricesInfo Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetPricesInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetPricesInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetPricesInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
