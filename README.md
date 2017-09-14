## Prerequisites

### Java:

### Youtube-dl:

##### Linux
Use these commands in the terminal to install youtube-dl on Linux:  
`sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl`   
`sudo chmod a+rx /usr/local/bin/youtube-dl`


#### Prebuilt jar
Unless you want to build the jar yourself with Gradle you need to download it here https://eternal.abimon.org/built.jar and place it in the folder containing `default-config.json` and `jukebox_index.html`


## Configuring
First thing to do is rename `default_config.json` to `config.json`, then open it with notepad/notepad++ on Windows and whatever text editor you like on Linux (for example nano: `nano config.json`)

Now you should go to https://developer.spotify.com/my-applications/ and log in to your spotify account.  
Then click the "Create an app" button and a new page should popup.   
There give it a name and description and click create.   
It should send you to the new app's page, the only thing you need from here is your Client ID and Client Secret  
(Note: Never share these with anyone!)  

Now fill in the Config file accordingly, you can also change the port if you'd like it to be something else but other than that there is no need to touch other options.  

#### SQL (Not required but does make some specific stuff work correctly)
For this you will need a SQL server running on the same machine that EternalJukebox will be running on.  
I won't explain how to make a SQL server but if you don't know here is a page to get you started:  
https://dev.mysql.com/doc/mysql-getting-started/en/  

If you want SQL you will need to replace the contents of the config.json with the one below and fill that in instead.  
```
{
  "comment":"This is the default config used by EternalJukebox, make sure to fill everything in for EternalJukebox to work correctly!",
  "ip":"http://$ip:$port",
  "port":11037,
  "logAllPaths":true,
  "spotifyClient":"Insert your Spotify Client ID Here",
  "spotifySecret":"Insert your Spotify Client Secret Here",
  "mysqlUsername":"Your SQL username",
  "mysqlPassword":"Your SQL password",
  "mysqlDatabase":"The SQL database used by EternalJukebox",
  "uploads":true
}  
```
When you are done save the config and move on to the next step.   

## Starting the server:

First you need to open the Terminal or Command Prompt.  
Then make sure its running in the folder that your EternalJukebox.jar is in, once again to do this use the `cd` command.  
Then execute the jar with `java -jar EternalJukebox.jar`

If everything went right it should say `Listening at http://0.0.0.0:11037`  

you should now be able to connect to it with a browser through http://localhost:11037  

Congrats you did it!  

## Building with gradle (for those who want to):
Firstly ofcourse you need to install gradle.  
There is a full documentation on how to do this here https://gradle.org/install  

Open a Command Prompt as Administrator or Terminal on linux and move to the folder you cloned the project files to earlier.
E.g. `cd C:\EternalJukebox`  

Now use the command `gradle clean shadowJar`
And it should start building!

Once this is finished move the .jar from build/libs/ to the project folder and rename it to EternalJukebox.jar

Now you should be done and ready to run it!
