# GetPaymentsInfo

Returns a list of the active Payments in the unTill database.

## The PaymentInfo Object

> PaymentInfo Object:

```xml
<item xsi:type="NS3:TPaymentInfo">
    <PaymentId xsi:type="xsd:long">5000000055</PaymentId>
    <PaymentNumber xsi:type="xsd:int">1</PaymentNumber>
    <PaymentName xsi:type="xsd:string">Cash</PaymentName>
    <PaymentKind xsi:type="xsd:int">0</PaymentKind>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
PaymentId | Long | Internal Id of this Payment
PaymentNumber | Integer | Number of this Payment
PaymentName | String | Name of this Category
PaymentKind | Integer | Payment kind
Extra | [ExtraInfo] | List of extra fields

## The GetPaymentsInfo Request

> GetPaymentsInfo Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetPaymentsInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetPaymentsInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetPaymentsInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
