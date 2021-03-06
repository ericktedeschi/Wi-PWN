## How to open a local copy of the WebOS
1. Launch `local-server.bat` which will start a localhost server and open it up in your default browser.

Alternatively you can just directly open the HTML files, but you won't be able to fully load the pages as they rely on importing files (which doesn't work without being on a server)

**NOTE:** The included `.json` file are there to simulate example output from the ESP8266 module. Do not include them in the final binary! 


##There are two ways to update web-server files

### Script Mode (Linux/Mac)
1. Update the desired files on ./html folder
2. at the command line run the shell script: ./convert_all.sh
3. open the generated file "data_h_temp" and copy the content (CTRL+C)
4. Go to [arduino/Wi-PWN/data.h](http://github.com/Wi-PWN/Wi-PWN/arduino/Wi-PWN/data.h) and replace the content between the comments like below:

```c
/* constants generated by convert_all.sh - start */
const char data_attackHTML[] PROGMEM = {0x3c,0x68,0x65,0x61...
const char data_darkCSS[] PROGMEM = {0x23,0x6c,0x6f,0x67,0x...
const char data_detectorHTML[] PROGMEM = {0x3c,0x68,0x65,0x...
const char data_errorHTML[] PROGMEM = {0x3c,0x68,0x65,0x61,...
const char data_indexHTML[] PROGMEM = {0x3c,0x68,0x65,0x61,...
const char data_infoHTML[] PROGMEM = {0x3c,0x68,0x65,0x61,0...
const char data_js_attackJS[] PROGMEM = {0x66,0x75,0x6e,0x6...
const char data_js_functionsJS[] PROGMEM = {0x66,0x75,0x6e,...
const char data_js_scanJS[] PROGMEM = {0x66,0x75,0x6e,0x63,...
const char data_js_settingsJS[] PROGMEM = {0x66,0x75,0x6e,0...
const char data_js_usersJS[] PROGMEM = {0x66,0x75,0x6e,0x63...
const char data_mainCSS[] PROGMEM = {0x3a,0x72,0x6f,0x6f,0x...
const char data_settingsHTML[] PROGMEM = {0x3c,0x68,0x65,0x...
const char data_setupHTML[] PROGMEM = {0x3c,0x68,0x65,0x61,...
const char data_usersHTML[] PROGMEM = {0x3c,0x68,0x65...
/* constants generated by convert_all.sh - end */
```

### Manual Mode

1. Open `minifier.html` and paste the HTML source in input field  
2. Click on <kbd>minifiy + byte-ify</kbd>  
3. Copy the results  
4. Go to [arduino/Wi-PWN/data.h](http://github.com/Wi-PWN/Wi-PWN/arduino/Wi-PWN/data.h) and replace the array (of the changed html file) with the copied bytes  

You can now compile the binary using the Arduino project file ([arduino/Wi-PWN/Wi-PWN.ino](http://github.com/Wi-PWN/Wi-PWN/arduino/Wi-PWN/Wi-PWN.ino))

**Remember to upload your sketch :)**

##Better compression rates

It is possible to get better compression rates by using [kangax/html-minifier](https://github.com/kangax/html-minifier)
