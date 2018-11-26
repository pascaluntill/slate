# GetCountries

Returns the list of countries, declared in the backoffice.

## The Country Object

> Country Object:

```xml
<item xsi:type="NS3:TCountry">
    <CountryId xsi:type="xsd:long">65000348984</CountryId>
    <CountryName xsi:type="xsd:string">Netherlands</CountryName>
    <Kind xsi:type="xsd:int">0</Kind>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">is_active</Key>
            <Value xsi:type="xsd:string">1</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
    </Extra>
</item>
```

Parameter | Type | Description
----------| -----| -----------
Id | Long | Internal Id of this Country
CountryName | String | Name of this Country
Kind | Integer | 0: Home Country; 1: Member EC; 2: Other
Extra | [ExtraInfo] | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description | Read | Write
--- | ----- | ----------- | ---- | -----
`is_active` | 1/ 0 | Activity flag. | Always | Optional, default = 1.

## The GetCountries Request

> GetCountries Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetCountries soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetCountriesRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetCountries>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
Extra | [ExtraInfo] | Optional | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`id` | Long | Search Country by Id.
`is_active` | 1 / 0 / -1 | 1: Active only, 0: Inactive only, -1: Both active and inactive.
