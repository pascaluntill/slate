# Types and Classes

All strings are unicode UTF8 strings. Other classes are listed below.

## ArticleDiscountItemInfo

> ArticleDiscountItemInfo Object

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
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## ArticleInfo

> ArticleInfo Object

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
Prices | [[ItemPrice]](#itemprice) | List of Prices for this Article
DepartmentId | Long | Id of the Department where this Article belongs to
FreeOption | Long | Free Option ID
Options | [Long] | List of must-have options
IsMenu | Boolean | Returns true if this Article is a menu
IsManualPrice | Boolean | Returns true if this Article requires a manual price input when ordered
IsActive | Boolean | Returns if true is this Article is active
Promo | Boolean | Return true if this Article is a Cobmo/Promo article
HqId | String | HQ Id
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Description
--- | -----------
`course_id` | Only return articles of a specific course
`daily_stock_active` | 1/0 (if DailyStock=1 was specified in request’s Extra fields)
`daily_stock_qty` | Daily stock quantity (if DailyStock=1 was specified in request’s Extra fields)
`info` | Article info (tab 9 of the article settings in back-office)
`plu` | When PLU is not zero
`purchase_price` | Purchase price

## ArticleShort

> ArticleShort Object

```xml
<item xsi:type="NS3:TArticleShort">
    <ArticleId xsi:type="xsd:long">5000001716</ArticleId>
    <ArticleName xsi:type="xsd:string">Coca Cola</ArticleName>
    <ArticleNumber xsi:type="xsd:int">1</ArticleNumber>
    <SalesAreaId xsi:type="xsd:long">5000000210</SalesAreaId>
    <DepartmentId xsi:type="xsd:long">5000000170</DepartmentId>
    <HqId xsi:type="xsd:string">Coca Cola</HqId>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| -----| -----------
ArticleId | Long | Internal Id of this Article
ArticleName | String | Name of this Article
ArticleNumber | Integer | Number of this Article
SalesAreaId | Long | Id of the Sales Area where this Article is available
DepartmentId | Long | Id of the Department where this Article belongs to
HqId | String | HQ Id
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## CancelledItem

> CancelledItem Object

```xml
<item xsi:type="NS3:TCancelledItem">
    <ArticleId xsi:type="xsd:long">5000001722</ArticleId>
    <DateTime xsi:type="xsd:dateTime">2018-11-20T16:30:42.000+01:00</DateTime>
    <UserId xsi:type="xsd:long">5000001377</UserId>
    <TableNo xsi:type="xsd:int">21</TableNo>
    <TablePart xsi:type="xsd:string">a</TablePart>
    <Quantity xsi:type="xsd:int">1</Quantity>
    <Price xsi:type="xsd:double">2</Price>
    <PriceId xsi:type="xsd:long">5000000206</PriceId>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
ArticleId | Long | Article Id
DateTime | Timestamp | Date/time of cancelling the article
UserId | Long | Waiter Id
TableNo | Integer | Table number where the article was cancelled
TablePart | String | Table part where the article was cancelled
Quantity | Integer | Quantity of cancelled articles
Price | Decimal | Price
PriceId | Long | Id of the Price level
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## CategoryInfo

> CategoryInfo Object

```xml
<item xsi:type="NS3:TCategoryInfo">
    <CategoryId xsi:type="xsd:long">5000000036</CategoryId>
    <CategoryName xsi:type="xsd:string">1.Bar</CategoryName>
    <HqId xsi:type="xsd:string">1.Bar</HqId>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
CategoryId | Long | Internal Id of this Category
CategoryName | String | Name of this Category
HqId | String | Hq Id
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## Client

> Client Object

```xml
<item xsi:type="NS3:TClient">
    <Id xsi:type="xsd:long">65000353067</Id>
    <Number xsi:type="xsd:int">1</Number>
    <Name xsi:type="xsd:string">John Doe</Name>
    <Country xsi:type="xsd:string">United States</Country>
    <Phone xsi:type="xsd:string">585-924-1525</Phone>
    <Fax xsi:type="xsd:string"/>
    <Email xsi:type="xsd:string">brabtleater1957@rhyta.com</Email>
    <Website xsi:type="xsd:string"/>
    <Address xsi:type="xsd:string">1951 Cherry Ridge Drive</Address>
    <Info xsi:type="xsd:string"/>
    <BirthDate xsi:type="xsd:dateTime">1995-03-07T00:00:00.000+01:00</BirthDate>
    <CardNumber xsi:type="xsd:string">MjY3MDIwNjQ2OTU0RA==</CardNumber>
    <Code xsi:type="xsd:string"/>
    <OnInvoice xsi:type="xsd:boolean">true</OnInvoice>
    <PriceActive xsi:type="xsd:boolean">true</PriceActive>
    <Price xsi:type="xsd:long">65000333282</Price>
    <PromotionPrice xsi:type="xsd:long">0</PromotionPrice>
    <AccountBalance xsi:type="xsd:double">0</AccountBalance>
    <AccountLimit xsi:type="xsd:double">0</AccountLimit>
    <IsSharedAccount xsi:type="xsd:boolean">false</IsSharedAccount>
    <SharedAccount xsi:type="xsd:string"/>
    <SavePoints xsi:type="xsd:int">1636</SavePoints>
    <SaveAmount xsi:type="xsd:int">0</SaveAmount>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[4]">
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">last_update</Key>
            <Value xsi:type="xsd:string">2018.11.20 10:36:14</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">is_active</Key>
            <Value xsi:type="xsd:string">1</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">country_id</Key>
            <Value xsi:type="xsd:string">65000353071</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">smartcard_uid</Key>
            <Value xsi:type="xsd:string">48C44B8C</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
    </Extra>
</item>
```

Parameter | Type | Description
----------| -----| -----------
Id | Long | Internal Id of this Client
Number | Integer | Number of this Article
Name | String | Name of this Article
Country | String | Country name (Id of country is sent in Extras)
Phone | String | Client phone
Fax | String | Client fax
Email | String | Client email
Website | String | Client website
Address | String | Client address
Info | String | Client info
BirthDate | Timestamp | Client birthdate
CardNumber | String | Client cardnumber (Base64-encoded)
Code | String | Client code
OnInvoice | Boolean | True if Client is allowed to consume on invoice
PriceActive | Boolean | True if Client has a special price level assigned
PromotionPrice | Long | Returns the special price level Id assigned to this Client
AccountBalance | Decimal | Current Client balance
AccountLimit | Decimal | Client limit
IsSharedAccount | Boolean | True if this Client belongs to a Shared Account
SharedAccount | String | Shared Account name
SavePoints | Integer | Current savepoints balance
SaveAmount | String | Current saveamount balance
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Value | Description | Read | Write
--- | ----- | ----------- | ---- | -----
`is_active` | 1/ 0 | Activity flag. | Always | Optional, default = 1.
`country_id` | Long | Id of Country. | Always | Optional
`last_update` | Timestamp | When client was updated for the last time. | Always | -
`smartcard_uid` | String (Hex) | Smartcard UID. | If not null | Optional

## Country

> Country Object

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
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Value | Description | Read | Write
--- | ----- | ----------- | ---- | -----
`is_active` | 1/0 | Activity flag | Always | Optional, default = 1.

## Course 

> Course Object

```xml
<item xsi:type="NS3:TCourse">
    <Id xsi:type="xsd:long">5000000468</Id>
    <Name xsi:type="xsd:string">Mains</Name>
    <Number xsi:type="xsd:int">3</Number>
    <Separate xsi:type="xsd:boolean">true</Separate>
    <Changeable xsi:type="xsd:boolean">true</Changeable>
    <AutoFire xsi:type="xsd:boolean">false</AutoFire>
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
----------| ---- | -----------
Id | Long | Internal Id of this Course
Name | String | Name of this Course
Number | Integer | Number of this Course
Separate | Boolean | True if this Course is separate
Changeable | Boolean | True if this Course is changeable
AutoFire | Boolean | True is this Course is fired automatically
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Value | Description | Read | Write
--- | ----- | ----------- | ---- | -----
`is_active` | 1/0 | Activity flag | Always | N/A

## Credential

> ExtraInfo Object

```xml
<item xsi:type="NS3:TCredential">
    <CredentialGuid xsi:type="xsd:string">{56DAFD3A-B188-43A5-B337-EFE84DB88C33}</CredentialGuid>
    <CredentialName xsi:type="xsd:string">Administrator</CredentialName>
</item>
```

Parameter | Type | Description
----------| -----| -----------
CredentialGuid | String | Credential GUID
CredentialName | String | Credential Name

## DepartmentInfo

> DepartmentInfo Object

```xml
<item xsi:type="NS3:TDepartmentInfo">
    <DepartmentId xsi:type="xsd:long">5000000170</DepartmentId>
    <DepartmentNumber xsi:type="xsd:int">9002</DepartmentNumber>
    <DepartmentName xsi:type="xsd:string">Cold Drinks</DepartmentName>
    <Available xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="xsd:long[3]">
        <item>5000000208</item>
        <item>5000000209</item>
        <item>5000000210</item>
    </Available>
    <Supplement xsi:type="xsd:long">5000000157</Supplement>
    <Condiment xsi:type="xsd:long">5000000156</Condiment>
    <GroupId xsi:type="xsd:long">5000000043</GroupId>
    <SpecialArticles xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="xsd:long[0]"/>
    <HqId xsi:type="xsd:string">Cold Drinks</HqId>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
DepartmentId | Long | Internal Id of this Department
DepartmentName | String | Name of this Department
DepartmentNumber | Integer | Number of this Department
Available | [Long] | List of Sales Areas where this Department is available
Supplement | Long | Supplement Option Id
Condiment | Long | Condiment Option Id
GroupId | Long | Group Id
SpecialArticles | [Long] | List of extra Articles added to this Department
HqId | String | Hq Id
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## DepositItem

> DepositItem Object

```xml
<item xsi:type="NS3:TDepositItem">
    <Id xsi:type="xsd:long">20000156484</Id>
    <SalesAreaId xsi:type="xsd:long">5000000208</SalesAreaId>
    <ClientId xsi:type="xsd:long">5000096068</ClientId>
    <Amount xsi:type="xsd:double">10</Amount>
    <Comments xsi:type="xsd:string"/>
    <PaymentId xsi:type="xsd:long">5000000055</PaymentId>
    <ComputerName xsi:type="xsd:string">TESTPC</ComputerName>
    <UserId xsi:type="xsd:long">5000001380</UserId>
    <DateTime xsi:type="xsd:dateTime">2018-11-20T14:33:47.000+01:00</DateTime>
    <DepositNumber xsi:type="xsd:string">13</DepositNumber>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Id of the Deposit
SalesAreaId | Long | Sales Area Id
Amount | Decimal | Deposit amount
Comments | String | Deposit comments
PaymentId | Long | Payment Id
ComputerName | String | Computer name
UserId | Long | Waiter Id
DateTime | Timestamp | Deposit date/time
DepositNumber | String | Deposit number
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## DiscountGroupInfo

> DiscountGroupInfo Object

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
Articles | [[ArticleDiscountItemInfo]](#articlediscountiteminfo) | List of articles
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## ExtraInfo

> ExtraInfo Object

```xml
<Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
  <item xsi:type="NS3:TExtraInfo">
     <Key xsi:type="xsd:string">key</Key>
     <Value xsi:type="xsd:string">value</Value>
     <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
  </item>
</Extra>
```

Parameter | Type | Description
----------| -----| -----------
Key | String | Extra Info Item Key
Value | String | Extra Info Item Value
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GroupInfo

> GroupInfo Object

```xml
<item xsi:type="NS3:TGroupInfo">
    <GroupId xsi:type="xsd:long">5000000043</GroupId>
    <GroupName xsi:type="xsd:string">1.Without Alcohol</GroupName>
    <CategoryId xsi:type="xsd:long">5000000036</CategoryId>
    <HqId xsi:type="xsd:string">1.Without Alcohol</HqId>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[2]">
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">bookkeeping_turnover</Key>
            <Value xsi:type="xsd:string">81030</Value>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
        <item xsi:type="NS3:TExtraInfo">
            <Key xsi:type="xsd:string">bookkeeping_vat</Key>
            <Value xsi:type="xsd:string"/>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
        </item>
    </Extra>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
GroupId | Long | Internal Id of this Group
GroupName | String | Name of this Group
CategoryId | Long | Category Id
HqId | String | Hq Id
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Description 
--- | ----------- 
`bookkeeping_turnover` | Bookkeeping turnover number
`bookkeeping_vat` | Bookkeeping VAT number

## HourlyWageItem

> HourlyWageItem Object

```xml
<item xsi:type="NS3:THourlyWageItem">
    <Position xsi:type="xsd:string">Manager</Position>
    <HourlyWage xsi:type="xsd:double">15</HourlyWage>
    <HourlyWageOvertime xsi:type="xsd:double">22.5</HourlyWageOvertime>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Position | String | Waiter Position
HourlyWage | Decimal | Hourly wage
HourlyWageOvertime | Decimal | Overtime hourly wage 

## InOutCashItem

> InOutCashItem Object

```xml
<item xsi:type="NS3:TInOutCashItem">
    <Id xsi:type="xsd:long">20000156558</Id>
    <DateTime xsi:type="xsd:dateTime">2018-11-20T15:47:05.000+01:00</DateTime>
    <ComputerName xsi:type="xsd:string">TESTPC</ComputerName>
    <UserId xsi:type="xsd:long">5000001377</UserId>
    <Amount xsi:type="xsd:double">-50</Amount>
    <Reason xsi:type="xsd:string">Out Cash</Reason>
    <Supplier xsi:type="xsd:string">unTill Software Development Group B.V.</Supplier>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Item Id
DateTime | Timestamp | In/Out Cash date/time
ComputerName | String | Computer name
UserId | Long | Waiter Id
Amount | Decimal | Amount. Positive for "In" cash and negative for "Out" cash items
Reason | String | In/Out Cash reason
Supplier | String | In/Out Cash supplier
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## ItemPrice

> ItemPrice Object

```xml
<item xsi:type="NS3:TItemPrice">
    <ArticleId xsi:type="xsd:long">5000001716</ArticleId>
    <PriceId xsi:type="xsd:long">5000000206</PriceId>
    <Amount xsi:type="xsd:double">2</Amount>
    <Vat xsi:type="xsd:double">21</Vat>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>

```

Parameter | Type | Description
----------| -----| -----------
ArticleId | Long | Internal Id of this Article
PriceId | Long | Internal Id of the price level
Amount | Decimal | Price amount
VAT | Decimal | VAT percent
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## KeyValue

> KeyValue Object

```xml
<item xsi:type="NS3:TKeyValue">
    <Key xsi:type="xsd:string">key</Key>
    <Value xsi:type="xsd:string">value</Value>
</item>
```

Parameter | Type | Description
----------| -----| -----------
Key | String | Item Key
Value | String | Item Value

## OptionInfo

> OptionInfo Object

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
Items | [[ItemPrice]](#itemprice) | List of Option items with their prices
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## OrderInfo

> OrderInfo Object

```xml
<item xsi:type="NS3:TOrderInfo">
    <TableNumber xsi:type="xsd:int">1</TableNumber>
    <TablePart xsi:type="xsd:string">a</TablePart>
    <OrderName xsi:type="xsd:string">Test</OrderName>
    <CientName xsi:type="xsd:string">John Doe</CientName>
    <OrderDescr xsi:type="xsd:string"/>
    <SalesAreaId xsi:type="xsd:long">5000000208</SalesAreaId>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
TableNumber | Integer | Table number
TablePart | String | Table part
OrderName | String | Order Name
ClientName | String | Name of the client assigned to the Order
OrderDescr | String | Order description
SalesAreaId | Long | Id of the Sales Area
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## OrderItem

> OrderItem Object

```xml
<item xsi:type="urn:TOrderItem">
    <ItemNumber xsi:type="xsd:int">1</ItemNumber>
    <ArticleId xsi:type="xsd:long">5000001716</ArticleId>
    <OrderItemType xsi:type="xsd:int">0</OrderItemType>
	<Text xsi:type="xsd:string"></Text>
	<ManualPrice xsi:type="xsd:double">0</ManualPrice>
	<Quantity xsi:type="xsd:int">1</Quantity>
    <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
</item>
```

Parameter | Type | Status | Description
----------| ---- | ------ | -----------
ItemNumber | Integer | Mandatory | Sequential order item number
ArticleId | Long | Mandatory | Id of Article to order. Specify '0' when OrderItemType = 6
OrderItemType | Integer | Mandatory | Type of order item
Text | String | Optional | Text when OrderItemType = 6
ManualPrice | Decimal | Optional | Only required when the Article has ManualPrice = true
Quantity | Integer | Mandatory | Quantity of ordered items. Note: Only valid when OrderItemType = 0 or 5
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`last` | - | Add this extra when this item is the last of a must-have option that has "Compose" enabled, and the next item is also a must-have option

## PaymentInfo

> PaymentInfo Object

```xml
<item xsi:type="NS3:TPaymentInfo">
    <PaymentId xsi:type="xsd:long">5000000055</PaymentId>
    <PaymentNumber xsi:type="xsd:int">1</PaymentNumber>
    <PaymentName xsi:type="xsd:string">Cash</PaymentName>
    <PaymentKind xsi:type="xsd:int">0</PaymentKind>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
PaymentId | Long | Internal Id of this Payment
PaymentNumber | Integer | Number of this Payment
PaymentName | String | Name of this Category
PaymentKind | Integer | Payment kind
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## Pouring

> Pouring Object

```xml
<item xsi:type="urn:TPouring">
    <PLU xsi:type="xsd:int">1</PLU>
    <Quantity xsi:type="xsd:int">1</Quantity>
    <TableNumber xsi:type="xsd:int">2</TableNumber>
    <DateTime xsi:type="xsd:dateTime">2018-11-20T15:30:44.000Z</DateTime>
    <WaiterID xsi:type="xsd:double">999</WaiterID>      
    <ClientCard xsi:type="xsd:string">80518B22694F04</ClientCard>                   
</item>
```

Parameter | Type | Status | Description
----------| ---- | ------ | -----------
PLU | Integer | Mandatory | PLU of the Article
Quantity | Integer | Mandatory | Quantity
TableNumber | Integer | Optional | Table number for which the pouring has been made
DateTime | Timestamp | Mandatory | Date/time of pouring
WaiterID | Integer | Optional | Waiter number (Users / Beverage Control / Waiter ID)
ExteranalID | Long | Optional | Id of pouring in 3rd party system
ExternalUID | String (max. 50) | Optional | A unique UID of pouring in 3rd party system. When not empty, unTill only inserts pouring if no pouring with the same External UID already exists in database
ClientCard | String | Optional | Client Card
LCU | Integer | Optional | Logical Control Unit number which identifies the device

## PriceInfo

> PriceInfo Object

```xml
<item xsi:type="NS3:TPriceInfo">
    <PriceId xsi:type="xsd:long">5000000206</PriceId>
    <PriceName xsi:type="xsd:string">Normal</PriceName>
    <HqId xsi:type="xsd:string"/>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
PriceId | Long | Internal Id of this Price
PriceName | String | Name of this Price
HqId | String | Hq Id
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## SalesAreaInfo

> SalesAreaInfo Object

```xml
<item xsi:type="NS3:TSalesAreaInfo">
    <SalesAreaId xsi:type="xsd:long">5000000208</SalesAreaId>
    <SalesAreaNumber xsi:type="xsd:int">1</SalesAreaNumber>
    <SalesAreaName xsi:type="xsd:string">Restaurant</SalesAreaName>
    <PriceId xsi:type="xsd:long">5000000206</PriceId>
    <Tables xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTableRange[x]">...</Tables>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
SalesArea | Long | Internal Id of this Sales Area
SalesAreaNumber | Integer | Number of this Sales Area
SalesAreaName | String | Name of this Sales Area
PriceId | Long | Id of the active Price Level for this Sales Area
Tables | [[TableRange]](#tablerange) | List of Table Ranges for this Sales Area 
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## Supplier

> Supplier Object

```xml
<item xsi:type="NS3:TSupplierInfo">
    <Id xsi:type="xsd:long">5000000074</Id>
    <Name xsi:type="xsd:string">unTill Software Development Group B.V.</Name>
    <Number xsi:type="xsd:int">1</Number>
    <Address xsi:type="xsd:string">Choorhoekseweg 8 4424NW Wemeldinge</Address>
    <AccountNumber xsi:type="xsd:string"/>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Supplier Id
Name | String | Supplier name
Number | Integer | Supplier number
Address | String | Supplier address
AccountNumber | String | Supplier account number
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## TableRange

> TableRange Object

```xml
<item xsi:type="NS3:TTableRange">
    <FromTable xsi:type="xsd:int">1</FromTable>
    <ToTable xsi:type="xsd:int">12</ToTable>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
FromTable | Integer | Internal Table range start
ToTable | Integer | Table range end
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## TimeAttendanceRecord

> TimeAttendanceRecord Object

```xml
<item xsi:type="NS3:TTimeAttendanceRecord">
    <UserId xsi:type="xsd:long">15000001214</UserId>
    <Start xsi:type="xsd:dateTime">2018-07-26T16:05:13.621+02:00</Start>
    <Stop xsi:type="xsd:dateTime">2018-07-26T23:15:21.000+02:00</Stop>
    <TotalTime xsi:type="xsd:string">07:10</TotalTime>
    <TotalDecimal xsi:type="xsd:double">7.1667</TotalDecimal>
    <TotalCosts xsi:type="xsd:double">0</TotalCosts>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
UserId | Long | Id of the User
Start | Timestamp | Record start
Stop | Timestamp | Record end ("1899-12-30" means that the User has not clocked out yet)
TotalTime | String | Record duration - Format " HH:MM"
TotalDecimal | Decimal | Record duration, in decimal
TotalCosts | Decimal | Total costs
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## TransactionBill

> TransactionBill Object

```xml
<item xsi:type="NS3:TTransactionBill">
    <Id xsi:type="xsd:long">25000158240</Id>
    <DateTime xsi:type="xsd:dateTime">2018-12-12T11:41:54.000+01:00</DateTime>
    <RealDateTime xsi:type="xsd:dateTime">2018-12-12T11:41:54.000+01:00</RealDateTime>
    <ComputerName xsi:type="xsd:string">TESTPC</ComputerName>
    <BillNumber xsi:type="xsd:string">1106</BillNumber>
    <UserId xsi:type="xsd:long">5000001377</UserId>
    <ClientName xsi:type="xsd:string"/>
    <SalesAreaId xsi:type="xsd:long">5000000208</SalesAreaId>
    <Tip xsi:type="xsd:double">0</Tip>
    <Payments xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTransactionBillPayment[x">...</Payments>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
    <ClientId xsi:type="xsd:long">0</ClientId>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Internal Bill Id
DateTime | Timestamp | Bill date/tme (first date.time of payment)
RealDateTime | Timestamp | Real date/time of payment
ComputerName | String | Computer name
BillNumber | String | Bill number
UserId | Long | Waiter Id
ClientName | String | Name of client assigned to this bill
ClientId | Long | Id of client assigned to this bill
SalesAreaId | Long | Id of Sales Area
Tip | Double | Tip amount
Payments | [[TransactionBillPayment]](#transactionbillpayment) | List of payments used in this bill
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## TransactionBillPayment

> TransactionBillPayment Object

```xml
<item xsi:type="NS3:TTransactionBillPayment">
   <Id xsi:type="xsd:long">25000158242</Id>
   <PaymentId xsi:type="xsd:long">5000000055</PaymentId>
   <Amount xsi:type="xsd:double">2</Amount>
   <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Internal Bill payment Id
PaymentId | Long | Id of Payment mode
Amount | Decimal | Payment amount
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## TransactionBillReprint

> TransactionBillReprint Object

```xml
<item xsi:type="NS3:TTransactionBillReprint">
    <Id xsi:type="xsd:long">25000158293</Id>
    <DateTime xsi:type="xsd:dateTime">2018-12-13T11:29:34.000+01:00</DateTime>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Internal Bill reprint Id
DateTime | Timestamp | Date/time of reprint
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## TransactionOrder

> TransactionOrder Object

```xml
<item xsi:type="NS3:TTransactionOrder">
    <Id xsi:type="xsd:long">25000158203</Id>
    <DateTime xsi:type="xsd:dateTime">2018-12-12T11:41:43.000+01:00</DateTime>
    <ComputerName xsi:type="xsd:string">TESTPC</ComputerName>
    <OrderNumber xsi:type="xsd:string">1215</OrderNumber>
    <UserId xsi:type="xsd:long">5000001377</UserId>
    <SalesAreaId xsi:type="xsd:long">5000000208</SalesAreaId>
    <Items xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTransactionOrderItem[x]">...</Items>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Internal Order Id
DateTime | Timestamp | Date/time of order
ComputerName | String | Computer name
OrderNumber | String | Order number
UserId | Long | Waiter Id
SalesAreaId | Long | Id of Sales Area
Items | [[TransactionOrderItem]](#transactionorderitem) | List of order items
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## TransactionOrderItem

> TransactionOrderItem Object

```xml
<item xsi:type="NS3:TTransactionOrderItem">
   <Id xsi:type="xsd:long">25000158207</Id>
   <ArticleId xsi:type="xsd:long">5000001722</ArticleId>
   <ItemNumber xsi:type="xsd:int">1</ItemNumber>
   <Kind xsi:type="xsd:int">1</Kind>
   <Quantity xsi:type="xsd:int">1</Quantity>
   <SinglePrice xsi:type="xsd:double">2</SinglePrice>
   <Price xsi:type="xsd:double">2</Price>
   <Discount xsi:type="xsd:double">0</Discount>
   <Vat xsi:type="xsd:double">0.3471</Vat>
   <VatPercent xsi:type="xsd:double">21</VatPercent>
   <Text xsi:type="xsd:string"/>
   <HqId xsi:type="xsd:string">Coca Cola</HqId>
   <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Internal Order item Id
ArticleId | Long | Article Id
ItemNumber | Integer | Number in order
Kind | Integer | 1. Article 2. Option 3. Message text
Quantity | Integer | Quantity of ordered articles
SinglePrice | Decimal | Single price
Price | Decimal | Total price
Discount | Decimal | Discount amount
Vat | Decimal | VAT amount
VatPercent | Decimal | Vat percent
Text | String | Text (in case when Id = 0)
HqId | String | HQ Id
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Description 
--- | ----------- 
`extra_taxes` | When requested in GetDetailedTurnoverRequest
`void` | When item is a result of a 'Void' operation (only when OnlyPaid = 0 in GetDetailedTurnoverRequest)

## TransactionProforma

> TransactionProforma Object

```xml
<item xsi:type="NS3:TTransactionProforma">
    <Id xsi:type="xsd:long">25000158236</Id>
    <DateTime xsi:type="xsd:dateTime">2018-12-12T11:41:49.000+01:00</DateTime>
    <UserId xsi:type="xsd:long">5000001377</UserId>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
Id | Long | Internal Proforma Id
DateTime | Timestamp | Date/time when Proforma was printed
UserId | Long | Id of waiter who printed the Proforma
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## TurnoverBill

> TurnoverBill Object

```xml
<item xsi:type="NS3:TTurnoverBill">
    <OpenDateTime xsi:type="xsd:dateTime">2018-09-21T08:21:02.000+02:00</OpenDateTime>
    <CloseDateTime xsi:type="xsd:dateTime">2018-09-21T08:21:02.000+02:00</CloseDateTime>
    <ComputerName xsi:type="xsd:string">TPAPIWIN7</ComputerName>
    <BillNumber xsi:type="xsd:int">38795</BillNumber>
    <BillSuffix xsi:type="xsd:string"/>
    <TableNumber xsi:type="xsd:int">103</TableNumber>
    <TablePart xsi:type="xsd:string">a</TablePart>
    <Covers xsi:type="xsd:int">5</Covers>
    <UserId xsi:type="xsd:long">65000358137</UserId>
    <SalesAreaId xsi:type="xsd:long">5000000146</SalesAreaId>
    <Items xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTurnoverBillItem[x]">...</Items>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
OpenDateTime | Timestamp | Transaction open date/time
CloseDateTime | Timestamp | Transaction close date/time
ComputerName | String | Computer name
BillNumber | Integer | Transaction number
BillSuffix | String | Transaction suffix
TableNumber | Integer | Table number
TablePart | String | Table part
Covers | Integer | Number of covers
UserId | Long | Id of the User
SalesAreaId | Long | Id of the Sales Area
Items | [[TurnoverBillItem]](#turnoverbillitem) | List of ordered items
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## TurnoverBillItem

> TurnoverBillItem Object

```xml
<item xsi:type="NS3:TTurnoverBillItem">
    <ArticleId xsi:type="xsd:long">15000028541</ArticleId>
    <DateTime xsi:type="xsd:dateTime">2018-09-21T08:21:02.000+02:00</DateTime>
    <ItemNumber xsi:type="xsd:int">0</ItemNumber>
    <ComputerName xsi:type="xsd:string">TESTPC</ComputerName>
    <Quantity xsi:type="xsd:int">3</Quantity>
    <Price xsi:type="xsd:double">15</Price>
    <UserId xsi:type="xsd:long">65000358137</UserId>
    <HqId xsi:type="xsd:string"/>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
ArticleId | Long | Article Id
DateTime | Timestamp | Date/time of ordering
ItemNumber | Integer | Number of item in order
ComputerName | String | Computer name
Quantity | Integer | Quantity of ordered items
Price | Decmial | Price
UserId | Long | Waiter Id
HqId | String | HQ Id
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## TurnoverTransaction

> TurnoverTransaction Object

```xml
<Transaction xsi:type="NS3:TTurnoverTransaction">
   <Id xsi:type="xsd:long">25000158204</Id>
   <OpenDateTime xsi:type="xsd:dateTime">2018-12-12T11:41:43.000+01:00</OpenDateTime>
   <CloseDateTime xsi:type="xsd:dateTime">1899-12-30T00:00:00.000+01:00</CloseDateTime>
   <TranNumber xsi:type="xsd:string">931</TranNumber>
   <TableNumber xsi:type="xsd:int">27</TableNumber>
   <TablePart xsi:type="xsd:string">a</TablePart>
   <Covers xsi:type="xsd:int">0</Covers>
   <UserId xsi:type="xsd:long">5000001377</UserId>
   <DiscountOnTotal xsi:type="xsd:double">0</DiscountOnTotal>
   <ServiceCharge xsi:type="xsd:double">0</ServiceCharge>
   <ClientName xsi:type="xsd:string"/>
   <Orders xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTransactionOrder[x]">...</Orders>
   <Bills xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTransactionBill[x]">...</Bills>
   <Proformas xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTransactionProforma[x]">...</Proformas>
   <BillReprints xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTransactionBillReprint[x]">...</BillReprints>
   <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[1]">
      <item xsi:type="NS3:TExtraInfo">
         <Key xsi:type="xsd:string">service_tax</Key>
         <Value xsi:type="xsd:string">0</Value>
         <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
      </item>
   </Extra>
   <ClientId xsi:type="xsd:long">0</ClientId>
</Transaction>
```

Parameter | Type | Description
----------| -----| -----------
Id | Long | Internal Id of this Transaction
OpenDateTime | Timestamp | Transaction open date/time
CloseDateTime | Timestamp | Transaction close date/time (1899-12-30 is returned when the transaction is not closed yet)
TranNumber | String | Transaction number
TableNumber | Integer | Table number
TablePart | String | Table part
Covers | Integer | Number of covers
UserId | Long | Waiter Id
DiscountOnTotal | Decimal | Discount amount on transaction total
ServiceCharge | Decimal | Service charge, in percents
ClientName | String | Name of Client
ClientId | Long | Id of Client
Orders | [[TransactionOrder]](#transactionorder) | List of orders for this transaction
Bills | [[TransactionBill]](#transactionbill) | List of bills for this transaction
Proformas | [[TransactionProforma]](#transactionproforma) | List of proformas for this transaction
BillReprints | [[TransactionBillReprint]](#transactionbillreprint) | List of bill re-prints
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`service_tax` | String | Percent value of Service Tax applied to the transaction
`service_charge_amount` | String | Service charge amount, only returned when service charge is applied
`course_id` | Long | Course Id
`extra_taxes` | Extra taxes | Optionally
`dscount_reason` | Discount reason | Optionally
`modified` | Timestamp | Optionally (YYYYMMDD-HHMMSS)

## UserGroup

> UserGroup Object

```xml
<Group xsi:type="NS3:TUserGroup">
    <GroupId xsi:type="xsd:long">5000000575</GroupId>
    <GroupName xsi:type="xsd:string">Manager</GroupName>
</Group>
```

Parameter | Type | Description
----------| ---- | -----------
FromTable | Integer | Internal Table range start
ToTable | Integer | Table range end

## UserInfo

> UserInfo Object

```xml
<item xsi:type="NS3:TUserInfo">
    <UserId xsi:type="xsd:long">50000309682</UserId>
    <UserName xsi:type="xsd:string">unTill</UserName>
    <FirstName xsi:type="xsd:string">John</FirstName>
    <LastName xsi:type="xsd:string">Doe</LastName>
    <Group xsi:type="NS3:TUserGroup">...</Group>
    <Credentials xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TCredential[x]">...</Credentials>
    <Language xsi:type="NS3:TLanguage">
        <LangCode xsi:type="xsd:string">0000</LangCode>
        <Language xsi:type="xsd:string">English (Default)</Language>
    </Language>
    <Void xsi:type="xsd:boolean">true</Void>
    <ClockIn xsi:type="xsd:boolean">false</ClockIn>
    <TagReaderCode xsi:type="xsd:string"/>
    <OperatorId xsi:type="xsd:string">123</OperatorId>
    <Address xsi:type="xsd:string">Choorhoeksweg 8</Address>
    <Country xsi:type="xsd:string">Netherlands</Country>
    <Phone xsi:type="xsd:string">+31123456789</Phone>
    <Birthdate xsi:type="xsd:dateTime">1986-08-15T00:00:00.000+02:00</Birthdate>
    <Insurance xsi:type="xsd:string">00000000097</Insurance>
    <HourlyWage xsi:type="xsd:double">15</HourlyWage>
    <HourlyWages xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:THourlyWageItem[x]">...</HourlyWages>
    <Void_number xsi:type="xsd:int">0</Void_number>
    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
</item>
```

Parameter | Type | Description
----------| ---- | -----------
UserId | Long | Internal Id of this User
UserName | String | Name of this User
FirstName | String | First name of this User
LastName | String | Last name of this User
Group | [UserGroup](#usergroup) | Group this user belongs to
Credentials | [[Credential]](#credential) | List of assigned credentials
Language | Language | User language
Void | Boolean | True if this User is allowed to void ordered Articles
ClockIn | Boolean | True if this User has time registration enabled
TagReaderCode | String | Tag Reader Code, Base64 encoded
OperatorId | String | Value passed to EFT-devices
Address | String | Address of this User
Country | String | Country of this User
Phone | String | Phone number of this User
Birthdate | Timestamp | Birtdate of this User
Insurance | String | Insurance number of this User
HourlyWage | Decimal | Deprecated since v1.4 (unTill build 92)
HourlyWages | [[HourlyWageItem]](#hourlywageitem) | List of hourly wages for this User (since v1.4 (unTill build 92))
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields
