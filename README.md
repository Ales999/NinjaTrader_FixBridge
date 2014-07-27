NinjaTrader_FixBridge
=====================
Trading Platform:

NinjaTrader7 is a nice proprietary application for trading and developing your own investment strategies in C# 3.5. More than that, it lets you choose your own broker.

FIX:

The dedicated protocol for order management and price notification is FIX. This protocol is based on messages of key-value pairs, transmitted on a socket between 2 hosts (exchange, broker, end-user/software). The robustness of the protocol is based on the sequence numbers, incremented for each messages, allowing resending missed message when re-spawning after a crash. - Find quickFIXn ,clone, compile to create the quickfix.dll


Installation

Compile QuickFix.dll from quickFIXn source

Compile NinjaTrader_FixBridge.dll from source ( must include NinjaTrader.core.dll + quickfix.dll) 

Copy both dlls into your personnal NinjaTrader folder, ie into %USERPROFILE%\Documents\NinjaTrader 7\bin\Custom

Restart NinjaTrader: it will load the dll on start up.


How it works:

After installing the NinjaTrader_FixBridge module, proceed as following:
Connect to a broker " File / Connect / Your favorite broker" (or to the "Market Replay Connection")
In the "Strategies" tab, create a FixConnector strategy (if it does not appear, something went wrong during installation).
Configure the strategy:
Symbols box : add the instrument names you want to expose via FIX. Ex: CL ##-##, ES ##-##, $EURUSD
BridgeName box : name of this bridge.
ConfigFileName box : absolute path to the config file. An example here
ActivateTrace : let this to 1 in order to have verbose logs. Set to 0 if your are very confident.
You can set the name of the bridge to identify this instance in the "log" tab
Start the strategy
Verify on the "log" tab the fix server has started.
