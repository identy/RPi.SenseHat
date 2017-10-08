# RPi.SenseHat
A complete Windows IoT class library for the Raspberry Pi "Sense HAT" (C#)

The solution contains the following projects:
*) Rpi.SenseHat
*) RPi.SenseHat.View
*) RPi.SenseHat.Tools
*) RT.IoT.Sensors

The Rpi.SenseHat is the main library. It contains a nice API to the Raspberry Sense HAT in C#.
The Rpi.SenseHat is dependent on the RT.IoT.Sensors project, which is a library for managing the sensor readings from the Sense HAT. That project is currently a copy of another github repository until no NuGet of it is available.

The RPi.SenseHat.Demo project is an application that you can run on the Raspberry Pi 2 || Pi 3. It doesn't utilize the regular UI, so there is no need to connect it to a monitor using the HDMI port.
The application comes with a number of views.
You must choose what demo to run by modifying the code in the "Selector" class. It should be fairly obvious what to do there. :-)


The RPi.SenseHat.Tools is a regular Windows console application that was used to test out some of the calculations that was needed in the actual library.
It also contains the process of converting a bitmap holding a font image into a "compiled" byte array that can be used by the font classes of the Sense HAT library.


************************
To get started:

*) Open the solution in Visual Studio 2017.

*) Make sure the "RPi.SenseHat.View" project is the start-up project.

*) Choose "ARM" as the solution platform.

*) Direct the debugging to a "Remote Machine" -- and make sure you enter the IP-address of your Raspberry Pi (and no authentication should be used).

*) Edit the Selector class (in the root of the "RPi.SenseHat.View" project) to select which view to run.

*) Run!


************************
Regarding thread safety:

The SenseHatFactory.Singleton.GetSenseHat() call is thread-safe, but the rest of the API is not.

It's deliberately not thread-safe to maximize performance, so you should avoid calling (for instance) the Update method on the sensors simultaneously from different threads (but you *may* call it from any thread).