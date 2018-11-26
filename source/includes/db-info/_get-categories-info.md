# GetCategoriesInfo

Returns a list of the active Categories in the unTill database.

## The CategoryInfo Object

> CategoryInfo Object:

```xml
<item xsi:type="NS3:TCategoryInfo">
    <CategoryId xsi:type="xsd:long">5000000036</CategoryId>
    <CategoryName xsi:type="xsd:string">1.Bar</CategoryName>
    <HqId xsi:type="xsd:string">1.Bar</HqId>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
CategoryId | Long | Internal Id of this Category
CategoryName | String | Name of this Category
HqId | String | Hq Id
Extra | [ExtraInfo] | List of extra fields

## The GetCategoriesInfo Request

> GetCategoriesInfo Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetCategoriesInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetCategoriesInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetCategoriesInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
