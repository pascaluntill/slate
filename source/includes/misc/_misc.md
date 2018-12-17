# Miscellaneous Functions

## GetVersion

Read current TPAPI protocol version.

### GetVersion Request

> GetVersion Request

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

### GetVersion Response

> GetVersion Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetVersionResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetVersionResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Major xsi:type="xsd:int">2</Major>
            <Minor xsi:type="xsd:int">23</Minor>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
               <item xsi:type="NS3:TExtraInfo">
                  <Key xsi:type="xsd:string">untill_version</Key>
                  <Value xsi:type="xsd:string">128.6.R.28274</Value>
                  <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
               </item>
            </Extra>
         </return>
      </NS1:GetVersionResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Major | Integer | Version Major number
Minor | Integer | Version Minor number
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Description
--- | -----------
`untill_version` | unTill application version

## GetBOStatus

Returns the status including BO database signature. Everytime any backoffice data is updated, this signature changes.

### GetBOStatus Request

> GetBOStatus Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetBOStatus soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetBOStatusRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetBOStatus>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user



### GetBOStatus Response

> GetBOStatus Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetBOStatusResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetBOStatusResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <CurrentSignature xsi:type="xsd:string">669bff6702861fa34909f6fd79ce74bed18c2006</CurrentSignature>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetBOStatusResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
CurrentSignature | String | Current BO database signature

## GetServerInfo

Returns general TPAPI server information.

### GetServerInfo Request

> GetServerInfo Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetServerInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetServerInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetServerInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user

### GetServerInfo Response

> GetServerInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetServerInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetServerInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <DateTime xsi:type="xsd:dateTime">2018-11-20T09:54:40.796+01:00</DateTime>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetServerInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
DateTime | Timestamp | Current server date/time

## PosRestart

Restarts POS.

### PosRestart Request

> PosRestart Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:PosRestart soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TPosRestartRequest" xmlns:urn="urn:TPAPIPosTypesU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:PosRestart>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user

### PosRestart Response

> PosRestart Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:PosRestartResponse xmlns:NS2="urn:TPAPIPosIntfU">
         <return xsi:type="NS2:TPosRestartResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
         </return>
      </NS1:PosRestartResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
