
To Do List
==========

### Documentation

* README: review IB Controller username/password instructions, review latest IB Controller release, update for new scripts (in scripts folder)
* Haddocks markup

### Defects

* Pico issue (see email): test on GHC 7.8.x - should be resolved
* Thread blocked indefinitely in an STM transaction: see [pipes-concurrency issue](https://github.com/Gabriel439/Haskell-Pipes-Concurrency-Library/issues/29)

### New features

* Test IB Gateway app
* IB Controller launcher (TWS and Gateway).
* Add a connection timeout (secs) config setting?
* Simple interface (connection object)?
* Remaining IB requests and responses (summarise here from list in Enum.hs)
* Contract database, automated update
* SSL connection to IB TWS

### Cabal file

* Standardise package dependency format to best practice
* Remove unnecessary dependencies in sample app executable sections
* Add stack support, standardise on a stackage version

### Design

* Refactor Edge to ListT (use state for partial parse)
* Async/exception handling
* Config read only (vs in 'mutable' state at present)?
* BASE currency (in AccountValue msg) solution

### Test suite 

* Unit tests
* Property tests
* Benchmarks

### Sample apps

* Requests-Simple: rename, add all requests
* Requests-Service: rename, change to be a basic algo trader (e.g. moving average crossover), separate project?, extend IB library with a set of helpers for requests (as in Monadic.hs) to be used with event handler approach
* Shell: IB shell (build into API?) - convert to IB monad, add full request support, single command invocation
* Capture (new): historical/streaming market data to file/db

### Connection

* Review all error handling / stop / cleanup logic to ensure graceful termination of services (including upstream)
* Add remaining conditions to ensure state machine is robust (e.g. can't process start unless pending) and invalid commands/condtions are logged
* Check client server version <= server version
* Error handler for error responses from IB (see IB API docs for error codes)
* Error response messages - see EClientSocket.java e.g. not connected, cannot send (also cannot create which currently only logs a message)

### Monadic interface

* Reduce duplication in requests code (getting sv, rid, etc.)
* Async function to fork an IB thread sharing the req/resp mailboxes and updating the same state?
* More IB instances (e.g. MonadCatch)

### Builder

* Contract builders: stock, forex, option
* Order builders: stop/limit/stoplimit orders, attached orders (stop loss, profit target, oco stop and profit target)

### Data 

* Consider using Text (github issue #1)
* IBOrder: into multiple data types
* IBOrder: maybe's for bools
* IBOrder: decomposition may allow a single maybe for related fields
* Consistent use of IB prefix for data type names (e.g. IBRequest and IBResponse constructors and fields)
* Use Data.Default for base instances (vs newIBContract, etc.)

### Enum

* Consider reducing duplication across encode and show (e.g. with a common mapping data structure)

### Requests

* Investigate cancel positions request - what does it do (e.g. close positions, cancel request positions msg, etc.)? 
* Use typing to prevent some of the error conditions (e.g. bar size)
* Lazy vs strict bytestring (github issue #2)
* Remove req historical data option to specify date format - just use one of the two options internally

### Parsing

* FromIB class for parsing?
* Review fields for possible signed / blank / default parsing requirement
* IBContract: complete refactoring to use field level parsers
* TickPrice: parse also generates a TickSize but latter seems to also stream separately - confirm/remove duplication? Have commented out TickSize generation from TickPrice parser.
* Add error message to fail "" (and empty?) statements

### Related package: mvc-service

See TODO.md file in the repo

