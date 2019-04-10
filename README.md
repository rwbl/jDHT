# b4j-library-jdht
jDHT is an open source B4J library for the digital-output relative humidity &amp; temperature sensors DHT11 &amp; DHT22 connected to a Raspberry Pi.

The library is written in B4J (requires v5.80 or higher) making use of Inline Java (requires Java 8 update 40 or higher).

[B4J](https://www.b4x.com/b4j.html) development tool for cross platform desktop, server and IoT solutions by [Anywhere Software](https://www.b4x.com).

The library

* is based upon [this](http://hirt.se/blog/?p=493) project (recommend to read the blog,  many thanks to the author).
* if a sensor value can not be read, NaN is returned.
* tested with the sensors DHT11 and DHT22 (see sample code) connected to a Raspberry Pi 3.

__Library Version__: 1.01 (Build 20170601)

## Files
* jDHT.zip contains the library and sample projects.
* jDHT.pdf manual

## Install
Copy jdht.jar, jdht.xml and dht.jar to the B4J additional libraries folder. Copy libdht.so to the dirapp folder.
When testing on the Raspberry Pi using the B4J-Bridge, ensure libdht.so is in the tempjars folder.

## Wiring
```
DHT11 = Raspberry Pi 3
5v = 5v
Data = Physical Pin #16 [BCM23]
GND = GND
```

```
DHT22 = Raspberry Pi 3
5v = 5v
Data = Physical Pin #15 [BCM22]
GND = GND
```

## Example B4J Non-UI Program
```
Sub Process_Globals          
  Private dht11 As DHT
  Private dht22 As DHT
  Private timer1 As Timer
End Sub

Sub AppStart (Args() As String)
  ' Init the sensor with sensortype and pin (BCM)
  dht11.Initialize(11, 23)
  dht22.Initialize(22, 22)
  timer1.Initialize("timer1", 2000)
  timer1.Enabled = True
  StartMessageLoop
End Sub

Sub timer1_tick
  Log($"DHT11 ${DateTime.Time(DateTime.Now)}: ${dht11.Temperature}*, ${dht11.Humidity}%"$)
  Log($"DHT22 ${DateTime.Time(DateTime.Now)}: ${dht22.Temperature}*, ${dht22.Humidity}%"$)
End Sub
```

__Output__
```
dht11 09:51:01: 19.9*, 41.7%
dht22 09:51:01: 19.9*, 41.7%
dht11 09:51:03: 18.0*, 44.6%
dht22 09:51:03: 18.0*, 44.6%
dht11 09:51:11: 18.0*, 56.4%
dht22 09:51:12: 18.0*, 56.4%
dht11 09:51:23: 18.7*, 71.7%
dht22 09:51:23: 18.7*, 71.7%
```

## Author
Robert W.B. Linn

## Licence
Copyright (C) 2017-2019  Robert W.B. Linn
This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or (at your option) any later version.
This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS for A PARTICULAR PURPOSE.  See the GNU General Public License for more details.
You should have received a copy of the GNU General Public License along with the samples.  If not, see [GNU Licenses](http://www.gnu.org/licenses/).

