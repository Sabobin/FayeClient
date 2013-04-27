FayeClient - iOS & Mac OS X
==========

This project is a copy of the Library made by pcrawfor there: <https://github.com/pcrawfor/FayeObjC>


Installation
---
1. Setup `Cocoapods` for your project <http://cocoapods.org/>
2. `Download` the last version of FayeClient
3. The downloaded folder contains an Example folder which is an example of use of the FayeClient, and the Library folder with the sources of the library. Copy the `Library` folder on your project.
4. Compile your project, your should be ready to go!
 
Usage
---
* Install the library
* Import the library in the file where you need it: 

```
#import #import "FayeClient.h"
```
* Create a property for the FayeClient object

```
@property (nonatomic, strong) FayeClient *client;
```
* Initialize the client with the URL of the server and the channel you want to be subscribed to:

```
_client = [[FayeClient alloc] initWithURLString:@"ws://localhost:9292/hub" channel:@"/room1"];
```
* Open the connection with the server:

```
[_client connectToServer]
```
* Send a message:

```
[_client sendMessage:@{@"jayztemplier" : @"Hello World!"}];
```

Delegate
---
You can also add a delegate to the Faye Client in order to have some feebacks about what happened:

```
  @protocol SRWebSocketDelegate <NSObject>

  - (void)webSocket:(SRWebSocket *)webSocket didReceiveMessage:(id)message;

  @optional

  - (void)webSocketDidOpen:(SRWebSocket *)webSocket;
  - (void)webSocket:(SRWebSocket *)webSocket didFailWithError:(NSError *)error;
  - (void)webSocket:(SRWebSocket *)webSocket didCloseWithCode:(NSInteger)code reason:(NSString *)reason wasClean:(BOOL)wasClean;

  @end
```

Faye Server
---
If you can to run a Faye server to test the client, you can find all the information you need there: <http://faye.jcoglan.com/>
You can also run the `server.rb` file under the `Server` directory:

```
gem install faye
ruby ./server.rb
```