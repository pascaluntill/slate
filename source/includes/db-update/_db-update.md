# Database Update Functions

## UpdateCountries

Adds or updates countries in database. When CountryId = 0, country is added otherwise it is updated. It is not allowed to add a country when a country with same name is already exists.

### UpdateCountries Request

> UpdateCountries Request

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
				    <CountryId xsi:type="xsd:long">65000348984</CountryId>
                    <CountryName xsi:type="xsd:string">The Netherlands</CountryName>
				    <Kind xsi:type="xsd:int">0</Kind>
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
Countries | [[Country]](#country) | Mandatory | List of countries to be added or updated

### UpdateCountries Response

> UpdateCountries Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:UpdateCountriesResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
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
      </NS1:UpdateCountriesResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| ---- | -----------
AddedCountries | Integer | Number of added Countries
UpdatedCountries | Integer | Number of updated Countries
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Description
--- | -----------
`result_ids` | Comma separated list of Id's of created and/or updated Countries. The number of Id's returned is equal to the number of Countries sent in the request.

## UpdateSalesAreaPrice

Updates the current price level for a Sales Area.

### UpdateSalesAreaPrice Request

> UpdateSalesAreaPrice Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:UpdateSalesAreaPrice soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TUpdateSalesAreaPriceRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <SalesAreaId xsi:type="xsd:long">5000000208</SalesAreaId>
            <PriceId xsi:type="xsd:long">5000000206</PriceId>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:UpdateSalesAreaPrice>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
SalesAreaId | Long | Mandatory | Id of Sales Area
PriceId | Long | Mandatory | Id of Price Level to set for the Sales Area

### UpdateSalesAreaPrice Response

> UpdateSalesAreaPrice Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:UpdateSalesAreaPriceResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TUpdateSalesAreaPriceResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:UpdateSalesAreaPriceResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## AddPouring

Registers pouring in database so the pouring appears in reports and Beverage Control Statistics.

### AddPouring Request

> AddPouring Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:AddPouring soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TAddPouringRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <Pourings xsi:type="urn:TPouringsArray" soapenc:arrayType="urn:TPouring[]">
                <item xsi:type="urn:TPouring">
                    <PLU xsi:type="xsd:int">1</PLU>
                    <Quantity xsi:type="xsd:int">1</Quantity>
                    <DateTime xsi:type="xsd:dateTime">2018-11-20T15:30:44.000Z</DateTime>
                    <WaiterID xsi:type="xsd:double">999</WaiterID>      
				    <ClientCard xsi:type="xsd:string">80518B22694F04</ClientCard>                   
                </item>
	       </Pourings>
         </Request>
      </urn:AddPouring>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
Pourings | [[Pouring]](#pouring) | Mandatory | List of Pourings to register

### AddPouring Response

> AddPouring Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:AddPouringResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TAddPouringResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:AddPouringResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields
