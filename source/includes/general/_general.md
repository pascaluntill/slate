# Introduction

Welcome to the TPAPI-POS API! unTill Server provides a SOAP interface for 3rd party applications which may be used for remotely working with POS: reading configuration, making orders, etc.: TPAPI-POS API.

You can view code samples in the dark area to the right, and switch the programming language of the examples with the tabs in the top right (currently we have only XML available but we might add more later).

In case you might have any questions about our API, please <a href="http://integrations.untill.com/support/tickets/new" target="_blank">create a new support ticket</a> or contact us by sending an email to <a href="mailto:systemintegration@untill.com">systemintegration@untill.com</a>.

<aside class="notice">You must replace the <code>UserName</code> and <code>Password</code> used in the sample requests with the credentials provided to you by your unTill Database Administrator.</aside>

# Architecture Overview

## Control Flow

* 3rd party software calls SOAP functions, provided by unTill Server
* unTill Server communicates to a special instance of unTill.exe which runs in background
* unTill.exe performs the required action and sends back the result

## TPAPI-POS Entry Point

The TPAPI-POS WSDL consists of the hostname, port and looks like this:

<b>http://&lt;hostname&gt;:&lt;port&gt;/wsdl/ITPAPIPOS</b>

URL example: <a href="http://testapi.untill.com:3063/wsdl/ITPAPIPOS" target="_blank">http://testapi.untill.com:3063/wsdl/ITPAPIPOS</a>

This WSDL can be used to generate a client for the TPAPI web-service on any programming language. The default port is UNTILLSRV_PORT+3 but this may be redefined in untill.ini, if required: 
    
<i>[common]<br>
soapport=7777</i>

The default UNTILLSRV_PORT is 3060, if not redefined in untill.ini with “port” setting.<br>

<aside class="warning">Do not specify “soapport” to values in the range of UNTILLSRV_PORT .. UNTILLSRV_PORT+5, because they can be blocked by other unTill services. Only UNTILLSRV_PORT+3 is always reserved for TPAPI.<br><br><center><strong>Please note that each individual client location has its own TPAPI-POS Entry Point.<br>There is no single (cloud) Entry Point which redirects all calls to client instances.</strong></center></aside>

## Reading POS Configuration

The POS configuration should be read using the following algorythm:

1. Read the list of Sales Areas with [GetSalesAreasInfo](#getsalesareasinfo)
2. Read the list of Prices with [GetPricesInfo](#getpricesinfo)
3. Read the list of Options with [GetOptionsInfo](#getoptionsinfo)
4. Read the list of Departments with [GetDepartmentsInfo](#getdepartmentsinfo)
6. Read the list of Articles with [GetArticlesInfo](#getarticlesinfo)
6. Read the list of Payments with [GetPaymentsInfo](#getpaymentsinfo)

This sequence may be repeated from time to time to keep POS configuration up-to-date on the client side.

For convenience, a part of the backoffice hierarchy is shown below:

* Categories
    * Groups
        * Departments
            * Condiment
            * Supplement
            * Articles
                * Must-have options
                * Free option

***Please note that each Department, Article and Option has it's own availability settings.***

After the configuration has been received, [GetActiveOrders](#getactiveorders) may be called at any time to get the current availability of tables. Use [CreateOrder](#createorder) for creating a new order, and [CloseOrder](#closeorder) for paying and closing an existing order.<br>
Some functions require `TableNumber` and `TablePart`, where `TablePart` is a letter in the range from “a” to “f”. Other values are not accepted.

## Ordering Overview

The following [articles and option types](#order-item-types) can be ordered with TPAPI:

* <b>Regular articles</b>
* <b>Must-have options for an article:</b> When an article has must-have options (`Options`) configured, you must process all of them and add one item of each option group to the order as “Must have option”.
* <b>Free option for an article:</b> When an article has a free option (`FreeOption`) configured, the articles in this option group can be added to this article as “Free option”. Please note that the items in this option group are not for free by default (price 0), the option is just not required to be used.
* <b>Supplements for an article:</b> When a department has a Supplement (`Supplement`) configured, the articles in this option group can be added as “Supplement” to all regular items which belong to this deparment.
* <b>Condiments for an article:</b> When a department has a Condiment (`Condiment`) configured, the articles in this option group can be added as “Condiment” to all regular items which belong to this deparment. 
* <b>Menu items:</b> When a certain article is a menu (`IsMenu` = true), the list of “must-have options” (`Options`) for this article acts as a list of article-groups. You may order one article per option and this article needs to be included into order as “Menu item”.
* <b>Article message:</b> Text which may be informative either for certain order item, the order part or the complete order.

To identify the item type, there is the `OrderItemType` field in the [OrderItem](#orderitem) structure. It is not required to specify in [CreateOrderRequest](#createorder-request) if certain article has `IsMenu` enabled: the only requirement is to identify it’s menu items. Below there are a few examples. Order items are shown hierarchically just for convenience. In the list of items they follow one after another.

* <b>List of regular articles:</b>
    * Article 1: `OrderItemType` = 0
    * Article 2: `OrderItemType` = 0
    * ...
* <b>Article with “Must-have” options:</b>
    * Article 1: `OrderItemType` = 0
        - Must-have option 1, article 1: `OrderItemType` = 1
        - Must-have option 2, article 1: `OrderItemType` = 1
        - ...
* <b>Article with different types of options:</b>
    * Article 1: `OrderItemType` = 0
        - Must-have option 1, article 1: `OrderItemType` = 1
        - Must-have option 2, article 1: `OrderItemType` = 1
        - Free option, article 1: `OrderItemType` = 2
        - Condiment, article 1: `OrderItemType` = 4
        - Supplement, article 1: `OrderItemType` = 3
        - Supplement, article 2: `OrderItemType` = 3
* <b>Menus:</b>
    * Menu 1: `OrderItemType` = 0 (article with `IsMenu` = true)
        - Option 1, article 1: `OrderItemType` = 5
        - Option 2, article 1: `OrderItemType` = 5
        - Option 3, article 1: `OrderItemType` = 5
* <b>Each menu item may also have options:</b>
    * Menu 1: `OrderItemType` = 0 (article with `IsMenu` = true)
        - Option 1, article 1: `OrderItemType` = 5
        - Option 2, article 1: `OrderItemType` = 5
            - Must-have option 1, article 1: `OrderItemType` = 1
            - Must-have option 2, article 1: `OrderItemType` = 1
        - Option 3, article 1: `OrderItemType` = 5
* <b>Article with free text:</b>
    * Article 1: `OrderItemType` = 0
        - Free text 1: `OrderItemType` = 6
    * Article 2: `OrderItemType` = 0
    * ...
    