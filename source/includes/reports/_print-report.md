# PrintReport

Allows to print a report or return it in response as plain text.

## The PrintReport Response

> PrintReport Response:

```xml
<return xsi:type="NS2:TPrintReportResponse">
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">receipt_text</Key>
            <Value xsi:type="xsd:string">*** REPORT_TEXT ***</Value>
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
`receipt_text` | String | Text of the report in plain text when PrinterId = 0 is specified in request.

## The PrintReport Request

> PrintReport Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:PrintReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TPrintReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <LayoutId xsi:type="xsd:long">5000001172</LayoutId>
            <PrinterId xsi:type="xsd:long">0</PrinterId>
            <From xsi:type="xsd:dateTime">2018-11-20T08:00:00+01:00</From>
            <Till xsi:type="xsd:dateTime">2018-11-21T08:00:00+01:00</Till>
            <Arguments xsi:type="urn1:TKeyValueArray" soapenc:arrayType="urn1:TKeyValue[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:PrintReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
LayoutId | Long | Mandatory | Report layout Id
PrinterId | Long | Mandatory | Id of the printer where to print the report to. If `0` is specified, the result is sent in the response as plain text
From | Timestamp | Optional | Report start date/time
Till | Timestamp | Optional | RReport end date/time
Arguments | [KeyValue] | Optional | Report arguments
Extra | [ExtraInfo] | Optional | List of extra fields
