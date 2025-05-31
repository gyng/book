# Mavica tips

## Converting .411 files

These are thumbnail files. I've had luck using [XnConvert](https://www.xnview.com/en/xnconvert/) to do the conversion.

## Field vs frame

Field: slightly worse image, no interlacing artefacts

Frame: slightly better image, interlacing artefacts (moving things get shredded)

## Battery is stuck or won't go into the battery bay

Put a ribbon or floss around the battery first so you can pull it out later. If it's already stuck inside, take glue and stick a ribbon on it, then pull it out.

The ribbon is really annoying so I filed the batteries down to size.

## Checking and fixing floppy disks

On Windows

```
format a: /u
```

Use `/u` for unconditional format. After a couple of minutes

```
Insert new disk for drive A:
and press ENTER when ready...
The type of the file system is FAT.
Verifying 1.44M
Initializing the File Allocation Table (FAT)...
Volume label (11 characters, ENTER for none)?
Format complete.
       1.4 MB total disk space.
      274,432 bytes in bad sectors.
       1.1 MB are available.

          512 bytes in each allocation unit.
        2,311 allocation units available on disk.

           12 bits in each FAT entry.

Volume Serial Number is 0A42-5677
```

274432B of bad sectors is really bad!

Other things to try

- erasing with ImageDisk first
- manually resetting/wiping floppy with a strong magnet (eg, dead HDD magnet)
- use a different floppy disk drive
- take photos multiple times

See: https://www.vogons.org/viewtopic.php?t=84771

## Applying EXIF

```
exiftool \
  "-datetimeoriginal<filemodifydate" \
  -make="SONY" \
  -model="MAVICA MVC-FD7" \
  -EXIF:OffsetTime*=+8:00 \
  .
```

### If you have a GPS track

```
exiftool -geotag track.gpx \
  . \
  -api GeoMaxIntSecs=1800 \
  '-geotime<${DateTimeOriginal}+08:00'
```

[read more](https://gyng.github.io/book/articles/geotag/geotag.html)

### Combined

```
exiftool \
  "-datetimeoriginal<filemodifydate" \
  -make="SONY" \
  -model="MAVICA MVC-FD7" \
  -EXIF:OffsetTime*=+8:00 \
  . \
&& exiftool \
  -geotag track.gpx \
  . \
  -api GeoMaxIntSecs=1800 \
  '-geotime<${DateTimeOriginal}+08:00'
```

## Samples

![MVC-022F](https://github.com/user-attachments/assets/b4e6304e-563d-4751-bba8-c20fb5c55cae)
![MVC-029F](https://github.com/user-attachments/assets/dec5d9a3-d129-4916-9268-97620106617c)
![MVC-012F](https://github.com/user-attachments/assets/ba2bd969-a23d-4835-b649-746281eb5967)
![MVC-015F](https://github.com/user-attachments/assets/76c5c6e6-3ddb-4374-b6a6-4dcf41ff6a26)
![MVC-009F](https://github.com/user-attachments/assets/ce24f5a9-d74b-43f2-89e5-dc47f64854e3)
![MVC-021F](https://github.com/user-attachments/assets/50b9c9f9-8b46-4153-8f4e-560003cdf83f)

