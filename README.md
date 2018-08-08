# Open Qberry Messaging Protocol v1.0.0

"Qberry Open Protocol" is a messaging protocol between IOT devices and TCP Socket Servers which is used for messaging in "Qberryduino" project such as [qberryduino-gateway-one](https://github.com/denizkanmaz/qberryduino-gateway-one).

## Library for parsing
[qberry-open-protocol-parser-dotnet](https://github.com/denizkanmaz/qberry-open-protocol-parser-dotnet)

## Symbols

`$` is used to mark the beginning and the end of message.
`|` is used for splitting the `keyvals`.

Notice: Count of the pipes must be odd number.

Example:
`$|11|hello|12|90999888000000007|13|myScreT|14|tbdOne|15|1.0.0|$`

## Keyvals (Keys and Values)
Each value is spotted by a key. This keys always come just before the value.

Example: Let's try to parse this message:
`$|11|HOLA|12|90111122223333444|13|WMXQFV|14|B23a56|15|ONE|16|1.0.0|$`

`key|value`

`11|HOLA // The type of this message is "HOLA"`

`12|90111122223333444 // The identity of this device is "90111122223333444"`

`13|WMXQFV // The connection Id is "WMXQFV"`

`14|B23a56 // The secret key of this device is "B23a56"`

`15|ONE // The model of this device is "Qberryduino One"`

`16|1.0.0 // The version of the protocol which is used in this device is "1.0.0"`

## Keys

#### Header
11: Message Type (HOLA, GNSS, BATT)
12: Device Identity
13: Connection Id
14: Secret Key
15: Device Model
16: Protocol Version

### Body (Battery Status)
111: Charge Status (0: not charging, 1: charging, 2: Charging has finished)
112: Battery Connection Level (%)
113: Battery Voltage (mV)

### Body (Informations of Global Navigation Satellite System)
211: Fix status
212: Latitude
213: Longitude
214: MSL Altitude
215: Speed Over Ground
216: Course Over Ground
217: Fix Mode
218: GNSS Satellites Used
219: GLONASS Satellites Used

## Samples
`$|11|HOLA|12|90111122223333444|13|WMXQFV|14|B23a56|15|ONE|16|1.0.0|$`

`$|11|BATT|12|90111122223333444|13|WMXQFV|111|1|112|33|113|3664|$`

`$|11|GNSS|12|90111122223333444|13|WMXQFV|211|1|212|41.042820|213|28.689460|214|108.600|215|0.43|216|344.6|217|1|218|5|219|0|$`

## Known issues and missing important functions
After the development, there are some missing functions showed themselves. They will be solved with the incoming versions.

* There should be an option to compress the message.

## Versioning

Used [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/denizkanmaz/qberryduino-gateway-one/tags). 

## Authors

* **[Deniz Kanmaz](https://github.com/denizkanmaz)** - *Initial work* - [qberry.io](https://qberry.io)

## License

This project is licensed under the GNU General Public License v3 - see the [LICENSE.md](LICENSE.md) file for details.

NOTICE: This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
