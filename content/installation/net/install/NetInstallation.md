<!--
title: "Contrast .NET Agent Installation"
description: "Contrast .NET Agent Installation."
tags: "installation agent .NET"
-->


To install the .NET agent, complete the following steps:

* Log in to the Contrast interface. 
* Click the button in the top navigation bar to **Add Agent**.
* Select the **.NET Agent** in the dropdown menu, and click the button to **Download Agent**. You might need to specify proxy authentication information required by your network before downloading the agent.
* Extract the downloaded zip archive (e.g., *ContrastSetup_3.3.5.zip*) on the web server, and run *ContrastSetup.exe*. This installs the .NET agent. 

## Silent Installation

The .NET agent installer supports the command line options below. These options are silent, which means that they don't require your interaction and don't present the installer's user interface.

* Install: `ContrastSetup.exe -s -norestart`

* Install and Do Not Start the Contrast.NET Tray Application: `ContrastSetup.exe -s -norestart StartTray=0`

* Uninstall: `ContrastSetup.exe -uninstall -s -norestart`

* Repair: `ContrastSetup.exe -s -repair`


## Changes Made by the Agent Installer

Many users are curious about the changes made by the Contrast .NET agent and what impacts these changes may have. In all respects, the Contrast .NET agent installer is a normal Windows application installer built using standard MSI technology. The Contrast .NET agent installer validates that the target server satisfies several requirements (e.g., the operating system is Windows Server 2008 R2 or greater). If all requirements are met, the installer registers the .NET agent as a standard Windows program and makes the following changes:

- Places the agent’s files on a disk in the specified install location (e.g., *C:\ProgramFiles\Contrast.NET*). This includes several dynamic link library (DLLs) and executables, such as the background Windows service that drives agent behavior. 
- Creates the specified data directory for the agent that is primarily used to store agent log files (e.g., *C:\ProgramData\Contrast.NET*). 
- Registers the agent’s background Window service with the operating system.
- Reads the *DotnetAgentSettings.ini* file to customize the agent’s configuration file with details necessary to communicate with the Contrast application (e.g., API key).
- Registers several agent assemblies with the .NET global assembly cache so they can be loaded by instrumented applications.
- Starts the agent’s background Windows service and Tray (UI) application. This service has a number of responsibilities: 
  - Preparing the environment for instrumentation by registering the agent’s profiler component with IIS through environment variables and restarting IIS. This causes the CLR to load the agent’s profiler, which is responsible for instrumenting analyzed applications. 
  - Communication with the Contrast interface.
  - Communication with Profiler and Sensor components through local named pipes. 

## Next Steps

* [Use the Contrast .NET agent](installation-netusage.html#usage)  
* [Customize .NET agent configuration](installation-netconfig.html)  
