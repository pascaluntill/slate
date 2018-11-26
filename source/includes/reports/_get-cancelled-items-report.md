# GetCancelledItemsReport

Returns the list of articles which have been cancelled (added to an order and then removed by “Cancel” or “Void” button).

## The CancelledItem Object

> CancelledItem Object:

```xml
<item xsi:type="NS3:TCancelledItem">
    <ArticleId xsi:type="xsd:long">5000001722</ArticleId>
    <DateTime xsi:type="xsd:dateTime">2018-11-20T16:30:42.000+01:00</DateTime>
    <UserId xsi:type="xsd:long">5000001377</UserId>
    <TableNo xsi:type="xsd:int">21</TableNo>
    <TablePart xsi:type="xsd:string">a</TablePart>
    <Quantity xsi:type="xsd:int">1</Quantity>
    <Price xsi:type="xsd:double">2</Price>
    <PriceId xsi:type="xsd:long">5000000206</PriceId>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
ArticleId | Long | Article Id
DateTime | Timestamp | Date/time of cancelling the article
UserId | Long | Waiter Id
TableNo | Integer | Table number where the article was cancelled
TablePart | String | Table part where the article was cancelled
Quantity | Integer | Quantity of cancelled articles
Price | Decimal | Id of the Price level
Extra | [ExtraInfo] | List of extra fields

## The GetCancelledItemsReport Request

> GetCancelledItemsReport Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetCancelledItemsReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetCancelledItemsReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <From xsi:type="xsd:dateTime">2018-11-20T08:00:00+01:00</From>
            <Till xsi:type="xsd:dateTime">2018-11-21T08:00:00+01:00</Till>
         </Request>
      </urn:GetCancelledItemsReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
From | Timestamp | Mandatory | Report start date/time
Till | Timestamp | Mandatory | Report end date/time
