# MotionCanvas

A gesture-based creative drawing tool for adults with motor differences, built using Ultraleap hand tracking and p5.js.

## About

MotionCanvas treats movement as the creative material itself. Every existing drawing tool corrects movement toward a standard - MotionCanvas calibrates to the user's individual range and translates involuntary movement into expressive mark-making rather than suppressing it.

**Target users:** Adults with motor differences - tremor, cerebral palsy, limited range, MS - who have creative intent but have always had tools that fight their movement. This is not a rehabilitation project. It is about personal creative making.

**Three core contributions:**
- **Adaptive calibration** - the system maps to the user's actual movement range, not a default
- **Tremor reframing** - high-frequency low-displacement movement is translated into cross-hatch texture rather than treated as error
- **Contact-free input** - Leap Motion removes grip strength, surface contact, and pressure threshold requirements

The project applies Wobbrock et al.'s (2011) ability-based design principle - the system adapts to the user, not the user to the system - and draws on Hendren's (2020) argument that disability is a design problem, not a personal limitation.

## Group Members

- Ammal Samatar
- Breanna Gordon
- Katie Chen

DPR

## Technology

- [Ultraleap Gemini](https://leap2.ultraleap.com/downloads/leap-motion-controller-2/) - hand tracking driver
- Leap Motion WebSocket API - `ws://localhost:6437/v7.json`
- p5.js - canvas rendering, brush modes, animation loop
- HTML5 / JavaScript - no build step required, runs in browser

## Folder Structure

```
code/
  iteration1/        HTML5 Canvas proof of concept
  iteration2/        Full p5.js rebuild with onboarding, calibration, tremor detection
  iteration3/        Refined interaction - undo, success states, improved labelling
  demos/             Tremor comparison demo (split-screen raw vs reframed)

design/              Moodboard, storyboard, system overview diagram

evaluation/          Heuristic evaluation notes and cognitive walkthrough (HTML + PDF)
                     references.html - full 14-source reference list

meeting-logs/        Meeting logs 01-08 (HTML, print-to-PDF ready)

sketches/            flowcharts.html - design process and system diagrams

videos/              Iteration screen recordings

genai-declaration/   GenAI group reflection and AI assistance log

group-reflection/    Individual and group reflection documents
```

## Key Files

| File | Description |
|------|-------------|
| `code/iteration3/index.html` | Latest prototype - open this in browser to run |
| `code/iteration2/index.html` | Iteration 2 - full p5.js rebuild |
| `code/demos/tremor-comparison.html` | Side-by-side tremor reframe demonstration |
| `evaluation/references.html` | Full 14-source reference list |
| `sketches/flowcharts.html` | Design process and system diagrams |
| `meeting-logs/meeting-08.html` | Most recent meeting log |

## How to Run

**Step 1 - Install Ultraleap Gemini**

Download from: https://leap2.ultraleap.com/downloads/leap-motion-controller-2/

Install it, plug in the Leap Motion via USB, and you should see a small hand icon in your system tray (Windows) or menu bar (Mac). When you hover over it it should say "Tracking" with a green indicator. If it says "Device not connected" unplug and replug the USB.

**Step 2 - Enable WebSocket API**

Open the Ultraleap control panel and look for a setting called "Allow Web Apps" or "WebSocket Server" - make sure it is turned on. Without this the browser cannot receive hand data even if tracking is working.

**Step 3 - Open in browser**

Open `code/iteration3/index.html` with VS Code Live Server or drag it into Chrome. Chrome works best - Firefox sometimes has issues with the WebSocket connection.

The prototype also runs fully in mouse mode with no sensor required. Mouse mode is selected by default and all features including tremor simulation are available without Leap Motion.

---

**Troubleshooting Leap connection**

If the Leap toggle turns on but the dot stays grey and no drawing happens, the WebSocket connection failed. Common causes in order:

1. Ultraleap software is not running - check system tray
2. WebSocket API is not enabled in Ultraleap settings - check control panel
3. Wrong port - the code uses `6437`, confirm this matches your Ultraleap control panel
4. Browser blocked the connection - try Chrome if on Firefox or Safari
5. Firewall blocking localhost WebSocket - may need IT to allow it on university machines

Open the browser console (F12) and you will see either "Leap Motion connected" or an error message identifying which of these applies.


