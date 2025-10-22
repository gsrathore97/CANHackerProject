1. arduino-canhacker-master.zip, arduino-mcp2515-master.zip Add these zip library
2. CanHackerCodesketch_jun13a Upload Arduino code 
3. CANHackerV2.00.01.exe Install application  
4. En_EP_CAN_Protocol.pdf Protocol use your actual












1) Add the two ZIP libraries to Arduino IDE (Windows / macOS / Linux)

Method A — Using Arduino IDE (recommended, works for .zip without extracting)

Open Arduino IDE (1.8.x or 2.x).

Menu → Sketch → Include Library → Add .ZIP Library...

Browse to arduino-canhacker-master.zip → Open.

Repeat for arduino-mcp2515-master.zip.

Restart Arduino IDE.

Verify: Sketch → Include Library → Contributed libraries — you should see the two libraries listed.

Method B — Manual install (if Add .ZIP fails)

Unzip each archive. You should get folders like arduino-canhacker-master and arduino-mcp2515-master.

Rename them if needed so the main folder is the library name (e.g. CANHacker or MCP2515) — the folder should contain library.properties or a .h/.cpp pair at top level.

Move each folder to your Arduino libraries folder:

Windows: C:\Users\<your-username>\Documents\Arduino\libraries\

macOS: ~/Documents/Arduino/libraries/

Linux: ~/Arduino/libraries/

Restart Arduino IDE. Confirm under Sketch → Include Library.

2) Load the Arduino sketch CanHackerCodesketch_jun13a (Arduino code)

If the sketch is a .ino file or a folder named CanHackerCodesketch_jun13a:

If archived, unzip it so you have a folder like CanHackerCodesketch_jun13a that contains .ino (and maybe .cpp/.h). Place that folder into your sketches folder:

Windows: C:\Users\<you>\Documents\Arduino\CanHackerCodesketch_jun13a\CanHackerCodesketch_jun13a.ino

Open Arduino IDE → File → Open... and choose the .ino.

Select board & port: Tools → Board (e.g. Arduino Uno, Mega, ESP32, etc.) and Tools → Port.

Make sure the board you select matches the hardware you will flash.

Compile: click Verify (✔). If you see missing header/library errors, confirm the two libraries were installed correctly.

Upload to board when ready.

Common includes to check inside the sketch

The sketch likely references MCP2515 or CANHacker library headers, e.g.:

#include <mcp2515.h>        // from arduino-mcp2515-master
#include <CANHacker.h>      // or whatever header the CanHacker lib provides


If compile fails, copy the exact error and I can help debug.

3) CANHackerV2.00.01.exe — Windows application installation

Scan the file first with your antivirus and, if you want extra caution, upload to VirusTotal before running. (Always advisable with unknown EXEs.)

Right-click → Run as administrator (if it requires drivers or writes to Program Files).

Follow installer prompts. The installer may add start menu shortcuts and drivers (if it interfaces with hardware).

If the app communicates with a USB CAN adapter, ensure drivers are installed and the adapter shows in Device Manager (Windows).

If the installer fails or is blocked:

Temporarily disable SmartScreen or unblock the file (right-click Properties → Unblock), but re-enable protection after.

Run installer as admin, or check compatibility mode.

Note / safety: unsigned executables may trigger warnings. If you don’t trust the source, don’t run it — or run inside a sandbox/VM.

4) En_EP_CAN_Protocol.pdf — view or reference

Open with your preferred PDF reader (Adobe Reader, Edge, Preview on macOS).

If you want to extract details relevant to the sketch or libraries (e.g., CAN frame formats, message IDs, baud rates), search inside the PDF (Ctrl+F) for keywords like baud, ID, 0x, frame, data length, J1939, ISO-15765, etc.

If you want, copy the relevant sections (or screenshots) and paste them here — I can help translate PDF protocol specs into Arduino code (parsing CAN frames, building messages, filters, etc.).

Tips & Troubleshooting

Missing library errors after adding zip → restart IDE. If still failing, ensure the folder structure is libraries/LibraryName/src or libraries/LibraryName/*.h (older libraries may put sources at top level).

Multiple versions: If a library name conflicts with an existing library, delete the older one from Documents/Arduino/libraries or use Library Manager to manage versions.

MCP2515 hardware: It uses SPI — ensure correct pins and SPI included. Typical code uses mcp2515 object and CAN functions; check the library examples after installation: File → Examples → (LibraryName).

CAN bus baud rate: Make sure the sketch and your bus share the same speed (125k, 250k, 500k, etc.). Wrong baud rate → no frames.

If EXE is a GUI for interacting with hardware: run it after the library/sketch is working so you can cross-check frames between PC app and Arduino.
