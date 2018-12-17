# Order Functions

## GetActiveOrders

Returns a list of the active Orders in the unTill database.

### GetActiveOrders Request

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

### GetActiveOrders Response

> GetActiveOrders Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetActiveOrdersResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetActiveOrdersResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Orders xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TOrderInfo[x]">...</Orders>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetActiveOrdersResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Orders | [[OrderInfo]](#orderinfo) | Array of Orders
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetActiveTableInfo

Returns transaction structure and amounts (total, remaining, extra) for a certain table number.

### GetActiveTableInfo Request

> GetActiveTableInfo Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetActiveTableInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetActiveTableInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <TableNumber xsi:type="xsd:int">27</TableNumber>
            <TablePart xsi:type="xsd:string">a</TablePart>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetActiveTableInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
TableNumer | Integer | Mandatory | Table number to get info from
TablePart | String | Mandatory | Table part to get info from ("a" - "f")

### GetActiveTableInfo Response

> GetActiveTableInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetActiveTableInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetActiveTableInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Transaction xsi:type="NS3:TTurnoverTransaction">...</Transaction>
            <TotalAmount xsi:type="xsd:double">7.7</TotalAmount>
            <RemainingAmount xsi:type="xsd:double">5.7</RemainingAmount>
            <ExtraAmount xsi:type="xsd:double">0</ExtraAmount>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetActiveTableInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Transaction | [TurnoverTransaction](#turnovertransaction) | Transaction structure
TotalAmount | Decimal | Total amount of the transaction
RemainingAmount | Decimal | Remaining amount to be paid
ExtraAmount | Decimal | Extra amount
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## CreateOrder

Creates an Order.

### CreateOrder Request

> CreateOrder Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:CreateOrder soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TCreateOrderRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <TableNumber xsi:type="xsd:int">1</TableNumber>
            <TablePart xsi:type="xsd:string">a</TablePart>
            <ClientName xsi:type="xsd:string"></ClientName>
            <OrderName xsi:type="xsd:string"></OrderName>
            <OrderDescr xsi:type="xsd:string"></OrderDescr>
            <Items soapenc:arrayType="urn1:TOrderItem[2]" xsi:type="urn1:TOrderItemArray" xmlns:urn1="urn:TPAPIPosTypesU">...</Items>
            <Covers xsi:type="xsd:int">2</Covers>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
            <ClientId xsi:type="xsd:long">0</ClientId>
         </Request>
      </urn:CreateOrder>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
TableNumer | Integer | Mandatory | Table number to order on
TablePart | String | Mandatory | Table part to order on ("a" - "f")
ClientName | String | Optional | Client name
OrderName | String | Optional | Order name
OrderDescr | String | Optional | Order description
Covers | Integer | Optional | Number of covers
Items | [[OrderItem]](#orderitem) | Mandatory | Items to be ordered
ClientId | Long | Optional | Id of the Client to assign to the transaction
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`extraN` | 1..10 | These fields are available in the unTill datasets "Order" (screens/tickets) and "Bills" (reports). They will also be returned in the "Extra" field of the GetActiveOrders response
`OifDate` | YYYYMMDD-HHNN | When specified, an Order in the Future is created
`OifDepositAmount` | Cents | Deposit amount for the Order in the Future, to be specified in cents
`OifDepositPaymentModeId` | Id | Id of the payment mode to use for the Order in the Future

### CreateOrder Response

> CreateOrder Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:CreateOrderResponse xmlns:NS2="urn:TPAPIPosIntfU">
         <return xsi:type="NS2:TCreateOrderResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
         </return>
      </NS1:CreateOrderResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)

## NextCourse

Apply next course to table. If no more courses on table, the ReturnCode will be 7 with ReturnMessage: “There are no more courses”.

### NextCourse Request

> NextCourse Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:NextCourse soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TNextCourseRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <TableNumber xsi:type="xsd:int">1</TableNumber>
            <TablePart xsi:type="xsd:string">a</TablePart>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:NextCourse>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
TableNumber | Integer | Mandatory | Table number to apply the next course to
TablePart | String | Mandatory | Table part to apply the next course to ("a" - "f")

### NextCourse Response

> NextCourse Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:NextCourseResponse xmlns:NS2="urn:TPAPIPosIntfU">
         <return xsi:type="NS2:TNextCourseResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
         </return>
      </NS1:NextCourseResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)

## SetTableCourse

Apply certain course to table. When course is not changed because given course is already set, no error will be returned.
If it is unable to set given course for this table, the ReturnCode will be 7 with ReturnMessage: “Unable to change table course to [...]”

### SetTabeCourse Request

> SetTableCourse Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:SetTableCourse soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TSetTableCourseRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <TableNumber xsi:type="xsd:int">1</TableNumber>
            <TablePart xsi:type="xsd:string">a</TablePart>
            <CourseId xsi:type="xsd:long">5000001334</CourseId>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:SetTableCourse>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
TableNumber | Integer | Mandatory | Table number to apply course to
TablePart | String | Mandatory | Table part to apply course to ("a" - "f")
CourseId | Long | Mandatory | Course to apply to the table

### SetTabeCourse Response

> SetTabeCourse Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:SetTableCourseResponse xmlns:NS2="urn:TPAPIPosIntfU">
         <return xsi:type="NS2:TSetTableCourseResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
         </return>
      </NS1:SetTableCourseResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
