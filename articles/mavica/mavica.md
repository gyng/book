# Mavica tips

## Converting .411 files

These are thumbnail files

## Field vs frame

Field: slightly worse image, no interlacing artefacts
Frame: slightly better image, interlacing artefacts (moving things get shredded)

## Battery stuck

Put a ribbon or floss around the battery first

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

