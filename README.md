# Tango-Newport_AG_UC8


## 

- (Connect)[#Connect]
- (ZeroPosition)[#ZeroPosition]
- (MeasurePosition)[#MeasurePosition]
- (MoveRel)[#MoveRel]
- (Status)[#Status]
- (MoveRel)[#Reset]
- (StepAmplitudePos)[#StepAmplitudePos]
- (StepAmplitudeNeg)[#StepAmplitudeNeg]

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
