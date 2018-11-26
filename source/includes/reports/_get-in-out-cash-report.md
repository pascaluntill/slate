# GetInOutCashReport

Returns the list of “In/Out” cash entries from the database per time period.

## The InOutCashItem Object

> InOutCashItem Object:

```xml
<item xsi:type="NS3:TInOutCashItem">
    <Id xsi:type="xsd:long">20000156558</Id>
    <DateTime xsi:type="xsd:dateTime">2018-11-20T15:47:05.000+01:00</DateTime>
    <ComputerName xsi:type="xsd:string">TESTPC</ComputerName>
    <UserId xsi:type="xsd:long">5000001377</UserId>
    <Amount xsi:type="xsd:double">-50</Amount>
    <Reason xsi:type="xsd:string">Out Cash</Reason>
    <Supplier xsi:type="xsd:string">unTill Software Development Group B.V.</Supplier>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Item Id
DateTime | Timestamp | In/Out Cash date/time
ComputerName | String | Computer name
UserId | Long | Waiter Id
Amount | Decimal | Amount. Positive for "In" cash and negative for "Out" cash items
Reason | String | In/Out Cash reason
Supplier | String | In/Out Cash supplier
Extra | [ExtraInfo] | List of extra fields

## The GetInOutCashReport Request

> GetInOutCashReport Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetInOutCashReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetInOutCashReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <From xsi:type="xsd:dateTime">2018-11-20T08:00:00+01:00</From>
            <Till xsi:type="xsd:dateTime">2018-11-21T08:00:00+01:00</Till>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetInOutCashReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
From | Timestamp | Mandatory | Report start date/time
Till | Timestamp | Mandatory | Report end date/time
