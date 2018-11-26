# GetDetailedTurnoverReport

Returns the detailed list of transactions for the specified period. For each transaction, a list of orders, bills, proformas and re-prints is returnd.

## The TurnoverTransaction Object

> TurnoverTransaction Object:

```xml
<item xsi:type="NS3:TTimeAttendanceRecord">
    <UserId xsi:type="xsd:long">15000001214</UserId>
    <Start xsi:type="xsd:dateTime">2018-07-26T16:05:13.621+02:00</Start>
    <Stop xsi:type="xsd:dateTime">2018-07-26T23:15:21.000+02:00</Stop>
    <TotalTime xsi:type="xsd:string">07:10</TotalTime>
    <TotalDecimal xsi:type="xsd:double">7.1667</TotalDecimal>
    <TotalCosts xsi:type="xsd:double">0</TotalCosts>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
UserId | Long | Id of the User
Start | Timestamp | Record start
Stop | Timestamp | Record end - "1899-12-30" means that the User has not clocked out yet
TotalTime | String | Record duration - Format " HH:MM"
TotalDecimal | Decimal | Record duration, in decimal
TotalCosts | Decimal | Total costs
Extra | [ExtraInfo] | List of extra fields

## The GetDetailedTurnoverReport Request

> GetDetailedTurnoverReport Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetDetailedTurnoverReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetDetailedTurnoverReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <From xsi:type="xsd:dateTime">2018-09-21T08:00:00+02:00</From>
            <Till xsi:type="xsd:dateTime">2018-09-22T08:00:00+02:00</Till>
            <SalesAreaId xsi:type="xsd:long">0</SalesAreaId>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetDetailedTurnoverReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
From | Timestamp | Mandatory | Report start date/time
Till | Timestamp | Mandatory | Report end date/time
SalesAreaId | Long | Optional | Specify to request report of a certain Sales Area only