# Time Formatter in Dart
This is a FORK of tpscrpt/time_formatter which displays the Strings in german language and Formatting.


This library takes UNIX (milliseconds) timestamps and converts them to pretty, human-readable time formats.

## Using
Add the package to your pubspec.yaml
```yaml
dependencies:
  time_formatter: ^1.0.0
```
Import the library in a .dart file
```dart
import 'package:time_formatter/time_formatter.dart';
```
Format an arbitrary UNIX timestamp (int type, milliseconds since epoch) with formatTime()
```
String formatted = formatTime(1548979724964)
```

## Format
Here's a mini truth table for the format of the value returned by the function:
 - < 1 second         : "Gerade eben"
 - < 60 seconds       : "vor X Sekunden" (2-59)
 - < 2 minutes        : "vor 1 Minute" 
 - < 60 minutes       : "vor X Minuten" (2-59)
 - < 2 hours          : "vor 1 Stunde"
 - < 24 hours         : "vor X Stunden" (2-23)
 - < 2 days           : "vor 1 Tag"
 - < 7 days           : "vor X Tagen" (2-6)
 - < 2 weeks          : "vor 1 Woche"
 - < 28 days          : "vor X Wochen" (2-3)
 - < 30.44 * 1.5 days : "vor 1 Monat"
 - < 365 - 15.22 days : "vor X Monaten" (2-12)
 - < 730 days         : "vor 1 Jahr"
 - Rest               : "vor X Jahre"

I decided to use truncate() for everything except months, as they can yield scenarios where something was stamped 59 days ago, but it still returns "1 month" (for example). Monthly timestamps are rounded to the nearest month.

## Contributing
If you spot a bug or would like to provide additional functionality, you are more than welcome to submit an issue or pull request.

## License
GPL 2.0, as per recommendation.
