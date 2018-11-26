# UpdateCountries

Adds or updates countries in database. When CountryId = 0, country is added otherwise it is updated. It is not allowed to add a country when a country with same name is already exists.

## The Country Object

See [The Country Object](#the-country-object)

## The UpdateCountries Response

> UpdateCountries Response:

```xml
<return xsi:type="NS2:TUpdateCountriesResponse">
    <AddedCountries xsi:type="xsd:int">0</AddedCountries>
    <UpdatedCountries xsi:type="xsd:int">1</UpdatedCountries>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">result_ids</Key>
            <Value xsi:type="xsd:string">65000348984</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
    </Extra>
</return>
```

Parameter | Type | Description
----------| ---- | -----------
AddedCountries | Integer | Number of added Countries
UpdatedCountries | Integer | Number of updated Countries
Extra | [ExtraInfo] | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`result_ids` | String | Comma separated list of Id's of created and/or updated Countries. The number of Id's returned is equal to the number of Countries sent in the request.

## The UpdateCountries Request

> UpdateCountries Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:UpdateCountries soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TUpdateCountriesRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <Countries soapenc:arrayType="urn1:TCountry[1]" xsi:type="urn1:TCountriesArray" xmlns:urn1="urn:TPAPIPosTypesU">
                <item xsi:type="urn:TCountry">
				    <CountryId>65000348984</CountryId>
				    <CountryName>The Netherlands</CountryName>
				    <Kind>0</Kind>
				    <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
                </item>
		    </Countries>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:UpdateCountries>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
Countries | [[Country]](#the-country-object) | Mandatory | List of countries to be added or updated
