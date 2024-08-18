# Uber Like Android App
Building a ride-sharing Android Taxi Clone App like Uber, 


</p>
<br>

## About me

Hi, I am Nimisha Kumari, currently working on this project that uses Beckn Protocol.
.

## following for the App like Uber:
* Create Rider Android Clone App
* Fetch and show nearby cabs on Google Map
* Set Pickup and drop location
* Book a cab
* Fetch and show driver current location
* Show pickup and trip path on Map with Animation
* Cab Arrival for a pickup like Uber
* On-going trip UI
* Trip End
* Animation like Uber App for Moving Car
* Just to make it simple. This project uses the basic MVP Architecture for building the Uber and Lyft clone
* We have simulated the WebSocket API for you 



local.properties will like below:
```
sdk.dir=PATH_TO_ANDROID_SDK_ON_YOUR_LOCAL_MACHINE    
apiKey=YOUR_API_KEY
```
* Start implementing features:
   * Start with a new project.
   * Setup project with basic MVP Architecture.
   * Implement Permission for fetching current location.
   * Implement feature - nearby cabs.
   * Use WebSocket present in `simulator` module to fetch the nearby cabs.
   * Implement feature - pickup and drop location.
   * Implement feature - book a cab.
   * Implement feature - Show pickup path on the map with Animation.
   * Implement feature - Show the current driver location during pickup.
   * Implement feature - Cab is arriving and arrived.
   * Implement feature - Car Animation like Uber.
   * Implement feature - Show trip path on the map with Animation.
   * Implement feature - Trip Starts.
   * Implement feature - Show the current driver location during the trip.
   * Implement feature - Trip on-going.
   * Implement feature - Trip Ends.
   * Implement feature - Implement Take Next Ride.

## WebSocket API Reference for this project
A WebSocket is a persistent connection between a client and server. WebSockets provide a bidirectional, full-duplex communications channel that operates over HTTP through a single TCP/IP socket connection. At its core, the WebSocket protocol facilitates message passing between a client and server. In our case, we have simulated it for you.

* In WebSocket, we have three methods:
   * `connect()`: To connect with the server
   * `sendMessage(data: String)`: To send the data to the server
   * `disconnect()`: To disconnect from the server

* In WebSocketListener, we have four callbacks:
   * `onConnect()`: Called when it is connected with the server
   * `onMessage(data: String)`: Called when an event comes from the server
   * `fun onDisconnect()`: Called when the client is disconnected from the server
   * `fun onError(error: String)`:  Called when the error occurred on the server

* Client sending event to server using `webSocket.sendMessage(data)`:
    * Request for nearby cabs from server
    ```json
    {
      "type": "nearByCabs",
      "lat": 28.438147,
      "lng": 77.0994446
    }
    ``` 
   * Request a cab from server
    ```json
    {
      "type": "requestCab",
      "pickUpLat": 28.4369353,
      "pickUpLng": 77.1125599,
      "dropLat": -25.274398,
      "dropLng": 133.775136
    }
    ```
  
* The Server sending success event to the client received in `onMessage(data: String)`:
   * NearBy cabs 
    ```json
    {
      "type": "nearByCabs",
      "locations": [
        {
          "lat": 28.439147000000002,
          "lng": 77.0944446
        },
        {
          "lat": 28.433147,
          "lng": 77.0952446
        },
        {
          "lat": 28.440547000000002,
          "lng": 77.1026446
        }
      ]
    }
    ```
   * Cab Booked
    ```json
    {
      "type": "cabBooked"
    }
    ```  
   * PickUp Path
    ```json
    {
      "type": "pickUpPath",
      "path": [
        {
          "lat": 28.43578,
          "lng": 77.10198000000001
        },
        {
          "lat": 28.43614,
          "lng": 77.10164
        },
        {
          "lat": 28.436400000000003,
          "lng": 77.10149000000001
        }
      ]
    }
    ```   
   * Cab Current Location during pickup or trip
    ```json
    {
      "type": "location",
      "lat": 28.43578,
      "lng": 77.10198000000001
    }
    ```  
   * Cab is Arriving
    ```json
    {
      "type": "cabIsArriving"
    }
    ```    
   * Cab Arrived
    ```json
    {
      "type": "cabArrived"
    }
    ```    
   * Trip Start
    ```json
    {
      "type": "tripStart"
    }
    ```       
   * Trip Path
    ```json
    {
      "type": "tripPath",
      "path": [
        {
          "lat": 28.438370000000003,
          "lng": 77.09944
        },
        {
          "lat": 28.438450000000003,
          "lng": 77.1006
        },
        {
          "lat": 28.438480000000002,
          "lng": 77.10095000000001
        }
      ]
    }
    ``` 
   * Trip End
    ```json
    {
      "type": "tripEnd"
    }
    ```          
* The server sending the error event to the client received in `onError(error: String)`:
   * Direction API Failed
    ```json
    {
      "type": "directionApiFailed",
      "error": "Unable to resolve host \"maps.googleapis.com\": No address associated with hostname"
    }
    ```
   * Routes Not Available
    ```json
    {
      "type": "routesNotAvailable"
    }
    ```  




```
