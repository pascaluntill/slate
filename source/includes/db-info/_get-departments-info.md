# GetDepartmentsInfo

Returns a list of the active Departments in the unTill database.

## The DepartmentsInfo Object

> DepartmentInfo Object:

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
Extra | [ExtraInfo] | List of extra fields

## The GetDepartmentsInfo Request

> GetDepartmentsInfo Request:

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
