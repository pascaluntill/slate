# GetGroupsInfo

Returns a list of the active Groups in the unTill database.

## The GroupsInfo Object

> GroupInfo Object:

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
Extra | [ExtraInfo] | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description 
--- | ----- | ----------- 
`bookkeeping_turnover` | String | Bookkeeping turnover number
`bookkeeping_vat` | String | Bookkeeping VAT number

## The GetGroupsInfo Request

> GetGroupsInfo Request:

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
