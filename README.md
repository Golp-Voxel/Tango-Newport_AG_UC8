# Tango-Newport_AG_UC8


## Available commands

- [Connect](#Connect)
- [ZeroPosition](#ZeroPosition)
- [MeasurePosition](#MeasurePosition)
- [MoveRel](#MoveRel)
- [StatusMotor](#StatusMotor)
- [MoveRel](#Reset)
- [StepAmplitudePos](#StepAmplitudePos)
- [StepAmplitudeNeg](#StepAmplitudeNeg)

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
                "Channel"   : 0 to 3,
                "Axis"      : 1 or 2
            }
```


### MeasurePosition

```python
MeasurePosition(userinfoMP)
```

```
userinfo = {
                "Name"      : <user_name_given_on Connect>,
                "Channel"   : 0 to 3,
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
                "Channel"   : 0 to 3,
                "Axis"      : 1 or 2,
                "Position"  : 0 to 500
            }
```


### Status

```python
Status(userinfoS)
```

```
userinfoS =    {
                    "Name"      : <user_name_given_on Connect>,
                    "Channel"   : 0 to 3,
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

```python
StepAmplitudePos(userinfoSAP)
```

```
userinfoSAP =  {
                    "Name"      : <user_name_given_on Connect>,
                    "Channel"   : 0 to 3,
                    "Axis"      : 1 or 2
                }
```

### StepAmplitudeNeg

```python
StepAmplitudeNeg(userinfoSAN)
```

```
userinfoSAN =  {
                    "Name"      : <user_name_given_on Connect>,
                    "Channel"   : 0 to 3,
                    "Axis"      : 1 or 2
                }
```


### Steps

```python
Steps(userinfoSteps)
```

```
userinfoSteps =  {
                    "Name"      : <user_name_given_on Connect>,
                    "Channel"   : 0 to 3,
                    "Axis"      : 1 or 2
                }
```

## Exemple of controller a step motor


```python
import tango
import json
N_AG_UC8 = tango.DeviceProxy(<Thorlabs_Tango_location_on_the_database>)
print(N_AG_UC8.state())


# you need to check the SerialCOM of the device
AG_UC8 = {
            "Name"      : "Controller_1",
            "COM"       : 0
         }

print(N_AG_UC8.Connect(AG_UC8))

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
