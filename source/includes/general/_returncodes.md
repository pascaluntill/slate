# Return Codes

Each function returns a `ResultCode` and a `ResultMessage`. When the function completes without any errors, the `ResultCode` will be `0` and the `ResultMessage` will be `ok`. For the complete list of result codes, please see the table below:


Result Code | Result Message | Description
----------- | -------------- | -----------
0 | ok | The operation completed without any errors
1 | Exception class, message, stacktrace | Internal server error
2 | Authentication error | Authentication error
3 | Details | Illegal request argument (fe. incorrect SalesAreaId)
4 | Details | Database not available
5 | Details | TPAPI disabled
6 | TPAPI not allowed by unTill license | The TPAPI module is not enabled in the license
7 | Reason | Your request cannot be processed
