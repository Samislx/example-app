# Introduction
Q is an app based website that allows you to create web applications to manage everything that you can connect on Internet.

# Models

### Network
Basically, a Network is a group of Devices.
```json
{
  ":id": "8e9c8a3f-cd3c-41be-9a52-a2c6d0f3c82a",
  ":type": "urn:seluxit:xml:bastard:network-1.2",
  "name": "example network",
  "device": []
}
```

### Device
Device represents a real object like a light or a mower. One Device can contain multiple values like on/off or brightness.
```json
{
  ":id": "8e9c8a3f-cd3c-41be-9a52-a2c6d0f3c82b",
  ":type": "urn:seluxit:xml:bastard:device-1.2",
  "name": "light device",
  "type": "light",
  "serial": "23B7",
  "manufacturer": "Seluxit",
  "communication": "always",
  "protocol": "hue",
  "included": "1",
  "product": "SeluxitLight",
  "value": []
}
```

### Value
Value is a service of the device, for example: a device that represents a lamp can have values on/off, brightness and color. A Value can have some limitations as min, max or steps.<br/>
The attribute permission say if you can change the status of the object or only see it.
```json
{
  ":id": "8e9c8a3f-cd3c-41be-9a52-a2c6d0f3c82c",
  ":type": "urn:seluxit:xml:bastard:value-1.2",
  "name": "switch",
  "type": "on/off",
  "permission": "rw",
  "status": "ok",
  "state": []
}
```

### State
In relation if we can modify or not the Value, we will have a Control state. Similarly we will have a Report state to retrieve the current status of the Value.
```json
{
  ":id": "8e9c8a3f-cd3c-41be-9a52-a2c6d0f3c82d",
  ":type": "urn:seluxit:xml:bastard:state-1.2",
  "type": "Report",
  "data": "1",
  "status": "ok",
  "timestamp": "2016-02-15T10:52:45.561090Z"
}
```

### Data
Data will save whatever you put in it.
```json
{
  ":id": "8e9c8a3f-cd3c-41be-9a52-a2c6d0f3c82d",
  ":type": "urn:seluxit:xml:bastard:data-1.2",
  "nickname": "Ohayo"
}
```

# Example
Every Network is composed of different Devices.<br/>
Suppose that, for example, we have a Halloween pumpkin with red lights as eyes, a camera as nose and a mouth provided of some led that we can use to write some messages. Then we have the following structure:

* our pumpking is our Network
* the eyes of the pumking are two Devices under our Network pumpkin
* the camera in the nose is another Device
* the leds in the mouth are another Device.

In conclusion we have a Network with four Devices.

Every Device is composed of different components, these components are called Values.<br/>
Consider one of the eyes of our pumpkin,they are smart device lights where we can provide different colours (RGB), different intensity and turn them on and off. This means that for each light we have the following structure:

* our light is our Device
* the colour of the light is value
* the intensity of the light is another value
* the possibility to turn the light on or off is another value

In short we have a Device with three Values.

Every Value can have one or two States in relation depending on the permission if we can "read", "write" or "read & write".<br/>
Consider the intensity of the light: clearly we want to be able to check the actual intensity, and we want to be able to modify the intensity of the light. For this reason we have the following two States:

* a Report State: used to read the actual State of our Value
* a Control State: used to modify the State of our Value

In short this Value is provided of two States.
