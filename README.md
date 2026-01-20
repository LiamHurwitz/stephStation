# A weather station for my buddy

## Project Structure
I need code that:
- Takes incoming weather data from an Arduino every 15 minutes
- Parses it and stores it into an SQLite database
- Creates a graph from the SQLite and current data
- Displays this graph on a local website
- Sends this information back to an Arduino for it to display

The Arduino E-ink screen needs to:
- Run code once to initialize the screen 
- Recieve the data from the server and choose the correct pixel art and graphs

### File structure
- arduino_recieve.py
    Scans for incoming data packets and converts them into nice json
- data_handle.py
    Takes json data and stores it in a connected SQLite database
- weather_viz.py
    Fetches current and historical (1 week) data from DB and visualizes it on graphs
- web_backend.py (may need to be multiple files)
    Takes current/historical data and graphs and exports them to the backend of a simple website
    Will likely need some HTML/CSS to make the site look OK. Only one page needed
- arduino_send.py
    Send a packet of data to the E-ink ESP32 every 15 minutes with updated data

- station_send.ino
    Send weather data over Wifi as a small JSON packet every 15 minutes to the server
- eink_config.ino
    Initialize pixel art and empty graphs
    Scan for and recieve weather data
    Update graphs with current weather data / change art if necessary
