# MetaWear UWP Streamer

The **MetaWear UWP Streamer** is a **Universal Windows Platform** (UWP) app that  uses the [MetaWear C++ API](https://github.com/mbientlab/Metawear-CppAPI) to get data from a [MetaWear sensor](https://mbientlab.com/sensors/) (connected via Bluetooth Low Energy) and creates a client to stream that data (through a TCP/IP connection).

This project is based on the [MetaWear UWP Starter repository](https://github.com/mbientlab/MetaWear-UwpStarter) and the [UWP C# SDK Tutorial](https://mbientlab.com/docs/apis/c/) both provided by [mbientlab](https://mbientlab.com/).

This UMP Streamer has been tested in Windows10 with the XXXX MetaWear sensor.

## Build Solution
1. Open the solution in Visual Studio 2015 (Windows 10 is required)
2. Install the C# UWP library from NuGet as shown in this [MetaWear C# Tutorial Video](https://www.youtube.com/watch?v=AwdbTSwnwfk#t=01m30s) @ 1m30s
3. Select your architecture (x64) and run the app.

## Usage of the UWP Streamer workflow
The workflow for **MetaWear UWP Streamer**, or just **Streamer**, is the following:

1. Select the desired **mbientlab sensor** from the list.

2. Click on **Start**. Now the **Streamer** will try to connect to a TCP/IP Server in **127.0.0.1 : 40000** (For the moment this IP and Port are hardcoded).

2. Once connected, the **Streamer** sends a data package to the Server every time new data is acquired from the **mbientlab sensor**.

3. Each data package, **P**, consist in **N+1** Single (float32) values

  1. **P[0]** Indicates the number of remain elements in the package, **N**
  2. **P[1]** Indicates the measurement type
    * 1 for Acceleration
       * 3 data points, X, Y and Z [units]
    * 2 for ...
    * 3 for ...
    * ...
  3. **P[2] - P[N]** Are the data for the measurement  

    > **Example:** One acceleration-data package will look as:
         [4], [1], [AccX], [AccY], [AccZ]

4. When the User clicks **Stop**, the Streamer stops acquiring data from the sensor and closes the TCP/IP connection.

<!-- # Sampling frequencies in MetaHub
* Accelerometer
  12.5, 25, 50, 100 and 200 Hz
* Ambient light
  0.5, 1, 2, 5, 10 Hz
* Gyroscope
  12.5, 25, 50, 100 and 200 Hz
* Barometer
  0.25, 0.5, 0.99, 1.96, 3.82, 7.33, 13.51, 83.3 Hz
* Temperature
  1Hr, 30min, 15min, 1m, 30s, 15s, 1s -->


## TODOs
* Add IP and Port as configurable fields
* LED indicating the status of the board
* Selecting the device will lead to a Setup page to configure the measurements to stream, and their sampling frequency
* Implement other measurements

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
