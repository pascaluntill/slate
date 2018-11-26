# GetCourses

Returns a list of the active Courses in the unTill database.

## The Course Object

> Course Object:

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
Extra | [ExtraInfo] | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description | Read | Write
--- | ----- | ----------- | ---- | -----
`is_active` | 1/ 0 | Activity flag. | Always | N/A

## The GetCourses Request

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
Extra | [ExtraInfo] | Optional | List of extra fields

### Extra Fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`id` | Long | Searches for active Course by Id.
`is_active` | 1 / 0 / -1 | 1: Active only, 0: Inactive only, -1: Both active and inactive.
