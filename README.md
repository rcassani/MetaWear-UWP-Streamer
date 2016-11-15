# MetaWear UWP Stramer

This project is based on the [MetaWear UWP Starter repository](https://github.com/mbientlab/MetaWear-UwpStarter) and the [UWP C# SDK Tutorial](https://mbientlab.com/tutorial/uwp/cs/) both provided by [mbientlab](https://mbientlab.com/).

This project aims to have a Universal Windows Platform app using the [MetaWear C++ API](https://github.com/mbientlab/Metawear-CppAPI) able to stream data (throuh a TCP/IP connection) in real time from the [mbientlab sensors](https://mbientlab.com/sensors/) by using Bluetooth LE.

<!-- # Usage
User additions will mostly be added to the [DeviceSetup.xaml.cs](https://github.com/mbientlab/MetaWear-UwpStarter/blob/master/CS%20Template/DeviceSetup.xaml.cs)
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
