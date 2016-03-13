LeapDrone Python
================

Last edit: February 1, 2016

What is it ?
------------

LeapDrone Python is a Python script that enables you to control your [Ardupilot](http://copter.ardupilot.com/) drone with your hand thanks to the Leap Motion controller.

For now it can just handles the pitch and roll.

Dependencies
------------

In order to work properly, this script needs the following dependencies:

* Python v2.7
* DroneKit-Python 2.X
* Leap Motion SDK (Python)

Installation
------------

### 1. Install Python v2.7 and pip if not already installed

### 2. Download and install the python version of the Leap Motion SDK

Follow instructions on the [Leap Motion developer portal](https://developer.leapmotion.com/downloads).

To avoid inserting the path of the Leap Motion SDK in all your Python projects, you can copy the libraries in the Python `site-packages` directory.

The following steps show how to do it on a mac OS X setup.

**Locate the path of the `site-packages` directory**

```python
$ python
>>> import site; site.getsitepackages()
['/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python', '/Library/Python/2.7/site-packages']
```

**Copy the files into the `site-packages` directory**

Refer to [Leap Motion Website](https://developer.leapmotion.com/documentation/python/devguide/Leap_SDK_Overview.html#python) to know what are the needed files.

```sh
$ cp LeapSDK/lib/{Leap.py,LeapPython.so,libLeap.dylib} /Library/Python/2.7/site-packages
```

### 3. Install DroneKit-Python 2.x

Please refer to [Dronekit official documentation](http://python.dronekit.io/guide/quick_start.html#installation).

### 4. Install LeapDrone

A simple git clone is all you need to install this project:

```sh
$ git clone https://github.com/TenOs/leapdrone-python.git
```

Running the script
------------------

### Command usage

```sh
usage: leapdrone.py [-h] [-d] [-a Z] [-b B] [-l] [-t] [-o VAL] [-r]
                    vehicle_address

Control a drone with your hand thanks to the Leap Motion tracker

positional arguments:
  vehicle_address       For vehicle's address format see
                        http://python.dronekit.io/guide/connecting_vehicle.html#get-started-connecting

optional arguments:
  -h, --help            show this help message and exit
  -d, --debug           Show debug messages, kind of a verbose mode
  -a Z, --altitude Z    Relative flight altitude in meters, default is 5m
  -b B, --baud B        Set connection Baud rate
  -l, --land            Land and disarm when flight is over
  -t, --takeoff         Arm and takeoff the vehicle
  -o VAL, --overrideThrottle VAL
                        Override throttle to a value (default value is 1500)
  -r, --rtl             Return to launch, land and disarm when flight is over

NB: if both land and return to launch are set, the vehicle will only land, the priority is on land mode
```

Please refer to the [Dronekit documentation](http://python.dronekit.io/guide/connecting_vehicle.html#get-started-connecting) for the vehicle address format.

### Example

```sh
$ python leapdrone.py udp:localhost:14551 -a 7 -d
```

Technical notes
---------------

The script currently only supports the pitch and roll. For safety measures the flight mode is switched to `ALT_HOLD`.

Since the Leap Motion SDK only supports Python v2.7 this script cannot be run with Python 3.

License
-------

LeapDrone Python is released under the permissive open source [Apache v2.0 license](LICENSE).

--------
Copyright 2016 Jean-Baptiste Martin (github at martinjb dot com)
