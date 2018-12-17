# Version History

Version | yyyy/mm/dd | unTill version | Changes
------- | ---------- | -------------- | -------
1.0 | 2011/05/05 | 88 | Initial version
1.1 | 2011/09/01 | 90.1 | New functions [GetUsersInfo](#getusersinfo), [GetArticlesInfo](#getarticlesinfo), [GetTurnoverReport](#getturnoverreport) and [GetTimeAttendanceReport](#gettimeattendancereport) added
1.2 | 2011/09/22 | 90.9 | Fixes deserialization message problem
1.4 | 2012/01/17 | 92 | New field `HourlyWages` added to [UserInfo](#userinfo)
1.5 | 2012/02/03 | 92 | New function [GetDetailedTurnoverReport](#getdetailedturnoverreport) added
1.6 | 2012/02/07 | 92 | New fields `Promo` added to [ArticleInfo](#articleinfo)<br>New field `SpecialArticles` added to [DepartmentInfo](#departmentinfo)
1.7 | 2012/05/28 | 95 | New field HQ Id added
1.8 | 2012/06/28 | 96 | New field `HqId` added to [TurnoverTransaction](#turnovertransaction)<br> New field `Covers` added to [CreateOrderRequest](#createorder-request)
1.9 | 2012/08/22 | 96 | New field `HqId` added to [TurnoverBillItem](#turnoverbillitem)
1.10 | 2012/09/18 | 96 | New function [GetClients](#getclients) added
1.11 | 2012/10/09 | 97 | New fields `Proformas` and `BillReprints` added to [TurnoverTransaction](#turnovertransaction)
1.12 | 2012/10/10 | 97 | New function [GetVersion](#getversion) added
1.13 | 2012/10/22 | 97 | New function [GetCancelledItemsReport](#getcancelleditemsreport) added
1.14 | 2012/10/24 | 98 | New field `SalesAreaId` added to [GetDetailedTurnoverReportRequest](#getdetailedturnoverreport-request)
1.15 | 2012/10/28 | 98 | New field `Extra` added to all response classes to support additional fields
1.16 | 2012/12/21 | 101 | New function [ClientDeposit](#clientdeposit) added
1.17 | 2013/05/27 | 101 | New field `ClientId` added to [TurnoverTransaction](#turnovertransaction) and [TransactionBill](#transactionbill)
1.18 | 2013/07/24 | 101 | New field `ClientId` added to [CreateOrder](#createorder)
1.19 | 2014/01/24 | 102.4 | New Extra `extra_taxes` added to [TurnoverTransaction](#turnovertransaction)
1.20 | 2014/01/27 | 103 | New functions [UpdateClients](#updateclients) and [GetClientsEx](#getclientsex) added
1.21 | 2014/02/04 | 102.6 | New Extra `extra_taxes` added to [TurnoverTransaction](#turnovertransaction)
1.22 | 2014/03/14 | 103.6 | New Extras `bookkeeping_vat` and `bookkeeping_turnover` to [GroupInfo](#groupinfo)
1.23 | 2014/04/04 | 104 | New function [NextCourse](#nextcourse) added
1.24 | 2014/04/07 | 104 | New Extras `TaxesPerBill` and `TaxesPerOrderItem` added to [GetDetailedTurnoverReportRequest](#getdetailedturnoverreport-request)
1.25 | 2014/04/09 | 104.1 | Fixed [Order item types table](#order-item-types)
1.26 | 2014/05/05 | 105 | New Extra `DailyStock` added to [GetArticlesInfoRequest](#getarticlesinfo-request)
1.27 | 2014/08/29 | 107 | New function [SetTableCourse](#settablecourse)<br> New Extra `course_id` added to [ArticleInfo](#articleinfo)
1.28 | 2014/09/16 | 107 | New Extra `info` added to [ArticleInfo](#articleinfo)
2.0 | 2015/04/01 | 108 | Initial version
2.1 | 2015/04/03 | 108.3 | New Extra `get_receipt` added to [ClientDeposit](#clientdeposit)
2.2 | 2015/04/06 | 109 | New function [GetDepositsReport](#getdepositsreport) added
2.3 | 2015/04/23 | 109 | New Extra `DiscountReason` added to [GetDetailedTurnoverReportRequest](#getdetailedturnoverreport-request)
2.4 | 2015/05/05 | 109 | New Extra `ModificationDates` added to [GetDetailedTurnoverReportRequest](#getdetailedturnoverreport-request)
2.5 | 2015/05/20 | 109 | New Extra `result_ids` added to [UpdateClientsResponse](#updateclients-response)
2.6 | 2015/06/03 | 110 | TPAPI performance improvements
2.7 | 2015/06/24 | 110 | New function [GetInOutCashReport](#getinoutcashreport) added
2.8 | 2015/07/22 | 110.12 | Added the possibility to create Orders In Future using [CreateOrder](#createorder)
2.9 | 2015/09/02 | 110.12 | New Extra `void` added to [TransactionOrderItem](#transactionorderitem)
2.10 | 2015/09/17 | 111.1 | New Extra `IncludeReopen”` added to [GetDetailedTurnoverReportRequest](#getdetailedturnoverreport-request)
2.11 | 2015/09/18 | 111.1 | New function [PrintProforma](#printproforma) added
2.12 | 2015/10/20 | 111.1 | New functions [GetCountries](#getcountries) and [UpdateCountries](#updatecountries) added<br> New Extra `country_id` added to [Client](#client)
2.13 | 2015/10/29 | 111.1 | New function [PrintReport](#printreport) added
2.14 | 2015/12/24 | 113.1 | New Extra `tip` added to [PayRequest](#pay-request)
2.15 | 2016/01/21 | 113.1 | New function [GetDiscountGroupsInfo](#getdiscountgroupsinfo)<br> New Extra `untill_version` added to [GetVersionResponse](#getversion-response)
2.16 | 2016/04/25 | 115.1 | New Extra `proforma_signature` added in [PayRequest](#pay-request)
2.17 | 2016/05/13 | 115.1 | New Extra `last` added to [OrderItem](#orderitem)
2.18 | 2016/06/20 | 115.1 | New Extra `smartcard_uid` added to [Client](#client) and [GetClientsExRequest](#getclientsex-request) (filter)<br> New Extra `plu` added to [ArticleInfo](#articleinfo) and [GetArticlesInfoRequest](#getarticlesinfo-request) (filter)<br> New function [AddPouring](#addpouring)<br> New Extra `EftExtras` and `TranExtras` added to [GetDetailedTurnoverReportRequest](#getdetailedturnoverreport-request)
2.19 | 2016/11/21 | 116.1 | New function [GetCourses](#getcourses) added<br> New Extra `OifDepositAmount` and `OifDepositPaymentModeId` added to [CreateOrderRequest](#createorder-request)
2.20 | 2017/05/11 | 120.1 | New Extra `purchase_price` added to [ArticleInfo](#articleinfo)<br> New Extra `service_charge_amount` added to [TurnoverTransaction](#turnovertransaction)
2.21 | 2017/07/05 | 122.1 | New Extra `BillNumber`, `BillSuffix` `TranNumber` and `TranSuffix` added to [GetDetailedTurnoverReportRequest](#getdetailedturnoverreport-request)
2.22 | 2017/10/20 | 125.1 | New Extra `LookupByFirstBill` added to [GetDetailedTurnoverReportRequest](#getdetailedturnoverreport-request)
2.23 | 2018/04/24 | 127.0 | New function [UpdateSalesAreaPrice](#updatesalesareaprice) added
2.24 | 2018/12/05 | 129.0 | New function [GetSuppliersInfo](#getsuppliersinfo) added
