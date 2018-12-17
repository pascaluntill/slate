# Reporting Functions

## GetTurnoverReport

Get the list of Transactions including the ordered items.

### GetTurnoverReport Request

> GetTurnoverReport Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetTurnoverReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetTurnoverReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <UserId xsi:type="xsd:long">0</UserId>
            <SalesAreaId xsi:type="xsd:long">0</SalesAreaId>
            <From xsi:type="xsd:dateTime">2018-09-21T08:00:00+02:00</From>
            <Till xsi:type="xsd:dateTime">2018-09-22T08:00:00+02:00</Till>
         </Request>
      </urn:GetTurnoverReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
UserId | Long | Optional | Specify to request the report for a certain User only
SalesAreaId | Long | Optional | Specify to request report of a certain Sales Area only
From | Timestamp | Mandatory | Report start date/time
Till | Timestamp | Mandatory | Report end date/time

### GetTurnoverReport Response

> GetTurnoverReport Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetTurnoverReportResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetTurnoverReportResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Data xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTurnoverBill[x]">...</Data>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetTurnoverReportResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Data | [[TurnoverBill]](#turnoverbill) | List of bills with included items
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetDetailedTurnoverReport

Returns the detailed list of transactions for the specified period. For each transaction, a list of orders, bills, proformas and re-prints is returnd.

### GetDetailedTurnoverReport Request

> GetDetailedTurnoverReport Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetDetailedTurnoverReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetDetailedTurnoverReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <From xsi:type="xsd:dateTime">2018-09-11T08:00:00+01:00</From>
            <Till xsi:type="xsd:dateTime">2018-09-12T08:00:00+01:00</Till>
            <SalesAreaId xsi:type="xsd:long">0</SalesAreaId>
            <Extra xsi:type="urn:TExtraInfoArray" soapenc:arrayType="urn:TExtraInfo[1]">
 	           <item xsi:type="urn:TExtraInfo">
	  			<Key xsi:type="xsd:string">OnlyPaid</Key>
				<Value xsi:type="xsd:string">1</Value>
		      </item>
	       </Extra>
         </Request>
      </urn:GetDetailedTurnoverReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
From | Timestamp | Mandatory | Report start date/time
Till | Timestamp | Mandatory | Report end date/time
SalesAreaId | Long | Optional | Specify to request report of a certain Sales Area only
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

List of available extra fields:

Key | Value | Description
--- | ----- | -----------
`OnlyPaid` | Boolean | When true, it includes only order items which have been paid during this period. By default this property is “False”
`TaxesPerBill` | Boolean | When true, it returns information about extra taxes in TurnoverTransaction.ExtraFields: `service_charge_amount` and `vat_on_service_charge_amount`
`TaxesPerOrderItem` | Boolean | When true, it returns information about extra taxes in TransactionOrderItem.ExtraFields: `service_charge_amount` and `vat_on_service_charge_amount`
`DiscountReason` | Boolean | When true, it returns name of discount reason in TransactionOrderItem.ExtraFields (Key = `discount_reaon`)
`ModificationDates` | Boolean | When true, it returns transaction modification dates in TurnoverTransaction.ExtraFields (Key = `modified`)
`IncludeReopen` | Boolean | When true, re-opened bills are included in transactions (disabled by default). Fe. when a bill is paid with CASH, then re-opened and paid by VISA, all three bills will be included: 1. Positive CASH, 2. Negative CASH and 3. Positive VISA
`EftExtras` | String | Comma-separated list of EFT fields which should be returned in TransactionBillPayment.ExtraFields for card payments. List of possible fields can be found in App 3. Constants. The meaning of the values contained in these fields depend on the EFT model used for processing card payments
`TranExtras` | Boolean | When true, it returns user-defined extra fields in TurnoverTransaction.ExtraFields (when specified in the CreateOrderrequest)
`BillNumber` | String | When specified, only those transaction(s) are returned which have a bill with the specified number
`BillSuffix` | String | Can be specified in addition to `BillNumber`. If not specified, it means that unTill searches for bills with any (or without) a suffix
`TranNumber` | String | When specified, only those transaction(s) are returned which have the specified number
`TranSuffix` | String | Can be specified in addition to `TranNumber`. If not specified, it means that unTill searches for transactions with any (or without) a suffix
`LookupByFirstBill` | Boolean | Whe set to true, then it searches by the time of first bill. If the first bill in the transaction is made in the specified time range, this transaction is included in the response with all it’s history. Can be combined with `OnlyPaid` and `IncludeReopen` extras.

### GetDetailedTurnoverReport Response

> GetDetailedTurnoverReport Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetDetailedTurnoverReportResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetDetailedTurnoverReportResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Data xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTurnoverTransaction[x]">...</Data>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetDetailedTurnoverReportResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Data | [[TurnoverTransaction]](#turnovertransaction) | List of transactions with included orders & payments
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetCancelledItemsReport

Returns the list of articles which have been cancelled (added to an order and then removed by “Cancel” or “Void” button).

### GetCancelledItemsReport Request

> GetCancelledItemsReport Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetCancelledItemsReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetCancelledItemsReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <From xsi:type="xsd:dateTime">2018-11-20T08:00:00+01:00</From>
            <Till xsi:type="xsd:dateTime">2018-11-21T08:00:00+01:00</Till>
         </Request>
      </urn:GetCancelledItemsReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
From | Timestamp | Mandatory | Report start date/time
Till | Timestamp | Mandatory | Report end date/time

### GetCancelledItemsReport Response

> GetCancelledItemsReport Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetCancelledItemsReportResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetCancelledItemsReportResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Items xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TCancelledItem[x]">...</Items>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetCancelledItemsReportResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Items | [[CancelledItem]](#cancelleditem) | List of cancelled items
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetDepositsReport

Returns the list of deposits per time period.

### GetDepositsReport Request

> GetDepositsReport Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetDepositsReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetDepositsReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <From xsi:type="xsd:dateTime">2018-11-20T08:00:00+01:00</From>
            <Till xsi:type="xsd:dateTime">2018-11-21T08:00:00+01:00</Till>
            <SalesAreaId xsi:type="xsd:long">0</SalesAreaId>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetDepositsReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
From | Timestamp | Mandatory | Report start date/time
Till | Timestamp | Mandatory | Report end date/time
SalesAreaId | Long | Optional | Specify to request report for a certain Sales Area only

### GetDepositsReport Response

> GetDepositsReport Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetDepositsReportResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetDepositsReportResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Items xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TDepositItem[x]">...</Items>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetDepositsReportResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Items | [[DepositItem]](#deposititem) | List of deposits
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetTimeAttendanceReport

Get the Time and Attendance report.

### GetTimeAttendanceReport Request

> GetTimeAttendanceReport Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetTimeAttendanceReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetTimeAttendanceRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <UserId xsi:type="xsd:long">5000000575</UserId>
            <From xsi:type="xsd:dateTime">2018-07-01T08:00:00+02:00</From>
            <Till xsi:type="xsd:dateTime">2018-07-01T08:00:00+02:00</Till>
         </Request>
      </urn:GetTimeAttendanceReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
UserId | Long | Optional | Specify to request the report for a certain User only
From | Timestamp | Mandatory | Report start date/time
Till | Timestamp | Mandatory | Report end date/time

### GetTimeAttendanceReport Response

> GetTimeAttendanceReport Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetTimeAttendanceReportResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetTimeAttendanceResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Data xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TTimeAttendanceRecord[x]">...</Data>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetTimeAttendanceReportResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Data | [[TimeAttendanceRecord]](#timeattendancerecord) | List of time & attendance records
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## GetInOutCashReport

Returns the list of “In/Out” cash entries from the database per time period.

### GetInOutCashReport Request

> GetInOutCashReport Request

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:GetInOutCashReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TGetInOutCashReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <From xsi:type="xsd:dateTime">2018-11-20T08:00:00+01:00</From>
            <Till xsi:type="xsd:dateTime">2018-11-21T08:00:00+01:00</Till>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:GetInOutCashReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
----------| ---- | -------| -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
From | Timestamp | Mandatory | Report start date/time
Till | Timestamp | Mandatory | Report end date/time

### GetInOutCashReport Response

> GetInOutCashReport Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:GetInOutCashReportResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TGetInOutCashReportResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Items xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TInOutCashItem[x]">...</Items>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
         </return>
      </NS1:GetInOutCashReportResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Items | [[InOutCashItem]](#inoutcashitem) | List of in/out cash entries
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

## PrintReport

Allows to print a report or return it in response as plain text.

### PrintReport Request

> PrintReport Request:

```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:TPAPIPosIntfU-ITPAPIPOS" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:PrintReport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <Request xsi:type="urn:TPrintReportRequest" xmlns:urn="urn:TPAPIPosIntfU">
            <Password xsi:type="xsd:string">KxydW9kstVhfbwCjVdF68XJTDk4sKB</Password>
            <UserName xsi:type="xsd:string">unTill</UserName>
            <LayoutId xsi:type="xsd:long">5000001172</LayoutId>
            <PrinterId xsi:type="xsd:long">0</PrinterId>
            <From xsi:type="xsd:dateTime">2018-11-20T08:00:00+01:00</From>
            <Till xsi:type="xsd:dateTime">2018-11-21T08:00:00+01:00</Till>
            <Arguments xsi:type="urn1:TKeyValueArray" soapenc:arrayType="urn1:TKeyValue[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
            <Extra xsi:type="urn1:TExtraInfoArray" soapenc:arrayType="urn1:TExtraInfo[]" xmlns:urn1="urn:TPAPIPosTypesU"/>
         </Request>
      </urn:PrintReport>
   </soapenv:Body>
</soapenv:Envelope>
```

Parameter | Type | Status | Description
--------- | ---- | ------ | -----------
Username | String | Mandatory | Username of unTill user
Password | String | Mandatory | TPAPI password of unTill user
LayoutId | Long | Mandatory | Report layout Id
PrinterId | Long | Mandatory | Id of the printer where to print the report to. If `0` is specified, the result is sent in the response as plain text
From | Timestamp | Optional | Report start date/time
Till | Timestamp | Optional | RReport end date/time
Arguments | [[KeyValue]](#keyvalue) | Optional | Report arguments
Extra | [[ExtraInfo]](#extrainfo) | Optional | List of extra fields

### PrintReport Response

> PrintReport Response

```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/">
   <SOAP-ENV:Body SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:NS1="urn:TPAPIPosIntfU-ITPAPIPOS">
      <NS1:PrintReportResponse xmlns:NS2="urn:TPAPIPosIntfU" xmlns:NS3="urn:TPAPIPosTypesU">
         <return xsi:type="NS2:TPrintReportResponse">
            <ReturnCode xsi:type="xsd:int">0</ReturnCode>
            <ReturnMessage xsi:type="xsd:string">ok</ReturnMessage>
            <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[2]">
               <item xsi:type="NS3:TExtraInfo">
                    <Key xsi:type="xsd:string">receipt_text</Key>
                    <Value xsi:type="xsd:string">*** REPORT TEXT ***</Value>
                    <Extra xsi:type="SOAP-ENC:Array" SOAP-ENC:arrayType="NS3:TExtraInfo[0]"/>
               </item>
            </Extra>
         </return>
      </NS1:PrintReportResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Parameter | Type | Description
----------| -----| -----------
ReturnCode | Integer | [Return code](#return-codes)
ReturnMessage | String | [Return message](#return-codes)
Extra | [[ExtraInfo]](#extrainfo) | List of extra fields

List of available extra fields:

Key | Description
--- | -----------
`receipt_text` | Text of the report in plain text when PrinterId = 0 is specified in request
