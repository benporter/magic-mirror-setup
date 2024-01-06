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
We're ready! Run pm2 start MagicMirror from the ~/MagicMirror directory to start your MagicMirror.

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
		},
```
<br>
<b>DailyBibleVerse</b><br>
https://github.com/arthurgarzajr/MMM-DailyBibleVerse
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




