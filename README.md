# Open Qberry Messaging Protocol v1.1.0

"Qberry Open Protocol" is a messaging protocol between IOT devices and TCP Socket Servers which is used for messaging in "Qberryduino" project such as [qberryduino-gateway-one](https://github.com/denizkanmaz/qberryduino-gateway-one).

## Library for parsing
[qberry-open-protocol-parser-dotnet](https://github.com/denizkanmaz/qberry-open-protocol-parser-dotnet) is the official parsing library.

## Symbols

`$` is used to mark the beginning and the end of messages.

`|` is used to split the `keyvals`.

Example:
`$|11|HOLA|12|90111122223333444|13|WMXQFV|14|B23a56|15|ONE|16|1.0.0|$`

## Keyvals (Keys and Values)
Each value is presented by a `key`. These keys always come just before the `value`.

Example: Let's try to parse this message:
`$|11|HOLA|12|90111122223333444|13|WMXQFV|14|B23a56|15|ONE|16|1.0.0|$`

`{KEY}|{VALUE}`

`11|HOLA // The type of this message is "HOLA"`

`12|90111122223333444 // The identity of this device is "90111122223333444"`

`13|WMXQFV // The connection Id is "WMXQFV"`

`14|B23a56 // The secret key of this device is "B23a56"`

`15|ONE // The model of this device is "Qberryduino One"`

`16|1.0.0 // The version of the protocol which is used in this device is "1.0.0"`


## Message Types
There are three types of message.

### HOLA
"HOLA" is a message to used for introducing the device to the TCP Socket Server.

Sample:
`$|11|HOLA|12|90111122223333444|13|WMXQFV|14|B23a56|15|ONE|16|1.0.0|$`

### BATT
"BATT" is a message to used to inform the current status of battery.

Sample:
`$|11|BATT|12|90111122223333444|13|WMXQFV|111|1|112|33|113|3664|$`

### GNSS
"GNSS" is a message to used to inform the current status of location.

Sample:
`$|11|GNSS|12|90111122223333444|13|WMXQFV|211|1|212|39.922790|213|32.838507|214|108.600|215|0.43|216|344.6|217|1|218|5|219|0|$`

### TEHU
"TEHU" is a message to used to inform the current status of temperature and humidity.

Sample:
`$|11|TEHU|12|90111122223333444|13|WMXQFV|17|123456789|311|22.20|312|43.80|$`

### CNBS
"CNBS" is a message to used to inform can message.

Sample:
`$|11|CNBS|12|90111122223333444|13|WMXQFV|311|1|412|extid|413|0x18FE8100|414|8|415|0x00;0x7E;0x00;0x00;0x00;0x00;0x00;0x00|$`

## Keys and their descriptions

### Header
| Key | Description |
|--|--|
| 11 | Message Type |
| 12 | Device Id |
| 13 | Connection Id |
| 17 | Child (Endpoint) Id |

### Body (HOLA)
| Key | Description |
|--|--|
| 14 | Secret Key |
| 15 | Device Model |
| 16 | Protocol Version |

### Body (BATT)
| Key | Description |
|--|--|
| 111 | Charge Status (0: not charging, 1: charging, 2: Charging has finished) |
| 112 | Battery Connection Level (%) |
| 113 | Battery Voltage (mV) |

### Body (GNSS)
| Key | Description |
|--|--|
| 211 | Fix status |
| 212 | Latitude |
| 213 | Longitude |
| 214 | MSL Altitude |
| 215 | Speed Over Ground |
| 216 | Course Over Ground |
| 217 | Fix Mode |
| 218 | GNSS Satellites Used |
| 219 | GLONASS Satellites Used |

### Body (TEHU)
| Key | Description | Data Type |
|--|--|--|
| 311 | Temperature |number|
| 312 | Humidity |number|

### Body (CNBS)
| Key | Description |
|--|--|
| 411 | CAN Device Number |
| 412 | Id Type |
| 413 | rxId |
| 414 | Data length |
| 415 | Data |

## Known issues and missing important functions
After the development, there are some missing functions showed themselves. They will be solved with the incoming versions.

* There should be an option to compress the message.

## Versioning

Used [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/denizkanmaz/qberry-open-protocol/tags). 

## Authors

* **[Deniz Kanmaz (denizkanmaz@gmail.com)](https://github.com/denizkanmaz)** - *Initial work* - [qberry.io](https://qberry.io)

## License

This project is licensed under the GNU General Public License v3 - see the [LICENSE.md](LICENSE.md) file for details.

NOTICE: This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
