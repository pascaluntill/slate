# Payment Functions

## PrintProforma

Allows to print proforma and optionally return proforma text.

### PrintProforma Request

> PrintProforma Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:PrintProforma soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TPrintProformaRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <TableNumber xsi:type="xsd:int">1</TableNumber>
            <TablePart xsi:type="xsd:string">a</TablePart>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:PrintProforma>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
TableNumber | Integer | Mandatory | Table number to print the Proforma for
TablePart | String | Mandatory | Table part to print the Proforma for
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`get_receipt` | - | If added, then unTill does not print the Proforma but returns it in PrintProformaResponse.Extra instead, under the key “receipt_text” 
`layout_id` | String | Specify a custom layout for printing the Proforma. Value is the Id of an unTill ticket

### PrintProforma Response

> PrintProforma Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:PrintProformaResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TPrintProformaResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
                <item xsi:type="NS3:TExtraInfo">
                    <Key xsi:type="xsd:string">receipt_text</Key>
                    <Value xsi:type="xsd:string">*** RECEIPT_TEXT ***</Value>
                    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
                </item>
            </Extra>
         </return>
      </NS1:PrintProformaResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`receipt_text` | String | Text of Proforma, if requested with get_receipt

## CloseOrder

CLose the order and pay with the specified payment type.

### CloseOrder Request

> CloseOrder Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:CloseOrder soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TCloseOrderRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <TableNumber xsi:type="xsd:int">1</TableNumber>
            <TablePart xsi:type="xsd:string">a</TablePart>
            <PaymentId xsi:type="xsd:long">5000000055</PaymentId>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:CloseOrder>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
TableNumber | Integer | Mandatory | Table number to close
TablePart | String | Mandatory | Table part to close ("a" - "f")
PaymentId | Long | Mandatory | Id of the Payment mode to use
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

### CloseOrder Response

> CloseOrder Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:CloseOrderResponse xmlns:NS2="urn:TPAPIPosIntfU">
         <return xsi:type="NS2:TCloseOrderResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
         </return>
      </NS1:CloseOrderResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)

## Pay

Make payment on table with specified payment type.

### Pay Request

> Pay Request

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
PaymentId | Long | Mandatory | Id of the Payment mode to use
Amount | Decmial | Mandatory | Specify the amount to pay or use "0" to pay the complete amount
EFTData | String | Optional | When specified and not empty, means that EFT payment processed externally and shouldn’t be handled by unTill. Key=Value pairs separated by LF charachter: Syntax: “key1=value1\nkey2=value2...”
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`external_id` | String | Unique Id (up to 50 characters) which may be assigned to the bill made by “CloseOrder”
`get_bill` | - | If added, then unTill does not print the bill but returns it in PayResponse.Extra instead, under the key “bill_text”
`bill_layout` | String | Use custom ticket layout. Value is the Id of an unTill ticket
`tip` | String | Add tips (amount to be specified in cents)
`proforma_signature` | String | Specify the signature of a proforma to be paid

### Pay Response

> Pay Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:PayResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TPayResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
                <item xsi:type="NS3:TExtraInfo">
                    <Key xsi:type="xsd:string">bill_text</Key>
                    <Value xsi:type="xsd:string">*** BILL_TEXT ***</Value>
                    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
                </item>
            </Extra>
         </return>
      </NS1:PayResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`bill_text` | String | Receipt in the form of plain text returned in this ExtraInfo if `get_bill` has been added in PayRequest.Extra
