# Database Information Functions

## GetArticles

Returns a brief list of the available Articles in the unTill database.

### GetArticles Request

> GetArticles Request

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

### GetArticles Response

> GetArticles Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetArticlesResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetArticlesResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Articles xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TArticleShort[x]">...</Articles>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetArticlesResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Articles | [[ArticleShort]](#articleshort) | Array of articles
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetArticlesInfo

Returns a detailed list of the Articles and their options.

### GetArticlesInfo Request

> GetArticlesInfo Request

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
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`course_id` | Long | Only return articles of a specific course
`dailystock` | Boolean | Additionally return data about the daily stock status for all Articles. The data is returned in the ArticleInfo.Extra field
`plu` | List of PLU | Searches Articles by PLU number. The list of PLU can either be a single PLU number or a comma-separated list

### GetArticlesInfo Response

> GetArticlesInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetArticlesInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetArticlesInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Articles xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TArticleInfo[x]">...</Articles>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetArticlesInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Articles | [[ArticleInfo]](#articleinfo) | Array of articles
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetOptionsInfo

Returns a list of the active Options in the unTill database.

### GetOptionsInfo Request

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

### GetOptionsInfo Response

> GetOptionsInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetOptionsInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetOptionsInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Options xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TOptionInfo[x]">...</Options>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetOptionsInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Options | [[OptionInfo]](#optioninfo) | Array of Options
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetDepartmentsInfo

Returns a list of the active Departments in the unTill database.

### GetDepartmentsInfo Request

> GetDepartmentsInfo Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetDepartmentsInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetDepartmentsInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <SalesAreaId xsi:type="xsd:long">0</SalesAreaId>
            <DepartmentId xsi:type="xsd:long">0</DepartmentId>
         </Request>
      </urn:GetDepartmentsInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
---------- | ------- | ------- | -------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
SalesAreaId | Long | Optional | Specify to request Departments of a certain Sales Area only
DepartmentId | Long | Optional | Specify to request information of a certain Department only

### GetDepartmentsInfo Response

> GetDepartmentsInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetDepartmentsInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetDepartmentsInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Departments xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TDepartmentInfo[x]">...</Departments>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetDepartmentsInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Departments | [[DepartmentInfo]](#departmentinfo) | Array of Departments
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetGroupsInfo

Returns a list of the active Groups in the unTill database.

### GetGroupsInfo Request

> GetGroupsInfo Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetGroupsInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetGroupsInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetGroupsInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user

### GetGroupsInfo Response

> GetGroupsInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetGroupsInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetGroupsInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Groups xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TGroupInfo[x]">...</Groups>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetGroupsInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Groups | [[GroupInfo]](#groupinfo) | Array of Groups
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetCategoriesInfo

Returns a list of the active Categories in the unTill database.

### GetCategoriesInfo Request

> GetCategoriesInfo Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetCategoriesInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetCategoriesInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetCategoriesInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user

### GetCategoriesInfo Response

> GetCategoriesInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetCategoriesInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetCategoriesInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Categories xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TCategoryInfo[x]">...</Categories>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetCategoriesInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Categories | [[CategoryInfo]](#categoryinfo) | Array of Categories
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetPricesInfo

Returns a list of the active Prices in the unTill database.

### GetPricesInfo Request

> GetPricesInfo Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetPricesInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetPricesInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetPricesInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user

### GetPricesInfo Response

> GetPricesInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetPricesInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetPricesInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Prices xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TPriceInfo[x]">...</Prices>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetPricesInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Prices | [[PriceInfo]](#priceinfo) | Array of Prices
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetCourses

Returns a list of the active Courses in the unTill database.

### GetCourses Request

> GetCourses Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetCourses soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetCoursesRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">99999</Password>
            <UserName xsi:type="xsd:string">TPAPI</UserName>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetCourses>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

List of available extra fields:

Key | Description
--- | -----------
`id` | Searches for active Course by Id.
`is_active` | 1: Active only, 0: Inactive only, -1: Both active and inactive.

### GetCourses Response

> GetCourses Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetCoursesResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetCoursesResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
            <Courses xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TCourse[x]">...</Courses>
         </return>
      </NS1:GetCoursesResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Courses | [[Course]](#course) | Array of Courses
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetPaymentsInfo

Returns a list of the active Payments in the unTill database.

### GetPaymentsInfo

> GetPaymentsInfo Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetPaymentsInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetPaymentsInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetPaymentsInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user

### GetPaymentsInfo Response

> GetPaymentsInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetPaymentsInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetPaymentsInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Payments xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TPaymentInfo[x]">...</Payments>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetPaymentsInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Payments | [[PaymentInfo]](#paymentinfo) | Array of Payments
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetSalesAreasInfo

Returns a list of the active Sales Areas in the unTill database.

### GetSalesAreasInfo Request

> GetSalesAreasInfo Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetSalesAreasInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetSalesAreasInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetSalesAreasInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user

### GetSalesAreasInfo Response

> GetSalesAreasInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetSalesAreasInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetSalesAreasInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <SalesAreas xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TSalesAreaInfo[x]">...</SalesAreas>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetSalesAreasInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
SalesAreas | [[SalesAreaInfo]](#salesareainfo) | Array of Sales Areas
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetUsersInfo

Returns a list of the active Users in the unTill database.

### GetUsersInfo Request

> GetUsersInfo Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetUsersInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetUsersInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
         </Request>
      </urn:GetUsersInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user

### GetUsersInfo Response

> GetUsersInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetUsersInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetUsersInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Users xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TUserInfo[x]">...</Users>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetUsersInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Users | [[UserInfo]](#userinfo) | Array of active Users
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetDiscountGroups

Returns list of discount groups with details.

### GetDepartmentsInfo Request

> GetDepartmentsInfo Request

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

### GetDiscountGroups Response

> GetDiscountGroups Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetDiscountGroupsInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetDiscountGroupsInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <DiscountGroups xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TDiscountGroupInfo[x]">...</DiscountGroups>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetDiscountGroupsInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
DiscountGroups | [[DiscountGroupInfo]](#discountgroupinfo) | Array of Discount Groups
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetCountries

Returns the list of countries, declared in the backoffice.

### GetCountries Request

> GetCountries Request

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
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`id` | String | Search Country by Id.
`is_active` | 1 / 0 / -1 | 1: Active only, 0: Inactive only, -1: Both active and inactive

### GetCountries Response

> GetCountries Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetCountriesResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetCountriesResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Countries xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TCountry[x]">...</Countries>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetCountriesResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Countries | [[Country]](#country) | Array of Countries
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetSuppliersInfo

Returns the list of suppliers, declared in the backoffice.

### GetSuppliersInfo Request

> GetSuppliersInfo Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetSuppliersInfo soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetSuppliersInfoRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetSuppliersInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`is_active` | 1 / 0 / -1 | 1: Active only (default), 0: Inactive only, -1: Both active and inactive

### GetSuppliersInfo Response

> ### GetSuppliersInfo Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetSuppliersInfoResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetSuppliersInfoResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Items xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TSupplierInfo[x]">...</Items>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetSuppliersInfoResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Items | [[Supplier]](#supplier) | Array of Suppliers
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields