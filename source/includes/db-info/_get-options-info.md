# GetOptionsInfo

Returns a list of the active Options in the unTill database.

## The OptionInfo Object

> OptionInfo Object:

```xml
<item xsi:type="NS3:TOptionInfo">
    <OptionId xsi:type="xsd:long">5000000157</OptionId>
    <OptionName xsi:type="xsd:string">Supplement Cold Drinks</OptionName>
    <Available xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="xsd:long[3]">
        <item>5000000208</item>
        <item>5000000209</item>
        <item>5000000210</item>
    </Available>
    <Items xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TItemPrice[4]">
        <item xsi:type="NS3:TItemPrice">
            <ArticleId xsi:type="xsd:long">5000001996</ArticleId>
            <PriceId xsi:type="xsd:long">5000000206</PriceId>
            <Amount xsi:type="xsd:double">0.5</Amount>
            <Vat xsi:type="xsd:double">21</Vat>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TItemPrice">
            <ArticleId xsi:type="xsd:long">5000001996</ArticleId>
            <PriceId xsi:type="xsd:long">5000000207</PriceId>
            <Amount xsi:type="xsd:double">0.5</Amount>
            <Vat xsi:type="xsd:double">21</Vat>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TItemPrice">
            <ArticleId xsi:type="xsd:long">5000002025</ArticleId>
            <PriceId xsi:type="xsd:long">5000000206</PriceId>
            <Amount xsi:type="xsd:double">0.5</Amount>
            <Vat xsi:type="xsd:double">21</Vat>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TItemPrice">
            <ArticleId xsi:type="xsd:long">5000002025</ArticleId>
            <PriceId xsi:type="xsd:long">5000000207</PriceId>
            <Amount xsi:type="xsd:double">0.5</Amount>
            <Vat xsi:type="xsd:double">21</Vat>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
    </Items>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
OptionId | Long | Internal Id of this Option
OptionName | String | Name of this Option
Available | [Long] | List of Sales Areas where this Option is available
Items | [ItemPrice] | List of Option items with their prices
Extra | [ExtraInfo] | List of extra fields

## The GetOptionInfo Request

> GetOptionsInfo Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetOptionsInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetOptionsInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <OptionId xsi:type="xsd:long">0</OptionId>
            <SalesAreaId xsi:type="xsd:long">0</SalesAreaId>
         </Request>
      </urn:GetOptionsInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
---------- | ------- | ------- | -------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
OptionId | Long | Optional | Specify to request information for a certain Option only
SalesAreaId | Long | Optional | Specify to request Options of a certain Sales Area only
