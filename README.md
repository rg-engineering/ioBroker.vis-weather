![Logo](admin/vis-weather.png)
ioBroker.vis-weather
============

[![NPM version](https://img.shields.io/npm/v/iobroker.vis-weather.svg)](https://www.npmjs.com/package/iobroker.vis-weather)
[![Downloads](https://img.shields.io/npm/dm/iobroker.vis-weather.svg)](https://www.npmjs.com/package/iobroker.vis-weather)

[![NPM](https://nodei.co/npm/iobroker.vis-weather.png?downloads=true)](https://nodei.co/npm/iobroker.vis-weather/)

This vis-widget shows weather forecast data from DasWetter.com or weatherunderground
You need DasWetter-Adpater or weatherunderground-Adapter running as well...

    In weatherunderground you need forecast of next 24 hours enabled.
    In DasWetter.com you need 5 days-forecast enabled.


## Notes / wiki
### Define Forecast hours
By default the forecast diagram shows 40 hours (DasWetter) or 36 hours (wunderground). If you prefer to only show e.g. 10 hours forecast, simply delete the unnecessary OIDs under oid_groups in vis-edit. 



## Changelog

#### 1.1.1
* (Ren�) Y axis with units

#### 1.1.0
* (Ren�) logs auskommentiert
* (Ren�) Berechnung min / max f�r Temperaturgraph optimiert
* (Ren�) Y-Achse automatisch ausblenden, wenn Graph nicht dargestellt wird
* (gitbock) konfigurierbare Y-Achsen je Graph (anzeigen/nicht anzeigen)
* (gitbock) Y-Achsen Beschriftung in der Farbe des Graphen
* (gitbock) Max.-/Min Werte f�r Temperatur Y-Achse
* (gitbock) konfigurierbares Datumsformat f�r X-Achse


#### 1.0.0
* (Ren�) first stable version

#### 0.0.7
* (Ren�) bug fix for android app > 1.0.6
* (Ren�) color adjustment for ticks and tick lable (from sbfspot)

#### 0.0.6
* (Ren�) css removed

#### 0.0.5
* (Ren�) number of labels on X axis adjustable

#### 0.0.4
* (Ren�) bug fixes

#### 0.0.3
* (Ren�) support of DasWetter.com and weatherunderground

#### 0.0.2
* (Ren�) bug fixes
	- in live mode nothing was shown

#### 0.0.1
* (Ren�) initial release

## License
Copyright (C) <2017>  <info@rg-engineering.eu>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.





