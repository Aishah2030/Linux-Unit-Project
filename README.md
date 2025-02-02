# Bash-Weather



## About
- weather.sh gets the current weather from OpenWeather and displays the results to the terminal

  
## Prerequisites
- OpenWeatherMap API key (http://openweathermap.org/appid).
- Bash shell
- curl command-line tool for getting data using HTTP protocol. curl can be found in the curl package on major Linux distributions.
- jq command-line tool for parsing JSON data. jq can be found in the jq package on major Linux distributions.


## How to use
Run weather.sh 
```
./weather2.sh
```
Add your OpenWeatherMap API key to the end of the openweathermap.key file,

```
# Add your OpenWeatherMap API key below (http://openweathermap.org/appid)
```
## Command-line options
`-s` The -s option can be used to specify arguments:


`-jq` a lightweight and flexible command-line JSON processor


`-r` True if file exists and is readable.

 
##### Example
Get the current weather in Riyadh:
```
./weather2.sh Riyadh
```
### Keyboard functions
current_weather()

### Screenshoot
![Weather](https://github.com/Aishah2030/Linux-Unit-Project/assets/90576780/039da1d9-ae5a-478d-8251-4b2c6f9ca973)


## Usage/Examples

```javascript
./'weather.sh'
#!/bin/bash
Username=$(whoami)
date=$(date "+%D")

        # Function to print the current weather.
current_weather() {

            echo "Welcome $Username"
            echo " Enter City Name to Check the Weather:"
   read city # city name passed as argument

   # Make a GET request to the weather API and retrieve the response
    local response=$(curl -s "http://api.openweathermap.org/data/2.5/weather?q=$city&appid=b07c392fc634b3b3241ddfe75315c74a&unit$

# Check if the request was successful
    if [ $? -eq 0 ]; then

# Extract the relevant weather information from the response
        local temperature=$(echo "$response" | jq -r '.main.temp')
       local description=$(echo "$response" | jq -r '.weather[0].description')


# Print the weather information
        echo "Weather In $city For Today $date Is:"
        echo "Temperature: $temperature °C"
        echo "Description: $description"
 else
      echo "Failed to retrieve weather information."
    fi
 }

      current_weather | tee city_log.txt
    sleep 2

        echo "Want to see other City? Yes/No "
read answer
            if [ $answer == "yes" ];
then
            current_weather

elif        [ $answer == "no" ];
then
        echo "Have a nice day! See u next time"
fi

```
