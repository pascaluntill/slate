# GetSalesAreasInfo

Returns a list of the active Sales Areas in the unTill database.

## The SalesAreaInfo Object

> SalesAreaInfo Object:

```xml
<item xsi:type="NS3:TSalesAreaInfo">
    <SalesAreaId xsi:type="xsd:long">5000000208</SalesAreaId>
    <SalesAreaNumber xsi:type="xsd:int">1</SalesAreaNumber>
    <SalesAreaName xsi:type="xsd:string">Restaurant</SalesAreaName>
    <PriceId xsi:type="xsd:long">5000000206</PriceId>
    <Tables xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTableRange[15]">
        <item xsi:type="NS3:TTableRange">
            <FromTable xsi:type="xsd:int">1</FromTable>
            <ToTable xsi:type="xsd:int">100</ToTable>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TTableRange">
            <FromTable xsi:type="xsd:int">1001</FromTable>
            <ToTable xsi:type="xsd:int">1100</ToTable>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
    </Tables>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
SalesArea | Long | Internal Id of this Sales Area
SalesAreaNumber | Integer | Number of this Sales Area
SalesAreaName | String | Name of this Sales Area
PriceId | Long | Id of the active Price Level for this Sales Area
Tables | [TableRange] | List of Table Ranges for this Sales Area 
Extra | [ExtraInfo] | List of extra fields

## The GetSalesAreasInfo Request

> GetSalesAreasInfo Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetSalesAreasInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetSalesAreasInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetSalesAreasInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
