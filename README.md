# FileDrop

Run it on ONE device (the host). Every other device joins by scanning a QR code or opening a link in its
normal browser - nothing to install on them. Then send files and text between any two devices.

## Start the host

| Host device | Command |
| --- | --- |
| Windows | double-click `filedrop-windows-amd64.exe` (allow it through the firewall on *Private* networks) |
| Linux | `chmod +x filedrop-linux-amd64 && ./filedrop-linux-amd64` |
| Android (Termux) | copy `filedrop-linux-arm64-termux-android` into Termux's home folder (not /sdcard), then `chmod +x filedrop-linux-arm64-termux-android && ./filedrop-linux-arm64-termux-android --no-open` then open the host link in the browser|
| Mac | `chmod +x filedrop-macos-apple-silicon && ./filedrop-macos-apple-silicon` |

The terminal prints a QR code and an invite link; the host's own UI opens in its browser
(on Termux, open the printed `http://127.0.0.1:8080/?k=...` link in your phone browser).

## Join

1. Other device (same Wi-Fi / hotspot): scan the QR code or open the link.
2. Browser warns about the self-signed certificate (once) -> Advanced -> Proceed.
3. Host taps **Allow**.
4. Pick a device, drop files (or send text). The receiver taps **Accept**; the file streams straight into
   their browser's Downloads folder.

## Options

`--port 8443` `--local-port 8080` `--ip 192.168.1.20` (if auto-detect picks the wrong address) `--name MyPC` `--no-open`

## Build from source

`go build -trimpath -ldflags="-s -w" -o filedrop .`  (Go 1.22+; source is in `source/`)
