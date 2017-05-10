﻿# Windows Application Driver (Beta)

Windows Application Driver is a service to support UI Test Automation of Windows Applications.  The service design subscribes to the Mobile JSON Wire Protocol standard.  If you've been looking for better support for using <a href="http://appium.io">Appium</a> to test Windows Applications then this service is for you!

This Github project provides
- documentation
- samples
- tests
- issue tracking

**Videos about WinAppDriver**<br/>
https://channel9.msdn.com/events/Connect/2016/202 (8min overview with demos)<br/>
https://channel9.msdn.com/events/Build/2016/Panel-Engineering-Quality (With Jonathan Lipps!)<br/>
https://channel9.msdn.com/events/Build/2016/P499 (Longer discussion)<br/>
https://www.youtube.com/watch?v=XAJVpvaEchY (c# demo with calculator sample walkthrough)<br/>

## Vote on New Features
Go to https://wpdev.uservoice.com/forums/110705-universal-windows-platform and enter requests under the **UI Testing** category.

## Getting Started
1. Download Windows Application Driver Installer here: https://github.com/Microsoft/WinAppDriver/releases
2. Run the Installer on the machine where you will run your test in (the application under test should also be installed on this machine)
3. Browse to the Windows Application Driver installation directory and run `WinAppDriver.exe`

When running `WinAppDriver.exe` a console window is opened which logs the JSON Wire Protocol HTTP requests

> Default listening address is 127.0.0.1:4723.  You can configure `WinAppDriver.exe` to listen to a different IP address and port if you run it as administrator. The syntax from the command line is:
WinAppDriver.exe *IP address* *port* For example:

	WinAppDriver.exe 127.0.0.1 4723
	WinAppDriver.exe 10.0.0.10 4725
	WinAppDriver.exe 10.0.0.10 4723/wd/hub


## Running on a Remote machine
1. On the machine you want to run the test application on, open up "Windows Firewall with Advanced Security"
	- Select "Inbound Rules" -> "New Rule"
	- Rule type -> port
	- Select TCP
	- Choose specific local port (4723 is WinAppDriver standard)
	- Action -> allow the connection
	- Profile -> select all
	- Name -> optional, choose name for rule (e.g. WinAppDriver remote) 
2. Run ipconfig to determine your machine's local IP address
	- Note that setting * as the IP address command line option will cause it to bind to all bound IP addresses on the machine
3. Run WinAppDriver.exe with command line arguments as seen above specifying local IP and port (must be in admin cmd)
4. On the machine with the test runner, make sure the URL in the test script is pointing to the IP of the remote machine
5. If the test app is installed on the remote machine run your test script and see the results!

## C# Samples
1. see Samples/C# in this github project. Take a look at https://www.youtube.com/watch?v=XAJVpvaEchY for a walkthrough of the c# calculator sample. Open one of the test solutions with Visual Studio 2015.  For example, pull and open `CalculatorTest.sln` under [CalculatorTest](https://github.com/Microsoft/WinAppDriver/tree/master/Samples/C%23/CalculatorTest)
2. In Visual Studio 2015 with the test solution open build the test and select **Test > Run > All Tests**
 
## Java Samples
1. see Samples/Java in this github project.  Open the sample folder as an existing project in a Java IDE such as IntelliJ. For example: [CalculatorTest](https://github.com/Microsoft/WinAppDriver/tree/master/Samples/Java/CalculatorTest)
2. In the Java IDE build and run the test

## Features
Windows Application Driver supports testing **Universal Windows Platform (UWP)** and **Classic Windows (Win32)** apps on **Windows 10 PC**

## Currently Supported APIs

| HTTP   	| Path                                              	|
|--------	|---------------------------------------------------	|
| GET    	| /status                                           	|
| POST   	| /session                                          	|
| GET    	| /sessions                                         	|
| DELETE 	| /session/:sessionId                               	|
| POST   	| /session/:sessionId/appium/app/launch             	|
| POST   	| /session/:sessionId/appium/app/close              	|
| POST   	| /session/:sessionId/back                          	|
| POST   	| /session/:sessionId/buttondown                    	|
| POST   	| /session/:sessionId/buttonup                      	|
| POST   	| /session/:sessionId/click                         	|
| POST   	| /session/:sessionId/doubleclick                   	|
| POST   	| /session/:sessionId/element                       	|
| POST   	| /session/:sessionId/elements                      	|
| POST   	| /session/:sessionId/element/active                	|
| GET    	| /session/:sessionId/element/:id/attribute/:name   	|
| POST   	| /session/:sessionId/element/:id/clear             	|
| POST   	| /session/:sessionId/element/:id/click             	|
| GET    	| /session/:sessionId/element/:id/displayed         	|
| GET    	| /session/:sessionId/element/:id/element           	|
| GET    	| /session/:sessionId/element/:id/elements          	|
| GET    	| /session/:sessionId/element/:id/enabled           	|
| GET    	| /session/:sessionId/element/:id/equals            	|
| GET    	| /session/:sessionId/element/:id/location          	|
| GET    	| /session/:sessionId/element/:id/location_in_view  	|
| GET    	| /session/:sessionId/element/:id/name              	|
| GET    	| /session/:sessionId/element/:id/screenshot        	|
| GET    	| /session/:sessionId/element/:id/selected          	|
| GET    	| /session/:sessionId/element/:id/size              	|
| GET    	| /session/:sessionId/element/:id/text              	|
| POST   	| /session/:sessionId/element/:id/value             	|
| POST   	| /session/:sessionId/forward                       	|
| POST   	| /session/:sessionId/keys                          	|
| GET    	| /session/:sessionId/location                      	|
| POST   	| /session/:sessionId/moveto                        	|
| GET    	| /session/:sessionId/orientation                   	|
| GET    	| /session/:sessionId/screenshot                    	|
| GET    	| /session/:sessionId/source                        	|
| POST   	| /session/:sessionId/timeouts                      	|
| POST   	| /session/:sessionId/timeouts/implicit_wait        	|
| GET    	| /session/:sessionId/title                         	|
| POST   	| /session/:sessionId/touch/click                   	|
| POST   	| /session/:sessionId/touch/doubleclick             	|
| POST   	| /session/:sessionId/touch/down                    	|
| POST   	| /session/:sessionId/touch/flick                   	|
| POST   	| /session/:sessionId/touch/longclick               	|
| POST   	| /session/:sessionId/touch/move                    	|
| POST   	| /session/:sessionId/touch/multi/perform           	|
| POST   	| /session/:sessionId/touch/scroll                  	|
| POST   	| /session/:sessionId/touch/up                      	|
| GET    	| /session/:sessionId/window                        	|
| DELETE 	| /session/:sessionId/window                        	|
| POST   	| /session/:sessionId/window                        	|
| GET    	| /session/:sessionId/window/handles                	|
| POST   	| /session/:sessionId/window/maximize               	|
| POST   	| /session/:sessionId/window/size                   	|
| GET    	| /session/:sessionId/window/size                   	|
| POST   	| /session/:sessionId/window/:windowHandle/size     	|
| GET    	| /session/:sessionId/window/:windowHandle/size     	|
| POST   	| /session/:sessionId/window/:windowHandle/position 	|
| GET    	| /session/:sessionId/window/:windowHandle/position 	|
| POST   	| /session/:sessionId/window/:windowHandle/maximize 	|
| GET    	| /session/:sessionId/window_handle                 	|
| GET    	| /session/:sessionId/window_handles                	|


## Creating Your Own Test Script
You can choose any programming language or tools supported by Appium/Selenium to write your test scripts. In the example below, we will author the test script in C# using Microsoft Visual Studio 2015.

### Create Test Project
1. Open **Microsoft Visual Studio 2015 or 2017** <br/>
  NOTE: in Visual Studio 2017 make sure you have the optional “.NET desktop development” workload installed
2. Create the test project and solution. I.e. select **New Project > Templates > Visual C# > Test > Unit Test Project**
3. Once created, select **Project > Manage NuGet Packages... > Browse** and search for **Appium.WebDriver**
4. Install the **Appium.WebDriver** NuGet packages for the test project
5. Starts writing your test (see sample code under [samples](https://github.com/Microsoft/WinAppDriver/tree/master/Samples))

### Universal Windows Platform App Testing

To test a UWP app, you can use any Selenium supported language and simply specify the **Application Id** for the app under test in the **app** capabilities entry. Below is an example of creating a test session for Windows **Alarms & Clock** app written in C#:

```c#
// Launch the AlarmClock app
DesiredCapabilities appCapabilities = new DesiredCapabilities();
appCapabilities.SetCapability("app", "Microsoft.WindowsAlarms_8wekyb3d8bbwe!App");
AlarmClockSession = new WindowsDriver<WindowsElement>(new Uri("http://127.0.0.1:4723"), appCapabilities);

// Control the AlarmClock app
AlarmClockSession.FindElementByAccessibilityId("AddAlarmButton").Click();
AlarmClockSession.FindElementByAccessibilityId("AlarmNameTextBox").Clear();
```

> When testing the application you authored yourself, you can find the **Application Id** in the generetated `AppX\vs.appxrecipe` file under `RegisteredUserModeAppID` node. E.g. ```c24c8163-548e-4b84-a466-530178fc0580_scyf5npe3hv32!App```

### Classic Windows App Testing

To test a classic Windows app, you can also use any Selenium supported language and specify the **full executable path** for the app under test in the **app** capabilities entry. Below is an example of creating a test session for Windows **Notepad** app:

```c#
// Launch Notepad
DesiredCapabilities appCapabilities = new DesiredCapabilities();
appCapabilities.SetCapability("app", @"C:\Windows\System32\notepad.exe");
NotepadSession = new WindowsDriver<WindowsElement>(new Uri("http://127.0.0.1:4723"), appCapabilities);

// Control the Notepad app
NotepadSession.FindElementByClassName("Edit").SendKeys("This is some text");
```

### Using Appium
WinAppDriver is integrated with Appium, meaning if you point your test at Appium then Appium will launch WinAppDriver and proxy the requests to WinAppDriver for you.

####A few details you should know
1. Appium will install WinAppDriver for you on Windows if you don't already have it.  Every release of Appium is linked to a specific release of WinAppDriver and will not proxy to a different version of WinAppDriver.  The easiest way to manage this is to let Appium install WinAppDriver for you.
2. To create multiple sessions with one Appium server you need Appium 1.6.4 or newer.  While 1.6.4 is not released to make sure you get this change you can install Appium via npm install appium@1.6.4-beta
3. When pointing a test at Appium you do need to include /wd/hub on the server URI.

For more details visit the Appium documentation:
http://appium.io/slate/en/master/?ruby#windows-application-ui-testing


### Inspecting UI Elements

Microsoft Visual Studio 2015 by default includes Windows SDK that provides great tool to inspect the application you are testing. This tool allows you to see every UI element/node that you can query using Windows Application Driver. This **inspect.exe** tool can be found under the Windows SDK folder such as `C:\Program Files (x86)\Windows Kits\10\bin\x86`

More detailed documentation on Inspect is available on MSDN <a href="https://msdn.microsoft.com/library/windows/desktop/dd318521(v=vs.85).aspx">here</a>.

The below table maps UI element attribues shown in Inspect to the matching WinAppDriver supported Client API.

| Client API                   	| Locator Strategy 	| Matched Attribute	                 	| Example      	|
|------------------------------	|------------------	|----------------------------------------	|--------------	|
| FindElementByAccessibilityId 	| accessibility id 	| AutomationId                           	| AppNameTitle 	|
| FindElementByClassName       	| class name       	| ClassName                              	| TextBlock    	|
| FindElementById              	| id               	| RuntimeId (decimal)                    	| 42.333896.3.1	|
| FindElementByName            	| name             	| Name                                   	| Calculator   	|
| FindElementByTagName         	| tag name         	| LocalizedControlType (upper camel case)	| Text         	|
