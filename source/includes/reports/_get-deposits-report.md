# GetDepositsReport

Returns the list of deposits per time period.

## The DepositItem Object

> DepositItem Object:

```xml
<item xsi:type="NS3:TDepositItem">
    <Id xsi:type="xsd:long">20000156484</Id>
    <SalesAreaId xsi:type="xsd:long">5000000208</SalesAreaId>
    <ClientId xsi:type="xsd:long">5000096068</ClientId>
    <Amount xsi:type="xsd:double">10</Amount>
    <Comments xsi:type="xsd:string"/>
    <PaymentId xsi:type="xsd:long">5000000055</PaymentId>
    <ComputerName xsi:type="xsd:string">TESTPC</ComputerName>
    <UserId xsi:type="xsd:long">5000001380</UserId>
    <DateTime xsi:type="xsd:dateTime">2018-11-20T14:33:47.000+01:00</DateTime>
    <DepositNumber xsi:type="xsd:string">13</DepositNumber>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Id of the Deposit
SalesAreaId | Long | Sales Area Id
Amount | Decimal | Deposit amount
Comments | String | Deposit comments
PaymentId | Long | Payment Id
ComputerName | String | Computer name
UserId | Long | Waiter Id
DateTime | Timestamp | Deposit date/time
DepositNumber | String | Deposit number
Extra | [ExtraInfo] | List of extra fields

## The GetDepositsReport Request

> GetDepositsReport Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetDepositsReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetDepositsReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <From xsi:type="xsd:dateTime">2018-11-20T08:00:00+01:00</From>
            <Till xsi:type="xsd:dateTime">2018-11-21T08:00:00+01:00</Till>
            <SalesAreaId xsi:type="xsd:long">0</SalesAreaId>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetDepositsReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
From | Timestamp | Mandatory | Report start date/time
Till | Timestamp | Mandatory | Report end date/time
SalesAreaId | Long | Optional | Specify to request report for a certain Sales Area only
