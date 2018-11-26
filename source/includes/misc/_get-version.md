# GetVersion

Read current TPAPI protocol version.

## The GetVersion Response

> GetVersion Response:

```xml
<return xsi:type="NS2:TGetVersionResponse">
    <Major xsi:type="xsd:int">2</Major>
    <Minor xsi:type="xsd:int">23</Minor>
        <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
            <item xsi:type="NS3:TExtraInfo">
                <Key xsi:type="xsd:string">untill_version</Key>
                <Value xsi:type="xsd:string">128.1.R.28140</Value>
                <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
            </item>
        </Extra>
</return>
```

Parameter | Type | Description
----------| ---- | -----------
Major | Integer | Version Major number
Minor | Integer | Version Minor number
Extra | [ExtraInfo] | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`untill_version` | String | unTill application version

## The GetVersion Request

> GetVersion Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetVersion soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetVersionRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetVersion>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
