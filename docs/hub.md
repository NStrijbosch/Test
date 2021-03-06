
!!! info
     LEGO has published official docs on the hub-module: [https://lego.github.io/MINDSTORMS-Robot-Inventor-hub-API/](https://lego.github.io/MINDSTORMS-Robot-Inventor-hub-API/)


# Hub status

## info()

`hub.info()`

Get hub information.

__Returns:__

* [dictionary](data_types.md#dictionary) including:  
  usb_vid (USB vendor ID)
  device_uuid  (unique device ID)
  1ms_tick_on_time(?)  
  usb_pid (USB   
  1ms_tick_min(?)  
  1ms_tick_miss(?)  
  hardware_version  
  product_variant  
  1ms_tick_total(?)

__Sample code:__

``` python
import hub

print(hub.info())
```

<span class='shell_output'>
\> {'usb_vid': 1684, 'device_uuid': '03970000-3900-5000-1851-383332353732', '1ms_tick_on_time': 99.8596, 'usb_pid': 9, '1ms_tick_min': 58000.0, '1ms_tick_miss': 1022, 'hardware_version': 'Version_E', '1ms_tick_max': 2.6265e+07, 'product_variant': 0, '1ms_tick_total': 728280}
</span>


## status()

`hub.status()`

Get hub status of hub including all sensors and motors

__Returns:__ 

*  [dictionary](data_types.md#dictionary) including:   
   gyroscope  
   port  
   accelerometer  
   yaw_pitch_roll  
   position  
   display

__Sample code:__

``` python
import hub

print(hub.status())
```

<span class='shell_output'>
\> {'gyroscope': (0, 0, 0), 'port': {'C': [], 'D': [], 'B': [], 'E': [], 'A': [0, 0, -2, 0], 'F': []}, 'accelerometer': (-78, -305, 966), 'yaw_pitch_roll': (-27, -17, 4), 'position': (-27, -17, 4), 'display': '00000:00000:00000:00000:00000'}
</span>

## temperature()

`hub.temperature()`

Get temperature of the hub (probably internal sensor?)

__Returns:__

* [float](data_types.md#float): Temperature of the hub in Celcius.

__Sample code:__

``` python
import hub

print('Temperature: ' + str(hub.temperature()))
```

<span class='shell_output'>
\> Temperature: 24.0
</span>

# Hub actions

## powerdown_timeout()

`hub.powerdown_timeout(time)`

Set the idle time until automatic power down.

__Parameters:__

*  time ([int](data_types.md#int)) in milliseconds.

__Returns:__

*  current idle time untill automatic power down (default is 30000). Only if no argument is provided. 

__Sample code:__

``` python
import hub

hub.powerdown_timeout(40000)

print('Time until automatic powerdown: '+str(hub.powerdown_timeout())+ ' ms')
```
<span class='shell_output'>
\> Time until automatic powerdown: 40000 ms
</span>

## reset()

`reset()`

Power off the hub

!!! note
    If the hub is connected to a computer via the usb cable this will result in an automatic restart after powering down the hub. 

__Sample code:__

``` python
import hub

hub.reset()
```

## power_off()

`power_off()`

!!! Warning 
    Not actual shutdown, display is cleared and led is turned off. Hub stays connected. 

__Sample code:__
``` python
import hub

hub.power_off()
```

## repl_restart()

`repl_restart()`

!!! danger
    This method results in keyboard interrupt + error message when using the SPIKE App. Not advised to use!  
    In REPL nothing is observed.


## file_tansfer()

`file_transfer()`

!!! todo
    Not sufficiently tested