# Tango-Newport_AG_UC8
This repository contains the driver for controlling a Newport AG_UC8 Controller with the Tango Control. After cloning this repository with the following command

```
git clone https://github.com/Golp-Voxel/Tango-Newport_AG_UC8.git
```

It is necessary to create the `tango-env` using the following command:

```
python -m venv tango-env
```

After activating it you can install all the models to run this tool by using the command:

```
pip install -r Requirements.txt
```

To complete the installation, it is necessary to copy the `AG_UC8.bat` template and change the paths to the installation folder. And the command to run the `tango-env\Scripts\activate` script. 

## Available commands

- [Connect](#Connect)
- [ZeroPosition](#ZeroPosition)
- [MeasurePosition](#MeasurePosition)
- [MoveRel](#MoveRel)
- [StatusMotor](#StatusMotor)
- [Reset](#Reset)
- [StepAmplitudePos](#StepAmplitudePos)
- [StepAmplitudeNeg](#StepAmplitudeNeg)
- [Steps](#Steps)

### Connect

```python
Connect(AG_UC8)
```

```
AG_UC8 = {
            "Name"      : <user_name_given_on Connect>,
            "COM"       : 0
         }
```

### ZeroPosition

```python
ZeroPosition(userinfoZP)
```

```
userinfoZP = {
                "Name"      : <user_name_given_on Connect>,
                "Channel"   : 1 to 4,
                "Axis"      : 1 or 2
            }
```


### MeasurePosition

Measures the position of the given axis. The position is returned as a number from 0 to 1000 corresponding to the full travel range of the mount.

```python
MeasurePosition(userinfoMP)
```

```
userinfoMP = {
                "Name"      : <user_name_given_on Connect>,
                "Channel"   : 1 to 4,
                "Axis"      : 1 or 2
            }
```


### MoveRel

```python
MoveRel(userinfoMR)
```

```
userinfoMR = {
                "Name"      : <user_name_given_on Connect>,
                "Channel"   : 1 to 4,
                "Axis"      : 1 or 2,
                "Position"  : 0 to 500
            }
```


### StatusMotor

```python
StatusMotor(userinfoS)
```

```
userinfoS =    {
                    "Name"      : <user_name_given_on Connect>,
                    "Channel"   : 1 to 4,
                    "Axis"      : 1 or 2
                }
```

### Reset

```python
Reset(userinfoR)
```

```
userinfoR =  {
                    "Name"      : <user_name_given_on Connect>
                }
```

### StepAmplitudePos

Returns the step amplitude in the positive direction. If the optional `"Amplitude"` field is given, it is set before being read back.

```python
StepAmplitudePos(userinfoSAP)
```

```
userinfoSAP =  {
                    "Name"      : <user_name_given_on Connect>,
                    "Channel"   : 1 to 4,
                    "Axis"      : 1 or 2,
                    "Amplitude" : -50 to 50 (optional)
                }
```

### StepAmplitudeNeg

Returns the step amplitude in the negative direction. If the optional `"Amplitude"` field is given, it is set before being read back.

```python
StepAmplitudeNeg(userinfoSAN)
```

```
userinfoSAN =  {
                    "Name"      : <user_name_given_on Connect>,
                    "Channel"   : 1 to 4,
                    "Axis"      : 1 or 2,
                    "Amplitude" : -50 to 50 (optional)
                }
```


### Steps

Returns the accumulated number of steps of the given axis.

```python
Steps(userinfoSteps)
```

```
userinfoSteps =  {
                    "Name"      : <user_name_given_on Connect>,
                    "Channel"   : 1 to 4,
                    "Axis"      : 1 or 2
                }
```

## Exemple of controller a step motor


```python
import tango
import json
N_AG_UC8 = tango.DeviceProxy(<AG_UC8_Tango_location_on_the_database>)
print(N_AG_UC8.state())


# you need to check the SerialCOM of the device
AG_UC8 = {
            "Name"      : "Controller_1",
            "COM"       : 0
         }

print(N_AG_UC8.Connect(json.dumps(AG_UC8)))

Controller_info =  {
                        "Name"      : "Controller_1",
                        "Channel"   : 1,             
                        "Axis"      : 1              
                    }

Controller_info = json.dumps(Controller_info)

N_AG_UC8.Reset(Controller_info)

N_AG_UC8.ZeroPosition(Controller_info)

print(N_AG_UC8.Steps(Controller_info))
print("Initial step amplitude:", N_AG_UC8.StepAmplitudePos(Controller_info))


Move_info = {
                "Name"      : "Controller_1",
                "Channel"   : 1,
                "Axis"      : 1,
                "Position"  : -7500
            }
Move_info = json.dumps(Move_info)

N_AG_UC8.MoveRel(Move_info)

print(N_AG_UC8.StatusMotor(Controller_info))
print(N_AG_UC8.Steps(Controller_info))

```
