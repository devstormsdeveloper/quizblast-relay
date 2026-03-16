# QuizBlast Relay Server

Run this on any spare machine on the same local network to handle large numbers
of student connections — freeing up the teacher's Mac to focus on running the game.

## When to use this

- **Classroom / small events (up to ~1,000 students):** Not needed. The Mac handles it fine on its own.
- **Large events (1,000–5,000+ students):** Run the relay on a dedicated machine (Raspberry Pi, mini-PC, venue server, or any spare laptop) on the same network.

## Requirements

- No installs required — the relay is a self-contained standalone binary
- Same local network as the teacher's Mac

## Quick start

1. Download the zip for your platform from [GitHub Releases](https://github.com/devstormsdeveloper/quizblast-relay/releases/latest)
2. Unzip it
3. **Mac:** Double-click `Start Relay (Mac).command`
   **Windows:** Double-click `Start Relay (Windows).bat`
   **Linux / Raspberry Pi:** Run `./start-relay-linux.sh`
4. Enter the teacher's Mac IP address when prompted (shown in the QuizBlast lobby)
5. Leave the window open during your event

> **macOS note:** If macOS shows a security warning, go to System Settings → Privacy & Security and click "Allow Anyway", then run the launcher again.

## In the QuizBlast app

1. Open **Setup → Display** (Step 6)
2. Scroll to **Large Event Mode** and toggle it on
3. Enter this relay machine's IP address (shown in the relay terminal window)
4. Leave Controller Port as `8081` unless you changed it
5. Click **Connect** — the status badge turns green when ready
6. Students connect to the relay machine's IP on port `8080` (the QR code updates automatically)

## Uninstalling

- **Mac:** Double-click `Stop & Uninstall Relay (Mac).command`
- **Windows:** Double-click `Stop & Uninstall Relay (Windows).bat`
- **Linux / Pi:** Run `./stop-uninstall-relay-linux.sh`

## Capacity

The relay runs a self-benchmark on startup and prints a capacity grade so you
know what to expect before your event starts.

| Hardware | Approximate concurrent students |
|---|---|
| Raspberry Pi 5 | ~3,000 (Excellent) |
| Mac / PC laptop | ~3,000+ (Excellent) |
| Mac mini / NUC / Linux VM | 5,000–15,000+ |

## How it works

The relay proxies all student WebSocket traffic to the teacher's Mac.
The Mac still handles all game logic, scoring, and PIN validation —
the relay just offloads the connection handling for large crowds.
