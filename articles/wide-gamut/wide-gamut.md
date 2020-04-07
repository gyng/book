# Wide gamut setup

## Test images

* https://webkit.org/blog-files/color-gamut/
* http://www.color.org/version4html.xalter
* https://www.netflix.com/us/title/81017017

## Colour calibration

Basic colorimeters

* [X-Rite i1Display Pro](https://www.amazon.com/dp/B0055MBQOW)
* [Datacolor Spyder5EXPRESS](https://www.amazon.com/dp/B00UBSL2TO)

Software

* [DisplayCAL](https://displaycal.net/)

## Windows

As of April 2020, Windows 10 is still poorly colour managed.

* Set up ICC profiles as needed (Control Panel > Colour Management)
* Turn on HD colour settings as needed (Display Settings > Windows HD Color settings)

### 10-bit support

#### Nvidia/Windows

NVIDIA Control Panel > Display > Change resolution > Use NVIDIA color settings

## Mac OS

* https://support.apple.com/en-us/guide/mac-help/mchlf3ddc60d/mac

## Application settings 

Mostly for Windows, since colour management on Mac OS has 

### Firefox

As of April 2020, Firefox does not manage colour fully. The first bug was opened 12 years ago!

* [455077 - Enable full color_management by default (i.e. set gfx.color_management.mode = 1)](https://bugzilla.mozilla.org/show_bug.cgi?id=455077)
* [1615404 - Images copied to clipboard should not color managed directly](https://bugzilla.mozilla.org/show_bug.cgi?id=1615404)
* [ICC color correction in Firefox](https://developer.mozilla.org/en-US/docs/Mozilla/Firefox/Releases/3.5/ICC_color_correction_in_Firefox)

You can force better colour management in `about:config`.

Set the following

* `gfx.color_management.mode` to `1` to force all content with no profiles to sRGB. This fixes oversaturation of web content, most noticably in reds.
* `gfx.color_management.enablev4` to `true` to force ICCv4 support

### WebKit/Chrome

Should behave well by default.

### Photoshop

Should behave well by default.

### MPC-HC

* [ICC color management in Media Player Classic Home Cinema](https://voxelium.wordpress.com/2010/09/20/icc-color-management-in-media-player-classic-home-cinema/)
* Right-click video > Renderer Settings > Colour Management > Enable

### VLC (all platforms)

Not colour managed. Switch to a different player.

### IrfanView

Should be colour managed, but there is a checkbox in Options > Properties/Settings > Zoom/Color management

## Further reading

* [Why Your HDR Monitor is (Probably) Not HDR at All – and Why DisplayHDR 400 Needs to Go](https://www.tftcentral.co.uk/blog/why-your-hdr-monitor-is-probably-not-hdr-at-all-and-why-displayhdr-400-needs-to-go/)
* [Web browser color management guide](https://cameratico.com/guides/web-browser-color-management-guide/)

