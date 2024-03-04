# Localisation

### Localisation Strategies
- Inertial measurement unit (IMU)
	- accelerometer + gyroscope
	- strong anti-interference
	- fast
	- errors build up and accumulate
- Visible light communication (VLC)
	- LED
	- low cost
	- does not interfere with radio communications
- Infrared (IR)
	- active/passive landmarks
- Ultrasonic detection
	- affected by temperature and pressure
- Geomagnetic field
	- available everywhere on earth
	- low accuracy
- LIDAR
	- 2D or 3D information
	- works in dark environments
	- no modification of the environment is necessary
- Computer vision
	- e.g. using QR code beacons
	- monocular/binocular/omnidirectional
-  Radio frequency (e.g. Wi-Fi/Bluetooth/ZigBee)
	- e.g. based on received signal strength indication (RSSI) 
	- triangulation or fingerprinting (more accurate)
- Radio frequency identification (RFID)
	- active/passive tags
	- UHF-RFID is low cost and has a high data transmission rate
- Ultra-wide-band (UWB)
	- narrow-band pulses
	- high speed
	- high time-resolution

### External Positioning
- Outdoors
	- The Global Positioning System (GPS) provides metre-level outdoor positioning using information from multiple satellites
	- Atmospheric conditions limit precision unless corrected using a reference (‘differential GPS’) • Can be power hungry
	- Same method also used by mobile phone masts (triangulation).
	- Doesn’t work indoors!
- Indoors
	- Wi-Fi and Bluetooth beacons can provide positioning systems indoors, but accuracy remains limited
	- Methods:
		- ‘in-range’ 
		- signal drop-off (attenuation)
		- triangulation (like GPS) 
	- Some systems use difference in sound and electromagnetic waves from the same source.
- Limitations
	- Accuracy not sufficient for many tasks:
		- GPS ~2m at the very best
		- worse in urban environments
	- Need for infrastructure limits applications:
		- exploration of new places (e.g. Mars!)
		- disaster areas
	- Security
	- These are all example of ‘exteroceptive sensing’ (using external cues)

### On-Board Positioning
- Odometry
	- The word ‘odometry’ is composed from the Greek words ‘odos’ (meaning ‘route’) and ‘metron’ (meaning ‘measure’)
	- In mobile systems, odometry refers to the use of data from motion sensors to estimate change in position (or pose) over time
	- Odometry is used by many mobile robots to estimate their position relative to a starting location


# Maps and path planning

### Issues with localisation
- External positioning (triangulation):
	- line of sight blocked (indoors, cities)
	- can be jammed or intentionally restricted
	- generally limited accuracy
- On-board positioning (odometry):
	- accumulates error
- Potential solution: a map

### Maps
- What is a map?
	- a collection of elements or features at some scale of interest
	- a representation of the spatial and/or semantic relationships between them
- Topographic maps
	- The locations of objects in an absolute coordinate system
	- Sensors for this can be LIDAR, Infrared, Ultrasonic or Vision
	- detailed, quantitative, ‘subsymbolic’ representation
	- good for representing (and avoiding) known static obstacles
	- high computational cost of storage and processing
	- require very accurate position tracking, hence a reliance on accurate odometry and range-finder sensors
	- necessary to determine an appropriate resolution
- Topological maps
	- a record of the connections (links) between a set of places (nodes)
	- Represents known locations and the connections between them as nodes and edges in a graph
	- The edges can represent actions needed to get from one node to the next (or direction and distance)
	- Can determine an ‘optimal’ route using standard graph search methods if distances (or costs) are added to the edges
	- abstract, qualitative, ‘symbolic’ representation
	- may be more robust to dynamic environments
	- low computational cost gives efficient path planning and scale better to large environments
	- require accurate place recognition, so susceptible to ‘perceptual aliasing’ where two or more places look the same
	- necessary to determine what makes a ‘place’
- Issues with maps
	- can be resource intensive
	- can become invalid
	- has to be kept up to date and valid