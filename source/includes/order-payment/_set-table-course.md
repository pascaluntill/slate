# SetTableCourse

Apply certain course to table. When course is not changed because given course is already set, no error will be returned.
If it is unable to set given course for this table, the ReturnCode will be 7 with ReturnMessage: “Unable to change table course to [...]”

## The SetTabeCourse Request

> SetTableCourse Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:SetTableCourse soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TSetTableCourseRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <TableNumber xsi:type="xsd:int">1</TableNumber>
            <TablePart xsi:type="xsd:string">a</TablePart>
            <CourseId xsi:type="xsd:long">5000001334</CourseId>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:SetTableCourse>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
TableNumber | Integer | Mandatory | Table number to apply course to
TablePart | String | Mandatory | Table part to apply course to ("a" - "f")
CourseId | Long | Mandatory | Course to apply to the table
