# device-modernizr

[Modernizr]: https://modernizr.com/
[mobile-detect.js]: http://hgoebl.github.io/mobile-detect.js/
[device.js]: https://github.com/matthewhudson/device.js

## Description

This package contains of a javascript object `DeviceModernizr`, and a css-file `device-modernizr.css` with classes to hide or show elements for different screen dimensions, orientations (portrait/landscape), devices, and print.

Using [Modernizr.addTest()](https://modernizr.com/docs#modernizr-addtest) to add different classes. 

[Modernizr] must be included.

Using [mobile-detect.js] to detect the name of the device etc.
 
Using [device.js] to detect operating system, orientation and type, but with the exception that the term *'mobile'* is used for *all* mobile devices (phones and tablets). Instead the term *phone* is used for mobile phones.




## Installation
### bower
    bower install https://github.com/FCOO/device-modernizr.git --save

## Demo
http://FCOO.github.io/device-modernizr/demo/ 

## Usage

### DeviceModernizr-object (device-modernizr.js)
Collects a number of difference values regarding the device and screen using [Modernizr] and [mobile-detect.js]

(Try to) calculate a `scale` (percent) that is the scaling needed for `<button>` and other html-elements to be displayed in the same physics size as on a 20'' desttop screen with a resolution of 1366x768 pixel. Can be changed by setting the `options.referenceScreen`  

```var myDeviceModernizr = new DeviceModernizr( options );```

#### Default options
	{
	  referenceScreen: { 
	    width		: 1366,
		height		: 768,
		diagonal_inc: 20
		}
	}


#### Properties
<table>
<tr>
  <th>Id</th>
  <th>Description</th>
</tr>
<tr>
<!--  
  <td><code>screen_width</code></td><td><td></td></tr>
  <td><code>screen_height</code></td><td></td></tr>
  <td><code>client_width</code></td><td></td></tr>
  <td><code>client_width</code></td><td></td></tr>
  <td><code>screen_width_em</code></td><td></td></tr>
  <td><code>screen_height_em</code></td><td></td></tr>
  <td><code>dpi</code></td><td>dots pro inc</td></tr>
  <td><code>dpr</code></td><td>device pixel ratio</td></tr>
-->
<td><code>scale</code></td><td>The scale is best guest for a scale (eq. <code>html.style.font-size = myDeviceModernizr.scale</code>) of the screen to have elements the same size as on the reference screen</td></tr>

<td><code>isDesktop</code></td><td><code>true</code> if it is a desktop</td></tr>

<td><code>isMobile</code></td><td><code>true</code> if it is a mobile device</td></tr>
<td><code>mobileName</code></td><td>Name of mobile device</td></tr>

<td><code>isPhone</code></td><td><code>true</code> if it is a mobile phone</td></tr>
<td><code>phoneName</code></td><td>Name of mobile phone</td></tr>

<td><code>isTablet</code></td><td><code>true</code> if it is a table</td></tr>
<td><code>tabletName</code></td><td>Name of tablet</td></tr>


<td><code>mobileGrade</code></td><td><a href="http://jquerymobile.com/gbs">Mobile Grade (A, B, C)</a></td></tr>

<td><code>userAgent</code></td><td>Browser (only for mobile devices)</td></tr>

<td><code>isWindows</code></td><td><code>true</code> if it is Windows OS</td></tr>
<td><code>isIos</code></td><td><code>true</code> if it is iOS</td></tr>
<td><code>isAndroid</code></td><td><code>true</code> if it is Android OS</td></tr>

<td><code>os</code></td><td>Operating System (only for mobile devices)</td></tr>
<td><code>browser_version</code></td><td>Browser and version as string. Eq.<code>Firefox 41</code></td></tr>
 'mobileGrade', 
</table>


#### Methods
All the methods of [mobile-detect.js] can be reached using the `.mobileDetect` object,eq.: 

	var version = myDeviceModernizr.mobileDetect.version('Chrome');

### device-modernizr.css

The css-classes is based on the visibility classes by [ZURB Foundation](http://foundation.zurb.com/docs/components/visibility.html) and the syntax used by [Modernizr].

A number of different 'states' or device 'settings' - named `MQNAME` in the syntax - is set in the css as in [Modernizr] by adding or removing the classes `MQNAME` and `no-MQNAME` to/from the `<html>` element

Example: 

The device is a tablet : `<html class="tablet ...">`

The device is not a tablet : `<html class="no-tablet ...">`

All the `MQNAME` and `no-MQNAME` classes are added to or removed from `<html>`by [Modernizr] or `device-modernizr.js`

#### Hide/Show classes
To control if a element is displayed (show) or hidden (hide) when a given 'state' is on or off there are the following classes defined for each 'state'

	(hide|show)-for[-no]-MQNAME[-down]

The `[-down]` is only for **screen sizes** and `[-no]` is not used for **print** 

#### States

There are four 'groups' of 'states' in 

- **Screen size** - show or hide for different screen sizes
- **Device** - desktop or mobile device, type (phone/tablet), and OS
- **Orientation** - landscape or portrate
- **Print** - show or hide on print

##### Screen size

To avoid problems with breakpoints when the device changes orientation the "size" of the screen is the minimum of the `screen.height` and `screen.width`

There are five breakpoints for screen size named `screen-small`, `screen-medium`, `screen-large`, `screen-xlarge`, and `screen-xxlarge`

The breakpoints for this five groups are given in the `src/device-modernizr.js`:
<table>
<tr><td>class</td><td>Screen size (min-<b>max</b>)</td></tr>
<tr><td>screen-small</td><td>0-<b>624px<b></td></tr>
<tr><td>screen-medium</td><td>625-<b>1024px</b></td></tr>
<tr><td>screen-large</td><td>1025-<b>1440px</b></td></tr>
<tr><td>screen-xlarge</td><td>1441-<b>1920px</b></td></tr>
<tr><td>screen-xxlarge</td><td><b>>1920px</b></td></tr>
</table>

For each size-class `SCREENSIZE` there are the following classes

	show-for-SCREENSIZE      //Displayed for screen size in range
	hide-for-SCREENSIZE      //Hidden for screen size in range
	show-for-SCREENSIZE-down //Displayed for all screen size in less than max
	hide-for-SCREENSIZE-down //Hidden for all screen size in less than max
	show-for-no-SCREENSIZE   //Displayed for screen size outside range
	hide-for-no-SCREENSIZE   //Hidden for screen size outside range

Example

	<p class="show-for-no-screen-small">The screen width and height is > 624px</p> 

##### Device
Test if the device is a `desktop` or `mobile` device and subsequently if it is a `phone` or a `tablet` and the OS (`windows`, `ios`, or `android`)

	show-for-desktop / hide-for-desktop
	show-for-no-desktop / hide-for-no-desktop

	show-for-mobile / hide-for-mobile
	show-for-no-mobile / hide-for-no-mobile 
	
	show-for-phone / hide-for-phone
	show-for-tablet / hide-for-tablet

	show-for-windows / hide-for-windows
	show-for-ios / hide-for-ios
	show-for-android / hide-for-android

##### Orientation
Four classes are provided
	
	show-for-portrait / hide-for-portrait
	show-for-landscape / hide-for-landscape


##### Print
Two classes are provided

	show-for-print / hide-for-print


#### Additional css and scss

The classes in `device-modernizr.css` only controls the display of elements under certent conditions.
But other properties can be controled by using the `MQNAME` and `noMQNAME` classes

Example: To define a class `green-when-in-portrait` that displayes a element in green when orientation is portrait:

	css:
	.portrait .green-when-in-portrait { color: green; }

	scss:
	.portrait {
	  .green-when-in-portrait { color: green; }
	  ...
	}


#### Examples

	<div class="show-for-landscape">This device is in LANDSCAPE mode</div>
	<div class="show-for-portrait">This device is in PORTRAIT mode</div>

	<div class="show-for-mobile">This device IS a MOBILE device</div>
	<div class="show-for-phone">..and it is a PHONE</div>
	<div class="show-for-tablet">..and it is a TABLET</div>
	<div class="show-for-no-mobile">This device is NOT a MOBILE device</code></div>

	<div class="show-for-screen-small">The screen IS a SMALL screen</div>
	<div class="hide-for-screen-small">The screen is NOT a SMALL screen</div>
	<div class="show-for-screen-medium">The screen IS a MEDIUM screen</div>
	<div class="hide-for-screen-medium">The screen is NOT a MEDIUM screen</div>
	<div class="show-for-screen-medium-down">The screen is a MEDIUM OR smaller screen</div>

	<div class="show-for-screen-large">The screen IS a LARGE screen</div>
	<div class="hide-for-screen-large">The screen is NOT a LARGE screen</div>
	<div class="show-for-screen-large-down">The screen is a LARGE OR smaller screen</div>

	<div class="show-for-screen-xlarge">The screen IS a XLARGE screen</div>
	<div class="hide-for-screen-xlarge">The screen is NOT a XLARGE screen</div>
	<div class="show-for-screen-xlarge-down">The screen is a XLARGE OR smaller screen</div>

	<div class="show-for-screen-xxlarge">The screen IS a XXLARGE screen</div>
	<div class="hide-for-screen-xxlarge">The screen is NOT a XXLARGE screen</div>
	<div class="show-for-screen-xxlarge-down">The screen is a XXLARGE OR smaller screen</div>

	<div class="hide-for-print">This text is only on the SCREEN</div>
	<div class="show-for-print">This text is only on the PRINT</div>
	


## Copyright and License
This plugin is licensed under the [MIT license](https://github.com/FCOO/device-modernizr/LICENSE).

Copyright (c) 2015 [FCOO](https://github.com/FCOO)

## Contact information

Niels Holt niels@steenbuchholt.dk


## Credits and acknowledgements


## Known bugs

## Troubleshooting

## Changelog



