# magic-mirror-setup
Setup process for my Magic Mirror

# Following the instructions from MagicMirror^2
 - Started here:  https://docs.magicmirror.builders/getting-started/installation.html
 - Which pointed me towards sdetweil's MagicMirror setup script: https://github.com/sdetweil/MagicMirror_scripts

Ran the following code from github.com/sdetweil/MagicMirror_scripts:

```bash
bash -c  "$(curl -sL https://raw.githubusercontent.com/sdetweil/MagicMirror_scripts/master/raspberry.sh)"
```

During the install process, two questions were asked and I said 'y' to both:
 - Do you want to disable the screen saver?
 - Do you want use pm2 for auto starting of your MagicMirror

Upon completion, it printed this message:<br>
<i>We're ready! Run pm2 start MagicMirror from the ~/MagicMirror directory to start your MagicMirror.</i>

# Remote Connection

To access the desktop environment of the Raspberry Pi from another computer, run these steps to enable a VNC server on the Raspberry Pi

https://www.raspberrypi.com/documentation/computers/remote-access.html#enable-the-vnc-server-on-the-command-line

Use using raspi-config to enable the VNC server on the command line.

Open raspi-config with the following line:
```bash
sudo raspi-config
```

Navigate to Interface Options. Press Enter to select.

Select VNC. Press Enter to select.

Under "Would you like the VNC Server to be enabled?", highlight <Yes> and press Enter.

Press Enter to return to the menu. Press Esc to exit raspi-config.

# Module Installs

After being installed (cloned from GitHub), the modules need to be configured and placed in the desired location by editing the "modules: [" object of the following file:
/home/pi/MagicMirror/config/config.js


<b>WeatherGraph</b><br>
https://github.com/FlatPepsi17/MMM-WeatherGraph
```bash
cd ~/MagicMirror/modules
git clone https://github.com/FlatPepsi17/MMM-WeatherGraph
```
Edited the config file with something close to this:
```javascript
                {
		    module: 'MMM-WeatherGraph',
		    position: 'top_right',  // This can be any of the regions.
		    config: {
		      // get your API key at:  https://openweathermap.org/home/sign_up
		      apiKey: 'lotsoflettersandnumbers123',

		      latitude:   3#.####
		      longitude: -8#.####
		    }
		}
```
<br>
<b>DailyBibleVerse</b><br>
https://github.com/arthurgarzajr/MMM-DailyBibleVerse<br>

```bash
cd ~/MagicMirror/modules
git clone https://github.com/arthurgarzajr/MMM-DailyBibleVerse.git
cd MMM-DailyBibleVerse
npm install
```

Edited the config file by adding roughly this to it:
```javascript
{
			module: 'MMM-DailyBibleVerse',
			position: 'bottom_bar',	// This can be any of the regions. Best result is in the bottom_bar as verses can take multiple lines in a day.
			config: {
				version: 'ESV', // This can be changed to any version you want that is offered by Bible Gateway. For a list, go here: https://www.biblegateway.com/versions/,
		    	size: 'small' // default value is medium, but can be changed. 
			}
}
```

<b>GoogleCalendar</b><br>
https://github.com/randomBrainstormer/MMM-GoogleCalendar

Step 1:  Install GoogleAPI dependency
https://github.com/googleapis/google-api-nodejs-client

```bash
npm install googleapis
```
Step 2:  Install the module
```bash
git clone https://github.com/randomBrainstormer/MMM-GoogleCalendar.git
cd MMM-GoogleCalendar
npm install
```
Step 3:  Do lots of point and click things to get the Desktop OAuth client file from the authentication setup section

The command line item to run was this, after the .json file had been renamed and moved to the MMM-GoogleCalendar folder:
```bash
cd ~/MagicMirror/modules/MMM-GoogleCalendar/
node authorize.js
```

Added this to config file:
```javascript

{
    module: 'MMM-GoogleCalendar',
    header: "Family Calendar",
    position: "top_left",
    config: {
	calendars: [
	    {
	      symbol: "calendar-week",
	      calendarID: "numbersandletters@group.calendar.google.com"
	    },
	    // add another calendar HERE if needed
	],
    }
},
```





