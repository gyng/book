# Guide to geotagging photos with Google location history and exiftool

If you have a camera without GPS you can use your Android phone as a budget GPS tracker and tag your photos afterwards.

To make things easy, do the following

1. Leave location tracking on your Android phone active
2. Set your camera's clock to UTC
3. Do a Google Takeout of your location data at the end of your trip

[exiftool](https://www.sno.phy.queensu.ca/~phil/exiftool/) is used to fix timezones and add geotag information.

## Grab your location history

You have two options here:

### Google Takeout

1. Go to [Google Takeout](https://takeout.google.com/settings/takeout)
2. Select just your location history<br /><img src="https://github.com/gyng/book/assets/370496/54c47abe-0217-4a6d-9384-09bf27c64951" width="440px" />
3. Click "Next step, "Export", and wait for the scheduled export to run. This usually takes a day or two.
4. Download and uncompress your takeout somewhere
5. Convert `Records.json` into KML using [rickprice/location-history-json-converter](https://github.com/rickprice/location-history-json-converter)
   ```bash
   $ cd takeout
   # if an error with `ModuleNotFoundError: No module named 'dateutil'` shows up
   $ pip3 install python-dateutil
   $ wget https://github.com/rickprice/location-history-json-converter/raw/master/location_history_json_converter.py
   $ python3 location_history_json_converter.py Records.json Records.kml
   ```
6. Put the converted KML somewhere (I put it alongside the photos to be edited)

### Manual download from browser

If you can't wait for Google Takeout or if the export is bugged and not running, you can manually obtain location data (split by day) from the browser

```js
function makeUrlForDate(year, month, day) {
  // month is 0-indexed ie, Jan = 0
  // Google only returns one day's worth of data even if more is requested
  return `https://www.google.com/maps/timeline/kml?authuser=0&pb=!1m8!1m3!1i${year}!2i${month}!3i${day}!2m3!1i${year}!2i${month}!3i${day}`;
}
```

Some additional automation: https://gist.github.com/gyng/e0f7eac4445793ef3b4d59ca0b0fa6b4

#### Some tooling for dealing with KML (not a sign of endorsement)

- https://www.gpsbabel.org/
- https://kmlmerger.com/

## Geotag

Because all my photos are taken in UTC I run the following command to tag my photos

```sh
exiftool -geotag Records.kml '-geotime<${DateTimeOriginal}+00:00' . -api GeoMaxIntSecs=1800
```

The location history obtained from Google is all in UTC. That matches my camera clock so there's no need to calculate and apply timezone offsets. Super convenient when photos span different timezones.

If, somehow, the photos are in local time then change the timezone offset in that command (eg, for California, which is -7 UTC)

```sh
exiftool -geotag Records.kml '-geotime<${DateTimeOriginal}-07:00' . -api GeoMaxIntSecs=1800
```

`-api GeoMaxIntSecs=1800` sets the interpolation to 1800 seconds, or 30 minutes.

Check the EXIF, and once satisfied, remove the originals. Google shows me the location if I [search for `34.6098346210444N, 135.027243317231E`](https://www.google.com/search?q=34.6098346210444N%2C+135.027243317231E).

```sh
$ exiftool -filename -gpslatitude -gpslongitude -n .\DSCF0244.RAF
File Name                       : DSCF0244.RAF
GPS Latitude                    : 34.6098346210444
GPS Longitude                   : 135.027243317231

$ rm *_original
$ rm Records.json Records.kml location_history_json_converter.py
```

## Optional: Timestamps

The EXIF standard does not specify a timezone field and so most people set the camera's clock to the local time as needed. This is a giant PITA due to forgetfulness and timezones (and DST!), so it's easier to leave the camera's clock set to UTC and adjust the files on a desktop instead.

You can leave your timestamps in UTC. It seems like Google Photos is smart enough to autoconvert geotagged photos to the correct timezone: photos in UTC uploaded to Google Photos seem to have the correct timezone applied!

What's really useful when taking this approach is to take at least one picture of a clock, or of road signage to make it easy to verify geotags or timestamps later on.

For photos taken in New York in July (UTC-4), I run this command while in a directory with all the photos I want to edit to fix the timezones

```
exiftool "-DateTimeOriginal-=0:0:0 4:0:0" *
```

This shifts the `DateTimeOriginal` field by -4 hours.

For photos taken in Singapore (UTC+8), the following command shifts the timestamp 8 hours forward instead

```
exiftool "-DateTimeOriginal+=0:0:0 8:0:0" *
```

Note the `+=` and `-=` to shift times around.

> |                  |                       |
> | ---------------- | --------------------- |
> | DateTimeOriginal | `15/06/2018 00:05:12` |

Once that's done, do a quick check of the EXIF, and then delete the originals once satisfied

```
rm *_original
```

## Lightroom, GPicSync

I used to use Lightroom and GPicSync, but never could get them to work without spending an entire afternoon encountering weird bugs.

## TL;DR

1. [Install exiftool](https://www.sno.phy.queensu.ca/~phil/exiftool/)
2. Download "Location History" in KML from [Google Takeout](https://takeout.google.com/settings/takeout)
3. `wget https://github.com/rickprice/location-history-json-converter/raw/master/location_history_json_converter.py`
4. `python3 location_history_json_converter.py Records.json Records.kml`
5. `exiftool -geotag Records.kml '-geotime<${DateTimeOriginal}+00:00' . -api GeoMaxIntSecs=108000`
6. Optional timezone fix: `exiftool "-DateTimeOriginal+=0:0:0 8:0:0" *`
7. `rm *_original Records.json Records.kml location_history_json_converter.py`
