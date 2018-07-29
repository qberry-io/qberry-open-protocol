# Open Qberry Protocol v1.0.0

"Qberry Open Protocol" is an open source version of the "Original Qberry Protocol" which is used for messaging in "Qberryduino" project such as [qberryduino-gateway-one](https://github.com/denizkanmaz/qberryduino-gateway-one).

## The parser libraries
[qberry-open-protocol-parser-dotnet](https://github.com/denizkanmaz/qberry-open-protocol-parser-dotnet)

## Symbols

`$` is used to mark beginning or end of the message.
`|` is used to splits the `keyvals`.

Notice: Count of the pipes must be odd number.

Example:
`$|11|hello|12|90999888000000007|13|myScreT|14|tbdOne|15|1.0.0|$`

## Keyvals (Keys and Values)
Each value is spotted by a key. This keys always come just before the value.

Example: Let's try to parse this message:
`$|11|hello|12|90999888000000007|13|myScrT|14|tbdOne|15|1.0.0|$`

`key|value`
`11|hello // The type of this message is 'hello'`
`12|90999888000000007 // The identity of this device is 90999888000000007`
`13|myScrT // The secret key is 'myScrT'`
`14|tbdOne // The model of this device is 'myScrT'`
`15|1.0.0 // The version of the protocol which is used in this device is '1.0.0'`

## Keys

#### Header
11: Type of message (hello, curr, bye)
12: Device identity
13: Secret Key
14: Model of the device
15: Version of the protocol (Which is used in the device)

### Body (Electricity & Battery Status)
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

## Known issues and missing important functions
After the development, there are somesome missing functions showed themselves. They will be solved with the incoming versions.

* There should be an option to compress the message.

## Versioning

Used [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/denizkanmaz/qberryduino-gateway-one/tags). 

## Authors

* **[Deniz Kanmaz](https://github.com/denizkanmaz)** - *Initial work* - [qberry.io](https://qberry.io)

## License

This project is licensed under the GNU General Public License v3 - see the [LICENSE.md](LICENSE.md) file for details.

NOTICE: This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
