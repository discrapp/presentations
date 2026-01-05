# GIF Recording Runbook

This guide covers how to record high-quality GIFs from a physical iPhone for
use in presentations and the web landing page.

## Prerequisites

Install required tools:

```bash
brew install ffmpeg gifsicle
```

## GIFs Needed for Investor Pitch

### 1. QR Scan Flow

**File:** `public/images/qr-scan-flow.gif`
**Duration:** ~8-10 seconds
**Shows:** Complete found disc flow via QR code

**Steps to record:**

1. Open the app to the "Found Disc" tab
1. Have a test QR code ready (printed or on another device)
1. Start recording
1. Tap "Scan QR Code"
1. Point camera at QR code and scan
1. Show the disc info that appears
1. Tap "Report Found"
1. Show success confirmation
1. Stop recording

---

### 2. AI Disc Identification

**File:** `public/images/ai-disc-id.gif`
**Duration:** ~6-8 seconds
**Shows:** AI identifying a disc from a photo

**Steps to record:**

1. Open the app to the "My Bag" tab
1. Have a real disc ready to photograph
1. Start recording
1. Tap "Add Disc"
1. Tap "AI Identify" or camera icon
1. Take photo of the disc
1. Show AI processing indicator
1. Show results with manufacturer, mold, flight numbers
1. Stop recording

---

### 3. Recovery Coordination Flow

**File:** `public/images/recovery-flow.gif`
**Duration:** ~10-12 seconds
**Shows:** Owner receiving notification and coordinating meetup

**Steps to record:**

1. Set up a test scenario where you'll receive a "disc found" notification
1. Start recording from lock screen or home screen
1. Show push notification appearing
1. Tap notification to open app
1. Show recovery details screen
1. Tap "Propose Meetup"
1. Show meetup scheduling interface
1. Stop recording

---

### 4. Visual Disc Recovery (Phone Number)

**File:** `public/images/visual-recovery.gif`
**Duration:** ~8-10 seconds
**Shows:** New feature - recovering disc via phone number photo

**Steps to record:**

1. Open the app to "Found Disc" tab
1. Have a disc with a phone number written on the back
1. Start recording
1. Tap "Use Phone Number on Disc"
1. Take photo of disc back (with phone number visible)
1. Take photo of disc front
1. Show AI extracting phone number
1. Show owner lookup results
1. Stop recording

---

### 5. Disc Inventory / My Bag

**File:** `public/images/my-bag.gif`
**Duration:** ~5-7 seconds
**Shows:** Scrolling through disc collection

**Steps to record:**

1. Ensure test account has 5-10 discs with photos
1. Open "My Bag" tab
1. Start recording
1. Scroll through the disc collection slowly
1. Tap on one disc to show details
1. Show flight numbers and disc info
1. Stop recording

---

## Recording from Physical iPhone

All GIFs should be recorded on a physical iPhone for consistency and to enable
camera-based features (QR scanning, AI identification).

### Method 1: iPhone Screen Recording (Simplest)

**Setup:**

1. Go to Settings > Control Center
1. Add "Screen Recording" if not already there

**Recording:**

1. Open Control Center (swipe down from top-right)
1. Long-press the Screen Recording button
1. Tap the microphone icon to turn OFF audio (smaller file)
1. Tap "Start Recording"
1. Wait for 3-second countdown
1. Perform the demo
1. Tap the red status bar at top and confirm to stop
1. Video saves to Photos app

**Transfer to Mac:**

- AirDrop the video to your Mac, or
- Use iCloud Photos, or
- Connect via USB and import via Image Capture

---

### Method 2: QuickTime Recording (Higher Quality)

**Setup:**

1. Connect iPhone to Mac via USB cable
1. Trust the computer on iPhone if prompted
1. Open QuickTime Player on Mac

**Recording:**

1. File > New Movie Recording
1. Click the dropdown arrow next to the record button
1. Select your iPhone as both Camera and Microphone source
1. Your iPhone screen appears in QuickTime
1. Click Record
1. Perform the demo on your iPhone
1. Click Stop
1. File > Export As > 1080p (or desired quality)

**Advantages:**

- Higher quality than screen recording
- Easier to manage on Mac
- Can record longer without filling iPhone storage

---

## Converting Video to GIF

### Basic Conversion

```bash
# Good quality, reasonable size (~1MB for 8 seconds)
ffmpeg -i recording.mov \
  -vf "fps=12,scale=350:-1:flags=lanczos" \
  -c:v gif \
  output.gif
```

### Optimized Conversion (Recommended)

```bash
# Two-pass for better colors
ffmpeg -i recording.mov \
  -vf "fps=12,scale=350:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" \
  output.gif

# Then optimize file size
gifsicle --optimize=3 --colors 128 output.gif -o output-optimized.gif
```

### Conversion Options

| Option | Description |
|--------|-------------|
| `fps=12` | Frames per second (10-15 is good for demos) |
| `scale=350:-1` | Width in pixels (-1 keeps aspect ratio) |
| `--colors 128` | Reduce colors to shrink file size |
| `--optimize=3` | Maximum optimization level |

---

## Trimming Videos

If you need to trim before converting:

```bash
# Trim: start at 2 seconds, keep 8 seconds
ffmpeg -i recording.mov -ss 2 -t 8 trimmed.mov

# Then convert trimmed video to GIF
ffmpeg -i trimmed.mov \
  -vf "fps=12,scale=350:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" \
  output.gif
```

---

## Adding GIFs to Presentations

1. Move optimized GIF to `public/images/`
1. Update the deck markdown:

```markdown
![width:300px](../public/images/qr-scan-flow.gif)
```

1. Preview with `npm run dev`
1. Commit and push

---

## Quality Checklist

Before committing each GIF:

- [ ] File size under 2MB (ideally under 1MB)
- [ ] Smooth animation (no jerky movements)
- [ ] Readable text (not too small)
- [ ] Clean start and end (no abrupt cuts)
- [ ] Consistent with other GIFs (same width: 350px)
- [ ] No sensitive data visible (use test accounts)
- [ ] Works in both light and dark presentation themes

---

## Recommended Recording Order

1. **My Bag** (easiest - just scrolling)
1. **AI Disc ID** (need a real disc to photograph)
1. **QR Scan Flow** (need printed QR code)
1. **Visual Recovery** (need disc with phone number)
1. **Recovery Coordination** (need backend setup for notification)

---

## Tips for Better Recordings

1. **Clean up the test account** - Remove any embarrassing or incomplete data
1. **Use airplane mode** - Prevents calls/notifications interrupting
1. **Charge your phone** - Low battery warning ruins recordings
1. **Good lighting** - For camera-based features (AI ID, Visual Recovery)
1. **Steady hands** - Or prop the phone for scanning demos
1. **Practice first** - Do a dry run before recording
1. **Wait 1 second** - At start and end for clean cuts

---

## Troubleshooting

### GIF too large

```bash
# Reduce resolution
ffmpeg -i input.mov -vf "fps=10,scale=300:-1" output.gif

# Reduce colors more aggressively
gifsicle --optimize=3 --colors 64 input.gif -o output.gif

# Reduce frame rate
ffmpeg -i input.mov -vf "fps=8,scale=350:-1" output.gif
```

### Poor quality / banding

Use the two-pass palette generation method above for better colors.

### QuickTime doesn't show iPhone

1. Unlock your iPhone
1. Trust the computer when prompted
1. Try a different USB cable (some cables are charge-only)
1. Restart QuickTime

---

## Sharing GIFs with Web Repo

GIFs created here can also be used on the web landing page:

```bash
# Copy to web repo
cp public/images/qr-scan-flow.gif ../web/public/images/
```

Update the web landing page in `web/src/components/landing/` to reference
the new GIFs.
