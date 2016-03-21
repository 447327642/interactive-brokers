# Interactive Brokers API

This library provides a Haskell wrapper for the Interactive Brokers API. It is based on [version 9.70 of the IB Java API](http://interactivebrokers.github.io/downloads/twsapi_macunix.970.01.jar). The latest version at the time of writing is 9.72. See [the IB API home page](https://www.interactivebrokers.com/en/index.php?f=5041) for up-to-date information.

## Status

* Work in progress (see TODO.md for planned enhancements)
* Working sample apps that demonstrate currently supported messages
* A test suite has not yet been developed
* Performance analysis has not yet been conducted

## API Coverage

The following messages are currently supported.

### Requests

* ReqMktData
* CancelMktData
* PlaceOrder
* CancelOrder
* ReqOpenOrders
* ReqAccountData
* ReqExecutions
* ReqIds
* ReqContractData
* ReqAutoOpenOrders
* ReqAllOpenOrders
* ReqManagedAccounts
* ReqHistoricalData
* CancelHistoricalData
* ReqCurrentTime
* ReqRealTimeBars
* CancelRealTimeBars
* ReqGlobalCancel
* ReqMarketDataType
* ReqPositions
* ReqAccountSummary
* CancelAccountSummary
* CancelPositions

### Responses

* TickPrice
* TickSize
* OrderStatus
* ErrorMessage
* OpenOrder
* AccountValue
* PortfolioValue
* AccountUpdateTime
* NextValidId
* ContractData
* ExecutionData
* ManagedAccounts
* HistoricalData
* TickGeneric
* TickString
* CurrentTime
* RealTimeBar
* ContractDataEnd
* OpenOrderEnd
* ExecutionDataEnd
* TickSnapshotEnd
* MarketDataType
* CommissionReport
* Position
* PositionEnd
* AccountSummary
* AccountSummaryEnd

## Setup

Tested on GHC 7.10.3:

    git clone https://github.com/cmahon/interactive-brokers.git
    git clone https://github.com/cmahon/mvc-service.git
    cd interactive-brokers
    stack build
    
With IB TWS running, run the example applications:

    stack exec ib contracts ES
    stack exec requests-service
    stack exec requests-simple
    stack exec shell

## Sample Output (requests-simple)

```bash
$ stack exec requests-simple
Starting
2016-03-21 20:52:54 AEDT MVC.Socket DEBUG: socketService start
ServicePending
Just (IBResponse (NextValidId {_nvId = 1}))
Just (Log "4\NUL2\NUL-1\NUL2119\NULMarket data farm is connecting:usfuture\NUL")
Just (IBResponse (Error {_errId = -1, _errCode = 2119, _errDesc = "Market data farm is connecting:usfuture"}))
Just (Log "10\NUL8\NUL1\NULES\NULFUT\NUL20161216\NUL0\NUL\NULGLOBEX\NULUSD\NULESZ6\NULES\NULES\NUL206848474\NUL0.25\NUL50\NULACTIVETIM,ADJUST,ALERT,ALGO,ALLOC,AVGCOST,BASKET,COND,CONDORDER,DAY,DEACT,DEACTDIS,DEACTEOD,GAT,GTC,GTD,GTT,HID,ICE,IOC,LIT,LMT,LTH,MIT,MKT,MTL,NGCOMB,NONALGO,OCA,PEGBENCH,SCALE,SCALERST,SNAPMID,SNAPMKT,SNAPREL,STP,STPLMT,TRAIL,TRAILLIT,TRAILLMT,TRAILMIT,WHATIF,\NULGLOBEX\NUL1\NUL11004968\NULE-mini S&P 500\NUL\NUL201612\NUL\NUL\NUL\NULCTT\NUL20160321:1700-1515,1530-1600;20160322:1700-1515,1530-1600\NUL20160321:0830-1515;20160322:0830-1515\NUL\NUL\NUL0\NUL52\NUL1\NUL1\NUL")
Just (IBResponse (ContractData {_cdReqId = 1, _cdContractDetails = IBContractDetails {_cdSummary = IBContract {_conId = 206848474, _conSymbol = "ES", _conSecType = IBFuture, _conExpiry = Just 2016-12-16, _conStrike = 0.0, _conRight = Nothing, _conMultiplier = Just 50.0, _conExchange = GLOBEX, _conCurrency = USD, _conLocalSymbol = "ESZ6", _conTradingClass = "ES", _conPrimaryExch = Other "", _conIncludeExpired = False, _conSecIdType = Nothing, _conSecId = "", _conComboLegsDescrip = "", _conComboLegs = [], _conUnderComp = Nothing}, _cdMarketName = "ES", _cdMinTick = 0.25, _cdPriceMagnifier = 1, _cdOrderTypes = "ACTIVETIM,ADJUST,ALERT,ALGO,ALLOC,AVGCOST,BASKET,COND,CONDORDER,DAY,DEACT,DEACTDIS,DEACTEOD,GAT,GTC,GTD,GTT,HID,ICE,IOC,LIT,LMT,LTH,MIT,MKT,MTL,NGCOMB,NONALGO,OCA,PEGBENCH,SCALE,SCALERST,SNAPMID,SNAPMKT,SNAPREL,STP,STPLMT,TRAIL,TRAILLIT,TRAILLMT,TRAILMIT,WHATIF,", _cdValidExchanges = [GLOBEX], _cdUnderConId = 11004968, _cdLongName = "E-mini S&P 500", _cdContractMonth = "201612", _cdIndustry = "", _cdCategory = "", _cdSubCategory = "", _cdTimeZoneId = "CTT", _cdTradingHours = "20160321:1700-1515,1530-1600;20160322:1700-1515,1530-1600", _cdLiquidHours = "20160321:0830-1515;20160322:0830-1515", _cdEvRule = "", _cdEvMultiplier = 0.0, _cdSecIds = fromList []}}))
Just (IBResponse (ContractDataEnd {_cdReqId = 1}))
Just (Log "4\NUL2\NUL-1\NUL2104\NULMarket data farm connection is OK:usfuture\NUL")
Just (IBResponse (Error {_errId = -1, _errCode = 2104, _errDesc = "Market data farm connection is OK:usfuture"}))
Just (Log "1\NUL6\NUL2\NUL9\NUL2022.50\NUL0\NUL0\NUL")
Just (IBResponse (TickPrice {_tpTickerId = 2, _tpTickType = Close, _tpPrice = 2022.5, _tpCanAutoExecute = False}))
ServiceActive
2016-03-21 20:52:57 AEDT MVC.Socket DEBUG: connectionReader stream error: threadWait: invalid argument (Bad file descriptor)
Just (IBResponse (NextValidId {_nvId = 1}))
Just (Log "4\NUL2\NUL-1\NUL2104\NULMarket data farm connection is OK:usfuture\NUL")
Just (IBResponse (Error {_errId = -1, _errCode = 2104, _errDesc = "Market data farm connection is OK:usfuture"}))
Just (Log "1\NUL6\NUL1\NUL1\NUL2025.50\NUL3\NUL1\NUL2\NUL6\NUL1\NUL0\NUL3\NUL")
Just (IBResponse (TickPrice {_tpTickerId = 1, _tpTickType = Bid, _tpPrice = 2025.5, _tpCanAutoExecute = True}))
Just (IBResponse (TickSize {_tsTickerId = 1, _tsTickType = BidSize, _tsSize = 3}))
Just (Log "1\NUL6\NUL1\NUL2\NUL2027.50\NUL4\NUL1\NUL2\NUL6\NUL1\NUL3\NUL4\NUL")
Just (IBResponse (TickPrice {_tpTickerId = 1, _tpTickType = Ask, _tpPrice = 2027.5, _tpCanAutoExecute = True}))
Just (IBResponse (TickSize {_tsTickerId = 1, _tsTickType = AskSize, _tsSize = 4}))
Just (Log "1\NUL6\NUL1\NUL9\NUL2022.50\NUL0\NUL0\NUL")
2016-03-21 20:53:08 AEDT MVC.Socket DEBUG: socketService end
2016-03-21 20:53:08 AEDT API.IB.Connection DEBUG: ibService end
2016-03-21 20:53:08 AEDT MVC.Socket DEBUG: connectionReader stream error: threadWait: invalid argument (Bad file descriptor)
ServiceTerminated
Finished
2016-03-21 20:53:08 AEDT API.IB.Connection DEBUG: withIB stop
2016-03-21 20:53:08 AEDT API.IB.Connection DEBUG: withIB error: thread killed
2016-03-21 20:53:08 AEDT MVC.Socket DEBUG: connectionReader error: thread killed
```

## Sample Output (shell)

```bash
$ stack exec shell
IB> help
commands: help, quit, con [es|gc], price [es|gc]
IB> price es
TickPrice {_tpTickerId = 1, _tpTickType = Bid, _tpPrice = 2025.5, _tpCanAutoExecute = True}
IB> price gc
TickPrice {_tpTickerId = 2, _tpTickType = Last, _tpPrice = 1251.4, _tpCanAutoExecute = False}
IB> con es
ContractData {_cdReqId = 3, _cdContractDetails = IBContractDetails {_cdSummary = IBContract {_conId = 206848474, _conSymbol = "ES", _conSecType = IBFuture, _conExpiry = Just 2016-12-16, _conStrike = 0.0, _conRight = Nothing, _conMultiplier = Just 50.0, _conExchange = GLOBEX, _conCurrency = USD, _conLocalSymbol = "ESZ6", _conTradingClass = "ES", _conPrimaryExch = Other "", _conIncludeExpired = False, _conSecIdType = Nothing, _conSecId = "", _conComboLegsDescrip = "", _conComboLegs = [], _conUnderComp = Nothing}, _cdMarketName = "ES", _cdMinTick = 0.25, _cdPriceMagnifier = 1, _cdOrderTypes = "ACTIVETIM,ADJUST,ALERT,ALGO,ALLOC,AVGCOST,BASKET,COND,CONDORDER,DAY,DEACT,DEACTDIS,DEACTEOD,GAT,GTC,GTD,GTT,HID,ICE,IOC,LIT,LMT,LTH,MIT,MKT,MTL,NGCOMB,NONALGO,OCA,PEGBENCH,SCALE,SCALERST,SNAPMID,SNAPMKT,SNAPREL,STP,STPLMT,TRAIL,TRAILLIT,TRAILLMT,TRAILMIT,WHATIF,", _cdValidExchanges = [GLOBEX], _cdUnderConId = 11004968, _cdLongName = "E-mini S&P 500", _cdContractMonth = "201612", _cdIndustry = "", _cdCategory = "", _cdSubCategory = "", _cdTimeZoneId = "CTT", _cdTradingHours = "20160321:1700-1515,1530-1600;20160322:1700-1515,1530-1600", _cdLiquidHours = "20160321:0830-1515;20160322:0830-1515", _cdEvRule = "", _cdEvMultiplier = 0.0, _cdSecIds = fromList []}}
IB> quit
$
```

## IB Installation (OS X)

### IB TWS

The IB API can be accessed via the full desktop client (TWS - Trader Workstation) or the gateway client. I have only used TWS to date but will try the gateway soon - from what I can tell it only offers a restricted subset of the native IB API (e.g. orders may not be supported) but supports the full API via FIX.

Create a folder for TWS.

    mkdir ~/IBJts

Download and run the [latest TWS installer for OS X](https://download2.interactivebrokers.com/download/TWSX_install_latest.pkg) and run it. Copy all files from the Contents/Resources/Java subfolder of the newly created Trader_WorkStation_X.app package to ~/IBJts. For example:

    cp -r /Users/<Username>/Applications/Trader_WorkStation_X.app/Contents/Resources/Java ~/IBJts

Change to the IBJts folder:

    cd ~/IBJts

Run TWS:

    java -cp jts.jar:total.jar -Xmx512M -XX:MaxPermSize=128M jclient.LoginFrame .

Create a shell file to launch TWS and save as 'ibtws':

    #!/bin/sh
    cd ~/IBjts
    java -cp jts.jar:total.jar -Xmx512M -XX:MaxPermSize=128M jclient.LoginFrame . 

Make ibtws executable

    chmod +x ibtws

### IBController

Download the [latest IBController code](https://github.com/ib-controller/ib-controller) and extract the archive in your home folder. Change to the newly created IBControllerVX-XX-X folder.

    cp sampleIBControllerStart.sh ibc
    chmod +x ibc

Edit ibc. Mine looks like this (note the commented-out username and password):

    #!/bin/bash
    TWSUSERID=<IB username>
    TWSPASSWORD=<IB password>
    IBCDIR=/Users/Chris/IBController/
    IBCINI=/Users/Chris/IBController/IBController.ini
    TWSDIR=/Users/Chris/IBJts
    TWSCP=jts.jar:total.jar
    JAVAOPTS="-Xmx512M -XX:MaxPermSize=128M" 
    pushd $TWSDIR
    java -cp  $TWSCP:$IBCDIR/IBController.jar $JAVAOPTS ibcontroller.IBController $IBCINI $TWSUSERID $TWSPASSWORD
    popd

Edit the following entries in IBController.ini.

    IbLoginId=<IB username>

    IbPassword=<IB password>

    IbDir=/Users/Chris/IBJts

### Testing

Make ibtws and ibc accessible e.g. via copying to a folder in your PATH.

Running ibtws should launch the TWS client and request your login details:

    ibtws

Running ibc should launch IB TWS and login automatically:

    ibc

### Enabling the IB API in TWS

Activate via menu / setting dialog:

Edit - Global configuration - API - Settings - Enable ActiveX and Socket Clients

