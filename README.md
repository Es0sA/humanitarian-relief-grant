# Humanitarian Relief Grant — Elusive Button

A single-page, impossible-to-click confirmation portal disguised as an official relief grant disbursement interface. Built with vanilla HTML, CSS, and JavaScript using dynamic proximity detection and touch evasion physics.

## How it works

The page mimics a legitimate government or NGO disbursement portal with reference identifiers, status indicators, and an active countdown timer. When the user attempts to tap or hover over the confirmation button:

1. **Proximity detection**: An event listener monitors pointer coordinates and cursor speed across the document.
2. **Dynamic evasion**: When the pointer enters the proximity threshold, the button calculates the furthest safe coordinates within viewport bounds and transitions away before a click can register.
3. **Touch screen handling**: Touch events (`touchstart` and `pointerdown`) calculate the Euclidean distance to the button center and immediately reposition the element, preventing taps on mobile devices.
4. **Varied transformations**: Slight scaling and rotational transforms are applied on each repositioning to simulate erratic screen behavior.

## Features

- **90-second countdown timer**: Displays a session timer (`01:30`) that shifts to an alert state in the final 20 seconds.
- **Session expiration**: When the countdown reaches zero, the evasion loop locks down and displays a session timeout modal.
- **Session retry**: Clicking the retry button clears the expiration modal, resets the timer back to 90 seconds, and restores the button to its initial position in the card.
- **Self-contained**: Zero external dependencies, libraries, or build steps required.

## Deployment

The project consists of a single static `index.html` file and can be served by any static web server or hosting provider:

### Local Preview

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080` in your browser.

### Static Hosting

- **GitHub Pages**: Enable Pages under repository Settings -> Pages and point the source to `main` root.
- **Cloudflare Pages / Netlify / Vercel**: Deploy the repository root directly without build configurations.
