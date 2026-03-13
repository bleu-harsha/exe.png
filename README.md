# exe.png
![image](https://github.com/user-attachments/assets/72cf7802-afba-4387-884e-898123e1f06f)

this is a exe that is disguised as a png to run things. currently the code does almost no harmful tasks and is not associated to webhook and other things(yet)

## how does this work?

This C program quietly gathers some basic diagnostic info about the PC it's running on — like your public IP, user account, OS details, running tasks, and network status — then writes it all to a log file in your %TEMP% directory. Think of it like a mini system snapshot, just in batch form.

But here's the cool part:
It hides the console window, creates a temporary .bat file on the fly, fills it with all those sweet Windows command-line instructions, and then runs that batch script automatically — all from C.(currently work in progress)


- i try to hide ahh code:
First thing it does is hide its own console window (ShowWindow(hWnd, SW_HIDE)), so the user won’t even see it running.

- storing the log file in temp in temp:
It grabs the %TEMP% folder path and uses that to create a new batch file there (temp_script.bat).

- fetch local time and start displaying the output one by one to the log in file in temp
It logs the current date and time into a text file named pnglogfile.txt, also in the temp directory. This becomes your logbook.

- get the ip and network and store it in the log file:
It pulls your public IP using OpenDNS (classic trick), and logs info about your current Wi-Fi setup using netsh.

- get theuser info and store it in the log file:
It logs your username (whoami) and checks if you're an admin by looking for a specific group ID (S-1-5-32-544).

- get the systeminfo and store it in the log file:
A quick peek at the OS name and version using systeminfo.

- get the task list and store it in the log file:
It dumps the current running tasks using tasklist.

## features

  * [x] Hidden Console Execution
    Uses the Windows API to suppress the command prompt window, ensuring the process runs silently in the background.

  * [x] Temporary File Handling
     Automatically locates the system %TEMP% directory and manages lifecycle operations for dynamic scripts.

  * [x] User Identification
     Retains context by identifying the currently logged-in Windows user via whoami for personalized execution.
     
  * [x] Automated Script Execution
    Generates batch files dynamically and executes them via cmd /c for high-speed task deployment.

  * [ ] Remote Audio Control
    Remotely adjust system volume levels or trigger specific audio files/frequencies on the host device.

  * [ ] Wallpaper Manipulation
     Programmatically switch the desktop background to any image URL or local path.

  * [ ] Dynamic Jumpscare Trigger
     Execute a full-screen visual/auditory "scare" either on a randomized timer or via a remote manual trigger.

  * [ ] Authenticated Remote Access (C2)
     Establish a persistent connection to the target machine using a unique Secret Key system, allowing for remote command execution through a secure handshake.

  * [ ] Stealth Remote Desktop
     Gain visual control of the desktop environment while utilizing obfuscation techniques to minimize detection by heuristic analysis.

## how do i make the .exe to disguise itself as png

refer [this](https://www.youtube.com/watch?v=cXEkSQl9wmw&list=LL&index=34&t=26s) video for more info
the logfile of all the data will be present in your local %temp% env to find yours.


>[!NOTE]
>This project is created for educational purposes only. 
>Any actions taken using this project are the sole responsibility of the user. 
>The author assumes no liability for misuse or damages caused by this project.


