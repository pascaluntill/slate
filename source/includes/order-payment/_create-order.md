# CreateOrder

Creates an Order.

## The OrderItem Object

> OrderItem Object:

```xml
<item xsi:type="urn:TOrderItem">
    <ItemNumber>1</ItemNumber>
    <ArticleId>5000001716</ArticleId>
    <OrderItemType>0</OrderItemType>
    <Text></Text>
    <ManualPrice>0</ManualPrice>
    <Quantity>1</Quantity>
    <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
</item>
```

Parameter | Type | Status | Description
----------| ---- | ------ | -----------
ItemNumber | Integer | Mandatory | Sequential order item number
ArticleId | Long | Mandatory | Id of Article to order. Specify '0' when OrderItemType = 6
OrderItemType | Integer | Mandatory | Type of order item
Text | String | Optional | Text when OrderItemType = 6
ManualPrice | Decimal | Optional | Only required when the Article has ManualPrice = true
Quantity | Integer | Mandatory | Quantity of ordered items. Note: Only valid when OrderItemType = 0 or 5
Extra | [ExtraInfo] | Optional | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`last` | - | Add this extra when this item is the last of a must-have option that has "Compose" enabled and the next item is also a must-have option.

## The CreateOrder Request

> CreateOrder Request:

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
            <Items soapenc:arrayType="urn1:TOrderItem[4]" xsi:type="urn1:TOrderItemArray" xmlns:urn1="urn:TPAPIPosTypesU">
                <item xsi:type="urn:TOrderItem">
				    <ItemNumber>1</ItemNumber>
				    <ArticleId>5000001716</ArticleId>
				    <OrderItemType>0</OrderItemType>
				    <Text></Text>
				    <ManualPrice>0</ManualPrice>
				    <Quantity>1</Quantity>
                </item>
                <item xsi:type="urn:TOrderItem">
				    <ItemNumber>2</ItemNumber>
				    <ArticleId>5000012095</ArticleId>
				    <OrderItemType>0</OrderItemType>
				    <Text></Text>
				    <ManualPrice>0</ManualPrice>
				    <Quantity>1</Quantity>
                </item>
		    </Items>
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
Items | [OrderItem] | Mandatory | Items to be ordered
ClientId | Long | Optional | Id of the Client to assign to the transaction
Extra | [ExtraInfo] | Optional | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`extraN` | 1..10 | These fields are available in the unTill datasets "Order" (screens/tickets) and "Bills" (reports). They will also be returned in the "Extra" field of the GetActiveOrders response.
`OifDate` | YYYYMMDD-HHNN | When specified, an Order in the Future is created.
`OifDepositAmount` | Cents | Deposit amount for the Order in the Future, to be specified in cents.
`OifDepositPaymentModeId` | Id | Id of the payment mode to use for the Order in the Future.
