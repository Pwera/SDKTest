# SDKTest

A simple mechanism to test the AppDynamics C++ SDK.

Use this mechanism to run a basic test of your C++ SDK credentials to validate that you can successfully create BTs from within the application.

The test will register the App/Tier/Node, create a Business Transaction, and make numerous appd_bt_begin()/appd_bt_end() paired calls, sleeping a 
configurable number of seconds between each cycle.  You can also configure the number of threads that simultaneously perform this operation, and 
the number of cycles each thread performs.  

Review the Makefile, uncommenting and/or assigning those fields that are required.  If you set a parameter, and that parameter has an accompanying
value that requires a mandatory setting, you'll need to replace the "dummy" setting (beginning with "ERROR_...") with the appropriate information.
At a minimum you will need to set the Controller Host/Port, and the AccessKey.

The following is the list of possible paramters.  Uncomment any that are appropriate, and set their value accordingly:

SDKTEST_CONTROLLER_HOST_NAME        = --ControllerHost ERROR_CONTROLLER_HOST_NOT_SET
SDKTEST_CONTROLLER_PORT_NUMBER      = --ControllerPort 0
#SDKTEST_CONTROLLER_USE_SSL          = --UseSSL
SDKTEST_CONTROLLER_ACCESS_KEY       = --AccessKey ERROR_ACCESS_KEY_NOT_SET
#SDKTEST_CONTROLLER_ACCOUNT_NAME     = --Account ERROR_ACCOUONT_NAME_NOT_SET

SDKTEST_CONTROLLER_APPLICATION      = --Application SDKTest1
SDKTEST_CONTROLLER_TIER_NAME        = --TierName SDKTier1
SDKTEST_CONTROLLER_NODE_NAME        = --NodeName SDKNode1

#SDKTEST_USE_HTTP_PROXY              = --UseHTTPProxy
#SDKTEST_HTTP_PROXY_HOST             = --HTTPProxyHost ERROR_HTTP_PROXY_HOST_NOT_SET
#SDKTEST_HTTP_PROXY_PORT             = --HTTPProxyPort 0
#SDKTEST_HTTP_PROXY_USER             = --HTTPProxyUser ERROR_HTTP_PROXY_USER_NOT_SET
#SDKTEST_HTTP_PROXY_PSWD             = --HTTPProxyPswd ERROR_HTTP_PROXY_PSWD_NOT_SET
#SDKTEST_HTTP_PROXY_FILE             = --HTTPProxyFile ERROR_HTTP_PROXY_FILE_NOT_SET

SDKTEST_RUNTIME_THREADS             = --Threads 1
SDKTEST_RUNTIME_CYCLES              = --Cycles 10
#SDKTEST_RUNTIME_NO_SDK              = --NoSDK

SDKTEST_RUNTIME_INIT_WAIT           = --InitWait 60000
SDKTEST_RUNTIME_BT_PAUSE            = --PauseBeforeBTBegin 1
SDKTEST_RUNTIME_TERM_PAUSE          = --PauseBeforeTerm 65

#SDKTEST_USER_CERT_FILE              = --UseCertFile
#SDKTEST_CERT_FILE                   = --CertFile ERROR_CERT_FILE_NOT_SET
#SDKTEST_CERT_DIR                    = --CertDir ERROR_CERT_DIR_NOT_SET

To run the SDKTest application via the makefile, use the "test" target (i.e. make test).   To see what the parameter values are set to within
the makefile, use the "params" target.  The "noop" parameter will run the test without making any actual SDK calls.


---EOF---
