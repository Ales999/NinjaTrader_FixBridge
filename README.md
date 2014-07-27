NinjaTrader_FixBridge
=====================

NinjaTrader7 strategy implementing a FIX server.

[wiki](https://github.com/FabienCarmagnac/NinjaTrader_FixBridge/wiki)

NinjaTrader

NinjaTrader7 is a nice proprietary application for trading and developing your own investment strategies in C# 3.5. More than that, it lets you choose your own broker.

FIX

The dedicated protocol for order management and price notification is FIX. This protocol is based on messages of key-value pairs, transmitted on a socket between 2 hosts (exchange, broker, end-user/software). The robustness of the protocol is based on the sequence numbers, incremented for each messages, allowing resending missed message when re-spawning after a crash. The c++ implementation can be found here and its c# implementation here. Sadly this version is not stable enough, so I recommend the use of this version (source code). If you dont want to build yourself the QuickFix.dll, you can directly download it from here.

How it works

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
Installation

Download QuickFix.dll from here
Download NinjaTrader_FixBridge.dll from here
Copy both dlls into your personnal NinjaTrader folder, ie into %USERPROFILE%\Documents\NinjaTrader 7\bin\Custom
Restart NinjaTrader: it will load the dll on start up.
Testing

A lots of FIX GUI exist in order to connect to the FIX bridge and send orders. For example, you can try the famous Banzai app, written in java. If you want something using the QuickFix.dll lib, you may try this one.

TODO

Implementation of the market data feed service via FIX protocol. For now, it is not clear anough how to transmit bid/ask/qty in the same message without breaking the FIX specifications.
