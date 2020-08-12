# Blip Chat Flutter App example
> An example app built with Flutter using the BLiP Chat

Meet [BLiP](http://blip.ai)!

## How to run

#### Install all the dependencies:

```sh
flutter pub get
```

#### Execute the project:

Press F5 on VSCode, and select (`Dart/Flutter`)


## Built With
This project was bootstrapped with [Flutter](https://flutter.dev/).

## Using BLiP Chat with Flutter

Install the library (`flutter_webview_plugin`) and use it to render a webview with the BLiP Chat URL.

```dart
final Set<JavascriptChannel> jsChannels = [
  JavascriptChannel(
      name: 'Print',
      onMessageReceived: (JavascriptMessage message) {
        print(message.message);
      }),
].toSet();

return WebviewScaffold(
    url: "https://chat.blip.ai/?appKey=YOUR-APP-KEY",
    javascriptChannels: jsChannels,
    mediaPlaybackRequiresUserGesture: false,
    appBar: AppBar(
        title: const Text('BLiP Chat'),
    ),
)
```

It is ecessary to add on PList:

```xml
<key>NSAppTransportSecurity</key>
<dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
    <key>NSAllowsArbitraryLoadsInWebContent</key>
    <true/>
</dict>
```

## Troubleshotting

* Why don't we use the library (`webview_flutter`)?
  * With static HTML: The chat loads but the bot breaks on loading screen.
  * With BLiP Chat URL: The chat and bot loads, but it is not possible to type the message.
  
* Using a static HTML: The bot breaks on loading screen.


## Contributing

1. Fork it (<https://github.com/takenet/blip-chat-flutter-example>)
2. Create your feature branch (`git checkout -b feature/fooBar`)
3. Commit your changes (`git commit -am 'Add some fooBar'`)
4. Push to the branch (`git push origin feature/fooBar`)
5. Create a new Pull Request
