# GetActiveOrders

Returns a list of the active Orders in the unTill database.

## The OrderInfo Object

> OrderInfo Object:

```xml
<item xsi:type="NS3:TOrderInfo">
    <TableNumber xsi:type="xsd:int">1</TableNumber>
    <TablePart xsi:type="xsd:string">a</TablePart>
    <OrderName xsi:type="xsd:string">Test</OrderName>
    <CientName xsi:type="xsd:string">John Doe</CientName>
    <OrderDescr xsi:type="xsd:string"/>
    <SalesAreaId xsi:type="xsd:long">5000000208</SalesAreaId>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
TableNumber | Integer | Table number
TablePart | String | Table part
OrderName | String | Order Name
ClientName | String | Name of the client assigned to the Order
OrderDescr | String | Order description
SalesAreaId | Long | Id of the Sales Area
Extra | [ExtraInfo] | List of extra fields

## The GetActiveOrders Request

> GetActiveOrders Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetActiveOrders soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetActiveOrdersRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <SalesAreaId xsi:type="xsd:long">0</SalesAreaId>
         </Request>
      </urn:GetActiveOrders>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
SalesAreaId | Long | Optional | Specify to request Orders of a certain Sales Area only
