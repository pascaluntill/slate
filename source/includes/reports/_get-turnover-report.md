# GetTurnoverReport

Get the list of Transactions including the ordered items.

## The TurnoverBill Object

> TurnoverBill Object:

```xml
<item xsi:type="NS3:TTurnoverBill">
    <OpenDateTime xsi:type="xsd:dateTime">2018-09-21T08:21:02.000+02:00</OpenDateTime>
    <CloseDateTime xsi:type="xsd:dateTime">2018-09-21T08:21:02.000+02:00</CloseDateTime>
    <ComputerName xsi:type="xsd:string">TPAPIWIN7</ComputerName>
    <BillNumber xsi:type="xsd:int">38795</BillNumber>
    <BillSuffix xsi:type="xsd:string"/>
    <TableNumber xsi:type="xsd:int">103</TableNumber>
    <TablePart xsi:type="xsd:string">a</TablePart>
    <Covers xsi:type="xsd:int">5</Covers>
    <UserId xsi:type="xsd:long">65000358137</UserId>
    <SalesAreaId xsi:type="xsd:long">5000000146</SalesAreaId>
    <Items xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTurnoverBillItem[2]">
        <item xsi:type="NS3:TTurnoverBillItem">
            <ArticleId xsi:type="xsd:long">15000028541</ArticleId>
            <DateTime xsi:type="xsd:dateTime">2018-09-21T08:21:02.000+02:00</DateTime>
            <ItemNumber xsi:type="xsd:int">0</ItemNumber>
            <ComputerName xsi:type="xsd:string">TPAPIWIN7</ComputerName>
            <Quantity xsi:type="xsd:int">3</Quantity>
            <Price xsi:type="xsd:double">15</Price>
            <UserId xsi:type="xsd:long">65000358137</UserId>
            <HqId xsi:type="xsd:string"/>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TTurnoverBillItem">
            <ArticleId xsi:type="xsd:long">5000000905</ArticleId>
            <DateTime xsi:type="xsd:dateTime">2018-09-21T08:21:02.000+02:00</DateTime>
            <ItemNumber xsi:type="xsd:int">0</ItemNumber>
            <ComputerName xsi:type="xsd:string">TPAPIWIN7</ComputerName>
            <Quantity xsi:type="xsd:int">3</Quantity>
            <Price xsi:type="xsd:double">55.5</Price>
            <UserId xsi:type="xsd:long">65000358137</UserId>
            <HqId xsi:type="xsd:string"/>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
    </Items>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
OpenDateTime | Timestamp | Transaction open date/time
CloseDateTime | Timestamp | Transaction close date/time
ComputerName | String | Computer name
BillNumber | Integer | Transaction number
BillSuffix | String | Transaction suffix
TableNumber | Integer | Table number
TablePart | String | Table part
Covers | Integer | Number of covers
UserId | Long | Id of the User
SalesAreaId | Long | Id of the Sales Area
Items | [TurnoverBillItem] | List of included items
Extra | [ExtraInfo] | List of extra fields

## The GetTurnoverReport Request

> GetTurnoverReport Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetTurnoverReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetTurnoverReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <UserId xsi:type="xsd:long">0</UserId>
            <SalesAreaId xsi:type="xsd:long">0</SalesAreaId>
            <From xsi:type="xsd:dateTime">2018-09-21T08:00:00+02:00</From>
            <Till xsi:type="xsd:dateTime">2018-09-22T08:00:00+02:00</Till>
         </Request>
      </urn:GetTurnoverReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
UserId | Long | Optional | Specify to request the report for a certain User only
SalesAreaId | Long | Optional | Specify to request report of a certain Sales Area only
From | Timestamp | Mandatory | Report start date/time
Till | Timestamp | Mandatory | Report end date/time
