# CarND-Unscented-Kalman-Filter
Self-Driving Car Engineer Nanodegree Program

---

## Dependencies

* cmake >= 3.5
 * Used installer: cmake-3.7.2-win64-x64.msi
* make >= 4.1
  * Used installer: make-3.81.exe
* gcc/g++ >= 5.4
  * Used installer: mingw-get-setup.exe

## Basic Build Instructions
Once you have this repository on your machine, `cd` into the repository's root directory and run the following commands from the command line:
```
mkdir build && cd build
cmake .. && make
UnscentedKF (path_to_input).txt (path_to_output).txt
    - eg. `UnscentedKF ../data/obj_pose-laser-radar-synthetic-input.txt output.txt`
```
**NOTE**
> If you encounter any problems, copy "vcvars32.bat" to build directory and run the command `vcvars32` to set environment variables
> If make command does not work try: `cmake .. -G "Unix Makefiles" && make`
> You can find some sample inputs in 'data/'.

## Algorithm
```
	For each measurement in the file	
		If this is the first measurement
			If it is from Radar
				Convert from polar coordinates to cartesian coordinates
			End If
			Initialize measurements
		Else
			If current timestamp is different from previous timestamp
				Predict the current state
			End If
			Update based on sensor type
		End If
	End For
```

## Testing
* Using combined sensors (use_laser_ = true and use_radar_ = true):
	- RMSE (px, py, vx, and vy) = 0.078 - 0.085 - 0.215 - 0.268
* Using only laser (use_laser_ = true and use_radar_ = false):
	- RMSE (px, py, vx, and vy) = 0.170 - 0.145 - 0.269 - 0.333
* Using only radar (use_laser_ = false and use_radar_ = true):
	- RMSE (px, py, vx, and vy) = 0.228 - 0.341 - 0.550 - 1.002
* Using extended Kalman filter:
	- RMSE (px, py, vx, and vy) = 0.140 - 0.666 - 0.604 - 1.624
	
* NIS values were within the expected range (0.35 and 7.81)

* Log files are stored in the folder (output)