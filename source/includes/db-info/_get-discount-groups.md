# GetDiscountGroups

Returns list of discount groups with details.

## The DiscountGroupInfo Object

> DiscountGroupInfo Object:

```xml
<item xsi:type="NS3:TDiscountGroupInfo">
    <Id xsi:type="xsd:long">65000577970</Id>
    <Name xsi:type="xsd:string">Test Group</Name>
    <Barcode xsi:type="xsd:string">978020137962</Barcode>
    <CheapestArticleDiscountedOnly xsi:type="xsd:boolean">false</CheapestArticleDiscountedOnly>
    <Articles xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TArticleDiscountItemInfo[3]">
        <item xsi:type="NS3:TArticleDiscountItemInfo">
            <ArticleId xsi:type="xsd:long">5000000633</ArticleId>
            <DiscountPercent xsi:type="xsd:double">10</DiscountPercent>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TArticleDiscountItemInfo">
            <ArticleId xsi:type="xsd:long">5000000634</ArticleId>
            <DiscountPercent xsi:type="xsd:double">10</DiscountPercent>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TArticleDiscountItemInfo">
            <ArticleId xsi:type="xsd:long">45000075087</ArticleId>
            <DiscountPercent xsi:type="xsd:double">15</DiscountPercent>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
    </Articles>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Internal Id of this Discount Group
Name | String | Name of this Discount Group
Barcode | String | Barcode of this Discount Group
CheapestArticleDiscountedOnly | Boolean | True if cheapest article is discounted only
Articles | [[ArticleDiscountItemInfo]](#the-articlediscountiteminfo-object) | List of articles
Extra | [ExtraInfo] | List of extra fields

## The ArticleDiscountItemInfo Object

> ArticleDiscountItemInfo Object:

```xml
<item xsi:type="NS3:TArticleDiscountItemInfo">
    <ArticleId xsi:type="xsd:long">5000000633</ArticleId>
    <DiscountPercent xsi:type="xsd:double">10</DiscountPercent>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
ArticleId | Long | Article Id
DiscountPercent | Decimal | Discount in percents
Extra | [ExtraInfo] | List of extra fields

## The GetDepartmentsInfo Request

> GetDepartmentsInfo Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetDiscountGroupsInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetDiscountGroupsInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetDiscountGroupsInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
---------- | ------- | ------- | -------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
