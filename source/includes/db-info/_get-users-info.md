# GetUsersInfo

Returns a list of the active Users in the unTill database.

## The GetUsersInfo Object

> UserInfo Object:

```xml
<item xsi:type="NS3:TUserInfo">
    <UserId xsi:type="xsd:long">50000309682</UserId>
    <UserName xsi:type="xsd:string">unTill</UserName>
    <FirstName xsi:type="xsd:string">John</FirstName>
    <LastName xsi:type="xsd:string">Doe</LastName>
    <Group xsi:type="NS3:TUserGroup">
        <GroupId xsi:type="xsd:long">5000000575</GroupId>
        <GroupName xsi:type="xsd:string">Manager</GroupName>
    </Group>
    <Credentials xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TCredential[2]">
        <item xsi:type="NS3:TCredential">
            <CredentialGuid xsi:type="xsd:string">{56DAFD3A-B188-43A5-B337-EFE84DB88C33}</CredentialGuid>
            <CredentialName xsi:type="xsd:string">Administrator</CredentialName>
        </item>
        <item xsi:type="NS3:TCredential">
            <CredentialGuid xsi:type="xsd:string">{083CC05D-4569-4057-AF67-1FEB7B352CB1}</CredentialGuid>
            <CredentialName xsi:type="xsd:string">Supervisor</CredentialName>
        </item>
    </Credentials>
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
    <HourlyWages xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:THourlyWageItem[1]">
        <item xsi:type="NS3:THourlyWageItem">
            <Position xsi:type="xsd:string">Manager</Position>
            <HourlyWage xsi:type="xsd:double">15</HourlyWage>
            <HourlyWageOvertime xsi:type="xsd:double">22.5</HourlyWageOvertime>
        </item>
    </HourlyWages>
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
Group | UserGroup | Group this user belongs to
Credentials | [Credential] | List of assigned credentials
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
HourlyWages | [HourlyWageItem] | List of hourly wages for this User (since v1.4 (unTill build 92))
Extra | [ExtraInfo] | List of extra fields

## The GetUsersInfo Request

> GetUsersInfo Request:

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
