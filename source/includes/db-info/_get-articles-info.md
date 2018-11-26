# GetArticlesInfo

Returns a detailed list of the Articles and their options.

## The ArticleInfo Object

> ArticleInfo Object:

```xml
<item xsi:type="NS3:TArticleInfo">
    <ArticleId xsi:type="xsd:long">5000001716</ArticleId>
    <ArticleName xsi:type="xsd:string">Coca Cola</ArticleName>
    <ArticleNumber xsi:type="xsd:int">1</ArticleNumber>
    <Available xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="xsd:long[3]">
        <item>5000000210</item>
        <item>5000000208</item>
        <item>5000000209</item>
    </Available>
    <DepartmentId xsi:type="xsd:long">5000000170</DepartmentId>
    <Prices xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TItemPrice[2]">
        <item xsi:type="NS3:TItemPrice">
        <ArticleId xsi:type="xsd:long">5000001716</ArticleId>
        <PriceId xsi:type="xsd:long">5000000206</PriceId>
        <Amount xsi:type="xsd:double">2</Amount>
        <Vat xsi:type="xsd:double">21</Vat>
        <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
    </item>
    <item xsi:type="NS3:TItemPrice">
        <ArticleId xsi:type="xsd:long">5000001716</ArticleId>
        <PriceId xsi:type="xsd:long">5000000207</PriceId>
        <Amount xsi:type="xsd:double">1.7</Amount>
        <Vat xsi:type="xsd:double">12</Vat>
        <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
    </item>
    </Prices>
    <FreeOption xsi:type="xsd:long">5000000145</FreeOption>
    <Options xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="xsd:long[1]">
        <item>5000000143</item>
    </Options>
    <IsMenu xsi:type="xsd:boolean">false</IsMenu>
    <IsManualPrice xsi:type="xsd:boolean">false</IsManualPrice>
    <IsActive xsi:type="xsd:boolean">true</IsActive>
    <Promo xsi:type="xsd:boolean">false</Promo>
    <HqId xsi:type="xsd:string">Coca Cola</HqId>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[5]">
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">daily_stock_active</Key>
            <Value xsi:type="xsd:string">0</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">daily_stock_qty</Key>
            <Value xsi:type="xsd:string">0</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">purchase_price</Key>
            <Value xsi:type="xsd:string">0.0000</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
            </item>
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">course_id</Key>
            <Value xsi:type="xsd:string">5000001331</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">info</Key>
            <Value xsi:type="xsd:string"/>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
    </Extra>
</item>
```

Parameter | Type | Description
--------- | ---- | -----------
ArticleId | Long | Internal Id of this Article
ArticleName | String | Name of this Article
ArticleNumber | Integer | Number of this Article
Available | [Long] | List of Sales Area Id's where this Article is available
Prices | [ItemPrice] | List of Prices for this Article
DepartmentId | Long | Id of the Department where this Article belongs to
FreeOption | Long | Free Option ID
Options | [Long] | List of must-have options
IsMenu | Boolean | Returns true if this Article is a menu
IsManualPrice | Boolean | Returns true if this Article requires a manual price input when ordered
IsActive | Boolean | Returns if true is this Article is active
Promo | Boolean | Return true if this Article is a Cobmo/Promo article
HqId | String | HQ Id
Extra | [ExtraInfo] | List of extra fields

## The GetArticlesInfoRequest

> GetArticlesInfoRequest:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetArticlesInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetArticlesInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <ArticleId xsi:type="xsd:long">0</ArticleId>
            <SalesAreaId xsi:type="xsd:long">0</SalesAreaId>
            <GetInactive xsi:type="xsd:boolean">true</GetInactive>
            <Extra xsi:type="urn:TExtraInfoArray" soapenc:arrayType="urn:TExtraInfo[2]">
               <item xsi:type="NS3:TExtraInfo">
                  <Key xsi:type="xsd:string">course_id</Key>
                  <Value xsi:type="xsd:string">0</Value>
               </item>
               <item xsi:type="NS3:TExtraInfo">
                  <Key xsi:type="xsd:string">dailystock</Key>
                  <Value xsi:type="xsd:string">true</Value>
               </item>
            </Extra>
         </Request>
      </urn:GetArticlesInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | -----| -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
SalesAreaId | Long | Optional | Specify to request Articles of a certain Sales Area only
GetInactive | Boolean | Optional | If set to true, also the inactive Articles will be returned
Extra | [ExtraInfo] | Optional | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`course_id` | Long | Only return articles of a specific course
`dailystock` | Boolean | Additionally return data about the daily stock status for all Articles. The data is returned in the ArticleInfo.Extra field
`plu` | List of PLU | Searches Articles by PLU number. The list of PLU can either be a single PLU number or a comma-separated list
