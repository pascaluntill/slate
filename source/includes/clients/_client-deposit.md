# ClientAccountDeposit

Makes Deposit to Client Account.

## The ClientAccountDeposit Response

> ClientAccountDeposit Response:

```xml
<return xsi:type="NS2:TClientAccountDepositResponse">
    <OldBalance xsi:type="xsd:double">40.0</OldBalance>
    <NewBalance xsi:type="xsd:double">50.0</NewBalance>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</return>
```

Parameter | Type | Description
----------| ---- | -----------
OldBalance | Decmial | Account balance before deposit
NewBalance | Decimal | Account balance after deposit
Extra | [ExtraInfo] | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`receipt_text` | String | Receipt in the form of a plain text returned in this ExtraInfo if `get_receipt` has been added in ClientAccountDepositRequest.Extra

## The ClientAccountDeposit Request

> ClientAccountDeposit Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:ClientDeposit soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TClientAccountDepositRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <ClientId xsi:type="xsd:long">5000096068</ClientId>
            <PaymentId xsi:type="xsd:long">5000000055</PaymentId>
            <Amount xsi:type="xsd:double">10</Amount>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:ClientDeposit>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
ModifiedSince | Timestamp | Optional | Specify this value to return only clients added/updated since that date/time

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`get_receipt` | - | Instead of printing deposit receipt unTill sends it back in ClientAccountDepositResponse as plain text. The value of ExtraInfo with this key doesn’t matter.
