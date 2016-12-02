# MetaWear UWP Streamer

This project is based on the [MetaWear UWP Starter repository](https://github.com/mbientlab/MetaWear-UwpStarter) and the [UWP C# SDK Tutorial](https://mbientlab.com/tutorial/uwp/cs/) both provided by [mbientlab](https://mbientlab.com/).

This project aims to have a Universal Windows Platform app (using the [MetaWear C++ API](https://github.com/mbientlab/Metawear-CppAPI)), which is able to stream data (through a TCP/IP connection) in real time from the [mbientlab sensors](https://mbientlab.com/sensors/) by using Bluetooth LE. The App can stream from one device at the time.

## MetaWear UWP Streamer workflow

The workflow for MetaWear UWP Streamer, or just **Streamer**, is the following:

1. The User selects the desired mbientlab sensor from the list.

2. When the User clicks on **Start**, the **Streamer** will try to connect to a TCP/IP Server in **127.0.0.1 : 40000** (For the moment this IP and Port are hardcoded, in future versions these values will be provided by the User)

2. The **Streamer** sends a data package to the Server every time new data is acquired from the mbientlab sensor.

3. Each data package, **P**, consist in **N+1** Single (float32) values

  1. **P[0]** Indicates the number of remain elements in the package, **N**
  2. **P[1]** Indicates the measurement type
    * 1 for Acceleration
    * 2 for ...
    * 3 for ...
    * ...
  3. **P[2] - P[N]** Are the data for the measurement  

    > **Example:** One acceleration data package will look as:
         [4], [1], [AccX], [AccY], [AccZ]

4. When the User clicks **Stop**, the Sender stops acquiring data from the sensor and closes the TCP/IP connection

## TODOs
* Start layout where the User can select the measurements to stream, and their samplign frequency
* LED indicating the status of the board
* Implement other measurements
* Add IP and Port as configurable fields

<!--
The commented section is the same as in [](https://github.com/mbientlab/MetaWear-UwpStarter)

# Usage ()
Further additions will mostly be added to the [DeviceSetup.xaml.cs](https://github.com/mbientlab/MetaWear-UwpStarter/blob/master/CS%20Template/DeviceSetup.xaml.cs)
file and the [DeviceSetup.xaml](https://github.com/mbientlab/MetaWear-UwpStarter/blob/master/CS%20Template/DeviceSetup.xaml)
layout file.  We will show how this is done by adding a switch that controls the LED using this app template.

## LED Switch
In the ``DeviceSetup.xaml`` layout file, we will add a toggle switch to turn on/off the LED.  

```xaml
<ToggleSwitch x:Name="ledSwitch" Header="LED" HorizontalAlignment="Stretch" Margin="10,10,10,0"
              VerticalAlignment="Top" Toggled="ledSwitch_Toggled"/>
```

In the ``DeviceSetup.xaml.cs`` file, implement the ``ledSwitch_Toggled`` function to turn on/off the LED.

```c#
private void ledSwitch_Toggled(object sender, RoutedEventArgs e) {
    if (ledSwitch.IsOn) {
        Led.Pattern pattern = new Led.Pattern();
        mbl_mw_led_load_preset_pattern(ref pattern, Led.PatternPreset.SOLID);
        mbl_mw_led_write_pattern(cppBoard, ref pattern, Led.Color.BLUE);
        mbl_mw_led_play(cppBoard);
    } else {
        mbl_mw_led_stop_and_clear(cppBoard);
    }
}
```

After making your code changes, load the app on your phone and use the switch to turn on/off the LED. -->
