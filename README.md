

![Screenshot 2024-05-07 154624](https://github.com/ChessLogical/wsb/assets/169053333/4f0fe690-9259-43d0-b0b4-5f4019794e31)






Windows Sandbox is a lightweight desktop environment where you can run applications in isolation from your main system. It's a useful feature for safely running untrusted applications without risking your main system's health. This feature is available in Windows 10 Pro and Windows 11 Pro versions. Here’s how to secure the Windows Sandbox by creating a configuration file (with a .wsb extension) and running it:

Step-by-Step Guide to Securing Windows Sandbox:
1. Enable Windows Sandbox:

First, you need to enable Windows Sandbox since it's not turned on by default. To do this, open the Start menu and type "Turn Windows features on or off". Open the Windows Features dialog.Scroll down to find "Windows Sandbox", check the box next to it, and then click "OK". You'll need to restart your computer to complete the installation process.
 
2. Create a Windows Sandbox Configuration File (.wsb):

Configuration files for Windows Sandbox are written in XML format and have a .wsb file extension. They allow you to specify certain properties of the sandbox, like networking capabilities, shared folders, and startup scripts.
Open Notepad or any text editor. Here’s an example of a basic configuration file that shares a folder and disables networking:
xml :::::

<Configuration>
  <vGPU>Disable</vGPU>
  <Networking>Disable</Networking>
  <MappedFolders>
    <MappedFolder>
      <HostFolder>C:\Users\YourUsername\Documents\SafeFolder</HostFolder>
      <SandboxFolder>C:\Users\WDAGUtilityAccount\Desktop\SafeFolder</SandboxFolder>
      <ReadOnly>false</ReadOnly>
    </MappedFolder>
  </MappedFolders>
</Configuration>


This configuration disables GPU acceleration (<vGPU>Disable</vGPU>) and networking (<Networking>Disable</Networking>), which increases security by isolating the sandbox further from your main system.
It maps a host folder (C:\Users\YourUsername\Documents\SafeFolder) to a folder on the sandbox desktop. Adjust the HostFolder path to point to a folder on your main system that you want to access from the sandbox. The <ReadOnly> tag can be set to true if you want to prevent the sandbox environment from modifying the contents of the shared folder.
3. Save the Configuration File:

Save the file with a .wsb extension, for example, SecureSandbox.wsb, to a location where you can easily find it.
4. Run Your Configuration File:

Double-click the .wsb file you created. Windows Sandbox will start up with the configuration settings applied. The environment will reflect the settings you specified—no network access and with the specified folder mapped.
5. Closing Windows Sandbox:

When you're done, simply close the Windows Sandbox window. All contents and state are discarded and deleted. The next time you run the .wsb file, the sandbox will start afresh based on the specifications in your configuration file.

Using this method, you can customize and secure your Windows Sandbox environment tailored to specific tasks, enhancing your system's security when running potentially unsafe applications.






