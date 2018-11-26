# PrintProforma

Make payment on table with specified payment type.

## The PrintProforma Response

> PrintProforma Response:

```xml
<return xsi:type="NS2:TPrintProformaResponse">
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">receipt_text</Key>
            <Value xsi:type="xsd:string">*** RECEIPT_TEXT ***</Value>
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
`bill_text` | String | Receipt in the form of plain text returned in this ExtraInfo if “get_bill” has been added in PayRequest.Extra

## The PrintProforma Request

> PrintProforma Request:

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
Extra | [ExtraInfo] | Optional | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`get_receipt` | - | If added, then unTill does not print the Proforma but returns it in PrintProformaResponse.Extra instead, under the key “receipt_text” 
`layout_id` | String | Specify a custom layout for printing the Proforma. Value is the Id of an unTill ticket
