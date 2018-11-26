# Pay

Make payment on table with specified payment type.

## The Pay Response

> Pay Response:

```xml
<return xsi:type="NS2:TPayResponse">
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">bill_text</Key>
            <Value xsi:type="xsd:string">*** BILL_TEXT ***</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
    </Extra>
</return>
```

Parameter | Type | Description
----------| ---- | -----------
Extra | [ExtraInfo] | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`bill_text` | String | Receipt in the form of plain text returned in this ExtraInfo if `get_bill` has been added in PayRequest.Extra

## The Pay Request

> Pay Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:Pay soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TPayRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <TableNumber xsi:type="xsd:int">1</TableNumber>
            <TablePart xsi:type="xsd:string">a</TablePart>
            <PaymentId xsi:type="xsd:long">5000000055</PaymentId>
            <Amount xsi:type="xsd:double">0</Amount>
            <EFTData xsi:type="xsd:string"></EFTData>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:Pay>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
TableNumber | Integer | Mandatory | Table number to make the payment to
TablePart | String | Mandatory | Table part to make the payment to
PaymentId | Long | Mandatory | Id of the [Payment mode](#getpaymentsinfo) mode to use
Amount | Decmial | Mandatory | Specify the amount to pay or use "0" to pay the complete amount
EFTData | String | Optional | When specified and not empty, means that EFT payment processed externally and shouldn’t be handled by unTill. Key=Value pairs separated by LF charachter: Syntax: “key1=value1\nkey2=value2...”
Extra | [ExtraInfo] | Optional | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`external_id` | String | Unique Id (up to 50 characters) which may be assigned to the bill made by “CloseOrder”
`get_bill` | - | If added, then unTill does not print the bill but returns it in PayResponse.Extra instead, under the key “bill_text”
`bill_layout` | String | Use custom ticket layout. Value is the Id of an unTill ticket
`tip` | String | Add tips (amount to be specified in cents)
`proforma_signature` | String | Specify the signature of a proforma to be paid
