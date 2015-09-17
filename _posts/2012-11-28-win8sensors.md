---
layout: post
title: Rocking the Windows 8 Sensors on the Intel IvyBridge Ultrabook
date: 2012-11-28 04:12
author: John
comments: true
categories: [pluralsight, review, ultrabook, Uncategorized, windows 8]
---
<p style="text-align: left;">The combination of good sensors and simplicity of tapping into the Windows 8 sensor APIs are really going to open the doors to some great apps. In this final review I'll touch on the core sensors, how they fared, and how to tap into each of them.</p>
<p style="text-align: left;">I've received a few pieces of hardware and software over the years for review purposes. Unfortunately, some of the hardware I receive falls far short of my expectations and hardly ever gets used again. This is definitely not the case with the Intel IvyBridge Ultrabook running Windows 8 Pro that I received. My experience with it over that time has left me extremely impressed for speed, portability, touch and a broad array of sensors.</p>
<img class="size-large wp-image-9941 aligncenter" title="win8" src="http://www.johnpapa.net/wp-content/uploads/2012/11/win8-600x337.png" alt="" width="600" height="337" />
<blockquote>From what I can tell, the machine itself is not one that we'll see in stores,  but instead its simply just a model Intel used as a sample to show what OEM’s can create for Windows 8. Mine is not branded and has stickers all over its bottom saying that its not for retail. However, the Intel components inside this device will be showing up in devices you can purchase.</blockquote>
You can read <a href="http://www.johnpapa.net/first-look-at-3rd-generation-intel-ivy-bridge-ultrabook/">my initial impressions of the IvyBridge Ultrabook here</a> and my <a href="http://www.johnpapa.net/intel-ivybridge-ultrabook-sensors/" target="_blank">follow up on my 2 week reaction here</a>. This ultrabook is easily portable and has many ports built in so I do not need a ton of dongles. That's key when you travel and present like me. I can easily slip it into my bag and carry it around for presentations and get a lot of work done on it.

It's fast. I live in Visual Studio 2012 and several other development tools. Speed and power are not "nice to have" for me; they are essentials. This ultrabook covers those areas despite its lower RAM and CPU than I usually get. I like an i7 but I admit with this ultrabook the i5 has been more than enough (perhaps its Windows 8 and its claimed efficiency or perhaps its just the super fast 180 GB SSD). Whatever it is, I'm very happy with the speed of this IvyBridge ultrabook.

In October I used this device to test some <a href="http://pluralsight.com/training/Courses/TableOfContents/win8-intro" target="_blank">Windows 8 course material</a> <a href="http://twitter.com/danwahlin" target="_blank">Dan Wahlin</a> and I authored for <a href="http://pluralsight.com" target="_blank">Pluralsight</a>. I was using quite a bit at the same time including Visual Studio 2012, Powerpoint, and OneNote. It all went very smooth on this device. You can learn more about this Introduction to Windows 8 course by clicking the image below.

<a href="http://pluralsight.com/training/Courses/TableOfContents/win8-intro" target="_blank"><img class="aligncenter" title="Win8Course" src="http://www.johnpapa.net/wp-content/uploads/2012/10/10-11-2012-5-54-58-PM.png" alt="" width="500" height="85" /></a>
<h2>Sensors</h2>
Windows 8 exposes a variety of APIs to access the device sensors. The Windows team made several examples available so you can test the sensors. You can find APIs for sensors including (but not limited to) these APIs:
<ul>
	<li>Accelerometer ( acceleration along 3 axes)</li>
	<li>Compass (orientation and position)</li>
	<li>Gyrometer (angular velocity)</li>
	<li>Inclinometer (angle of incline)</li>
	<li>LightSensor (ambient lighting)</li>
	<li>OrientationSensor (combines accelerometer, compass, gyrometer to get more sensitive movement)</li>
	<li>SimpleOrientation (orientation of the device including face up or down)</li>
</ul>
I tested the sensors using these sample apps.
<blockquote>All code samples below are directly from the <a href="http://code.msdn.microsoft.com/windowsapps/Windows-8-Modern-Style-App-Samples/view/SamplePack#content" target="_blank">Windows 8 Sample Apps that you can download from this link</a>.</blockquote>
<h2>Accelerometer</h2>
<div>Apps should understand motion and screen rotation, which requires an accelerometer. The accelerometer measures the force due to gravity, and the motion of the device itself. The accelerometer sensor tracks the acceleration along 3 axes (x,y, and z).  The sample app "Accelerometer sensor sample" tracks the acceleration values as they are reported to the sensors and also is useful for tracking when the device has been shaken. In my tests the sample app reported back the acceleration and the shakes immediately, and as expected.</div>
<div>So how easy is this? Quite simple actually. First you have to grab a reference to the sensor API. This is where you see the Accelerometer.GetDefault() in the code below. Then a simple null check determines if the you can access the sensor and its data. The sample grabs the minimum reporting interval that the sensor supports (which determines the frequency/interval of when the sensor reports its data).</div>
<pre class="prettyprint linenums">private Accelerometer _accelerometer;
private uint _desiredReportInterval;

public Scenario1()
{
    this.InitializeComponent();

    _accelerometer = Accelerometer.GetDefault();
    if (_accelerometer != null)
    {
        // Select a report interval that is both suitable for the purposes of the app and supported by the sensor.
        // This value will be used later to activate the sensor.
        uint minReportInterval = _accelerometer.MinimumReportInterval;
        _desiredReportInterval = minReportInterval &gt; 16 ? minReportInterval : 16;
    }
    else
    {
        rootPage.NotifyUser("No accelerometer found", NotifyType.StatusMessage);
    }
}</pre>
<div>Now that we have a handle to the accelerometer sensor, we can wire up an event handler to capture the data.</div>
<pre class="prettyprint">_accelerometer.ReadingChanged += 
    new TypedEventHandler<Accelerometer, AccelerometerReadingChangedEventArgs>(ReadingChanged);</pre>
<div>Then grabbing the data is as simple as reading the AccelerometerReading object in the event arguments(using an async handler). The data is pushed to the screen's TextBlocks one by one.</div>
<pre class="prettyprint linenums">async private void ReadingChanged(object sender, AccelerometerReadingChangedEventArgs e)
{
    await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =&gt;
    {
        AccelerometerReading reading = e.Reading;
        ScenarioOutput_X.Text = String.Format("{0,5:0.00}", reading.AccelerationX);
        ScenarioOutput_Y.Text = String.Format("{0,5:0.00}", reading.AccelerationY);
        ScenarioOutput_Z.Text = String.Format("{0,5:0.00}", reading.AccelerationZ);
    });
}</pre>
<div>We can also check if the device was shaken by wiring up an event handler.</div>
<pre class="prettyprint">_accelerometer.Shaken += 
    new TypedEventHandler<Accelerometer, AccelerometerShakenEventArgs>(Shaken);</pre>
<div>The number of shakes can be retrieved with a simple counter as shown below (from the same sample in Scenario 2).</div>
<pre class="prettyprint linenums">async private void Shaken(object sender, AccelerometerShakenEventArgs e)
{
    await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =&gt;
    {
        _shakeCount++;
        ScenarioOutputText.Text = _shakeCount.ToString();
    });
}</pre>
<h2>Compass</h2>
<div>The compass sensor reports back information on the orientation and position of the device. The sensors on the Intel IvyBridge Ultrabook detected the position using the compass very well when measured against other compasses I had available to me. You can use the Windows 8 sample app "Compass sensor sample" to detect the direction (north, south, east, west) measured in degrees. First you grab the compass object.</div>
<pre class="prettyprint">private Compass _compass;</pre>
<div>Then wire up an event handler</div>
<pre class="prettyprint">_compass.ReadingChanged += 
    new TypedEventHandler(ReadingChanged);</pre>
<div>Grab the reading in the event handler and display the position in degrees.</div>
<pre class="prettyprint">CompassReading reading = e.Reading;
ScenarioOutput_MagneticNorth.Text = String.Format("{0,5:0.00}", reading.HeadingMagneticNorth);</pre>
<h2>Gyrometer</h2>
<div>The Gyrometer sensor measures angular speed along 3 axes. The gyrometer on the Intel IvyBridge Ultrabook device proved to be very sensitive (a good thing) and when used in combination with other sensors such as a compass, it can be quite useful in motion and position sensing systems (think gaming). You can test the gyro using the "Gyrometer sensor sample". First grab the Gyrometer object</div>
<pre class="prettyprint">private Gyrometer _gyrometer;</pre>
<div>Then wire up the event handler</div>
<pre class="prettyprint">_gyrometer.ReadingChanged += 
    new TypedEventHandler(ReadingChanged);</pre>
<div>Finally, read the angular velocity data inside the event handler.</div>
<pre class="prettyprint linenums">async private void ReadingChanged(object sender, GyrometerReadingChangedEventArgs e)
{
    await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =&gt;
    {
        GyrometerReading reading = e.Reading;
        ScenarioOutput_X.Text = String.Format("{0,5:0.00}", reading.AngularVelocityX);
        ScenarioOutput_Y.Text = String.Format("{0,5:0.00}", reading.AngularVelocityY);
        ScenarioOutput_Z.Text = String.Format("{0,5:0.00}", reading.AngularVelocityZ);
    });
}</pre>
<h2>Inclinometer</h2>
<div>The inclinometer measures the angle of incline exposing the yaw, pitch, and roll readings from the device. The yaw is the z rotation, the roll is the y rotation, and the pitch is the x rotation of the device. I tapped into these APIs using the Windows 8 sample "Inclinometer sensor sample". Again, the Intel IvyBridge Ultrabook's sensors performed quite well reporting back the inclinometer readings. You can tap into this API following the familiar pattern I showed with the other APIs. First grab the Inclinometer object</div>
<pre class="prettyprint">private Inclinometer _inclinometer;</pre>
<div>Then wire up the event handler</div>
<pre class="prettyprint">_inclinometer.ReadingChanged += 
    new TypedEventHandler(ReadingChanged);</pre>
<div>Finally, read the yaw, pitch and roll data inside the event handler.</div>
<pre class="prettyprint linenums">async private void ReadingChanged(object sender, InclinometerReadingChangedEventArgs e)
{
    await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =&gt;
    {
        InclinometerReading reading = e.Reading;
        ScenarioOutput_X.Text = String.Format("{0,5:0.00}", reading.PitchDegrees);
        ScenarioOutput_Y.Text = String.Format("{0,5:0.00}", reading.RollDegrees);
        ScenarioOutput_Z.Text = String.Format("{0,5:0.00}", reading.YawDegrees);
    });
}</pre>
<h2>LightSensor</h2>
<div>The Intel IvyBridge device has an ambient light sensor that reports the brightness level. This can be used for various purposes including adjusting the display's brightness in a room with changing light. I tested this in a dark room, bright room, indoor and outdoor, and by moving a bright lightsource (desk lamp) near the Ultrabook. The sensor reported bacl consistent and expected data for all tests I ran.</div>
<div>Tapping into the light sensor is as easy as grabbing the LightSensor object (notice this sensor has the suffix "sensor" while the previous sensor APIs I mentioned do not). You can see this for yourself in the Windows 8 sample titled "LightSensor sample".</div>
<pre class="prettyprint">private LightSensor _sensor;</pre>
<div>Then wire up the event handler</div>
<pre class="prettyprint">_sensor.ReadingChanged += 
    new TypedEventHandler(ReadingChanged);</pre>
<div>Finally, read the illumination data (in lux) inside the event handler.</div>
<pre class="prettyprint linenums">async private void ReadingChanged(object sender, LightSensorReadingChangedEventArgs e)
{
    await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =&gt;
    {
        LightSensorReading reading = e.Reading;
        ScenarioOutput_LUX.Text = String.Format("{0,5:0.00}", reading.IlluminanceInLux);
    });
}</pre>
<h2>OrientationSensor</h2>
<div>The OrientationSensor combines the accelerometer, compass, and gyrometer to report even more sensitive movement than the sensors can on their own. You could use this to orient an image on the screen by reading the device orientation, the screen orientation and the accelerometer, for example.</div>
<div><a href="http://www.johnpapa.net/win8sensors/orientation/" rel="attachment wp-att-10161"><img class="aligncenter size-large wp-image-10161" title="orientation" src="http://www.johnpapa.net/wp-content/uploads/2012/11/orientation-600x337.png" alt="" width="600" height="337" /></a></div>
<div></div>
<div>First grab the OrientationSensor object</div>
<pre class="prettyprint">private OrientationSensor _sensor;</pre>
<div>Then wire up the event handler</div>
<pre class="prettyprint">_sensor.ReadingChanged += 
    new TypedEventHandler(ReadingChanged);</pre>
<div>Then read the OrientationSensorReading object's data inside the event handler.</div>
<pre class="prettyprint linenums">async private void ReadingChanged(object sender, OrientationSensorReadingChangedEventArgs e)
{
    await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =&gt;
    {
        OrientationSensorReading reading = e.Reading;

        // Quaternion values
        SensorQuaternion quaternion = reading.Quaternion;   // get a reference to the object to avoid re-creating it for each access
        ScenarioOutput_X.Text = String.Format("{0,8:0.00000}", quaternion.X);
        ScenarioOutput_Y.Text = String.Format("{0,8:0.00000}", quaternion.Y);
        ScenarioOutput_Z.Text = String.Format("{0,8:0.00000}", quaternion.Z);
        ScenarioOutput_W.Text = String.Format("{0,8:0.00000}", quaternion.W);

        // Rotation Matrix values
        SensorRotationMatrix rotationMatrix = reading.RotationMatrix;
        ScenarioOutput_M11.Text = String.Format("{0,8:0.00000}", rotationMatrix.M11);
        ScenarioOutput_M12.Text = String.Format("{0,8:0.00000}", rotationMatrix.M12);
        ScenarioOutput_M13.Text = String.Format("{0,8:0.00000}", rotationMatrix.M13);
        ScenarioOutput_M21.Text = String.Format("{0,8:0.00000}", rotationMatrix.M21);
        ScenarioOutput_M22.Text = String.Format("{0,8:0.00000}", rotationMatrix.M22);
        ScenarioOutput_M23.Text = String.Format("{0,8:0.00000}", rotationMatrix.M23);
        ScenarioOutput_M31.Text = String.Format("{0,8:0.00000}", rotationMatrix.M31);
        ScenarioOutput_M32.Text = String.Format("{0,8:0.00000}", rotationMatrix.M32);
        ScenarioOutput_M33.Text = String.Format("{0,8:0.00000}", rotationMatrix.M33);
    });
}</pre>
<h2>Wrap Up</h2>
<div>The Windows 8 sensor APIs make it easy to tap into device sensors. This makes it critical that the device implements the sensors and reports back the data at a tight interval and accurately. I found the Intel IvyBridge Ultrabook device that I tested to have fare very well with all of these sensors. I'm excited to see what types of apps we will see that take advantage of these sensors and Windows 8.</div>
<blockquote>Disclosure of Material Connection: I received one or more of the products or services mentioned above for free in the hope that I would mention it on my blog. Regardless, I only recommend products or services I use personally and believe my readers will enjoy. I am disclosing this in accordance with the <a href="http://www.gpo.gov/fdsys/pkg/CFR-2003-title16-vol1/content-detail.html">Federal Trade Commission’s 16 CFR, Part 255: “Guides Concerning the Use of Endorsements and Testimonials in Advertising</a>.”</blockquote>
