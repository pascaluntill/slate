# GetArticles

Returns a brief list of the available Articles in the unTill database.

## The ArticleShort Object

> ArticleShort Object:

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
Extra | ExtraInfo[] | List of extra fields

## The GetArticles Request

> GetArticles Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetArticles soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetArticlesRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <SalesAreaId xsi:type="xsd:long">5000000208</SalesAreaId>
         </Request>
      </urn:GetArticles>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
SalesAreaId | Long | Optional | Specify to request Articles of a certain Sales Area only
