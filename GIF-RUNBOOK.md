# GIF Recording Runbook

This guide covers how to record high-quality GIFs from the iOS Simulator for
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
2. Have a test QR code ready (printed or on another screen)
3. Start recording
4. Tap "Scan QR Code"
5. Scan the QR code
6. Show the disc info that appears
7. Tap "Report Found"
8. Show success confirmation
9. Stop recording

---

### 2. AI Disc Identification

**File:** `public/images/ai-disc-id.gif`
**Duration:** ~6-8 seconds
**Shows:** AI identifying a disc from a photo

**Steps to record:**

1. Open the app to the "My Bag" tab
2. Start recording
3. Tap "Add Disc"
4. Tap "AI Identify" or camera icon
5. Take photo of a disc (have a real disc ready)
6. Show AI processing indicator
7. Show results with manufacturer, mold, flight numbers
8. Stop recording

---

### 3. Recovery Coordination Flow

**File:** `public/images/recovery-flow.gif`
**Duration:** ~10-12 seconds
**Shows:** Owner receiving notification and coordinating meetup

**Steps to record:**

1. Trigger a test "disc found" notification (may need backend help)
2. Start recording from lock screen or notification center
3. Show push notification appearing
4. Tap notification to open app
5. Show recovery details screen
6. Tap "Propose Meetup"
7. Show meetup scheduling interface
8. Stop recording

---

### 4. Visual Disc Recovery (Phone Number)

**File:** `public/images/visual-recovery.gif`
**Duration:** ~8-10 seconds
**Shows:** New feature - recovering disc via phone number photo

**Steps to record:**

1. Open the app to "Found Disc" tab
2. Start recording
3. Tap "Use Phone Number on Disc"
4. Take photo of disc back (with phone number visible)
5. Take photo of disc front
6. Show AI extracting phone number
7. Show owner lookup results
8. Stop recording

---

### 5. Disc Inventory / My Bag

**File:** `public/images/my-bag.gif`
**Duration:** ~5-7 seconds
**Shows:** Scrolling through disc collection

**Steps to record:**

1. Ensure test account has 5-10 discs with photos
2. Open "My Bag" tab
3. Start recording
4. Scroll through the disc collection slowly
5. Tap on one disc to show details
6. Show flight numbers and disc info
7. Stop recording

---

## Recording Process

### Step 1: Set Up Simulator

```bash
# List available simulators
xcrun simctl list devices

# Boot a specific simulator (iPhone 15 Pro recommended)
xcrun simctl boot "iPhone 15 Pro"

# Open Simulator app
open -a Simulator
```

### Step 2: Prepare the App

1. Run the app in the simulator: `npm run ios`
2. Log in to a test account with sample data
3. Ensure good test data exists (discs, recoveries, etc.)
4. Enable dark mode or light mode as preferred

### Step 3: Record Video

```bash
# Start recording (saves to current directory)
xcrun simctl io booted recordVideo recording.mov

# Press Ctrl+C to stop recording
```

**Recording tips:**

- Wait 1 second before starting actions (gives a clean start)
- Move slowly and deliberately
- Avoid scrolling too fast
- Wait 1 second after finishing before stopping

### Step 4: Convert to GIF

```bash
# Basic conversion (good quality, reasonable size)
ffmpeg -i recording.mov \
  -vf "fps=12,scale=320:-1:flags=lanczos" \
  -c:v gif \
  output.gif

# Optimize file size
gifsicle --optimize=3 --colors 128 output.gif -o output-optimized.gif
```

**Conversion options:**

| Option | Description |
|--------|-------------|
| `fps=12` | Frames per second (12-15 is good) |
| `scale=320:-1` | Width in pixels (-1 keeps aspect ratio) |
| `--colors 128` | Reduce colors to shrink file size |

### Step 5: Review and Trim

If needed, trim the GIF:

```bash
# Trim first 2 seconds and keep next 8 seconds
ffmpeg -i recording.mov -ss 2 -t 8 \
  -vf "fps=12,scale=320:-1:flags=lanczos" \
  -c:v gif \
  output.gif
```

### Step 6: Add to Presentations

1. Move optimized GIF to `public/images/`
2. Update the deck markdown:

```markdown
![width:300px](../public/images/qr-scan-flow.gif)
```

3. Preview with `npm run dev`
4. Commit and push

---

## Quality Checklist

Before committing each GIF:

- [ ] File size under 2MB (ideally under 1MB)
- [ ] Smooth animation (no jerky movements)
- [ ] Readable text (not too small)
- [ ] Clean start and end (no abrupt cuts)
- [ ] Consistent with other GIFs (same size, style)
- [ ] Works in both light and dark presentation themes

---

## Recommended Recording Order

1. **My Bag** (easiest, just scrolling)
2. **AI Disc ID** (straightforward flow)
3. **QR Scan Flow** (need QR code ready)
4. **Visual Recovery** (new feature demo)
5. **Recovery Coordination** (may need backend setup)

---

## Troubleshooting

### GIF too large

```bash
# Reduce resolution
ffmpeg -i input.mov -vf "fps=10,scale=280:-1" output.gif

# Reduce colors more aggressively
gifsicle --optimize=3 --colors 64 input.gif -o output.gif
```

### Simulator not recording

```bash
# Reset simulator
xcrun simctl shutdown all
xcrun simctl erase all
```

### Poor quality

- Increase fps to 15
- Increase scale to 400
- Use `flags=lanczos` for better scaling

---

## Sharing GIFs with Web Repo

GIFs created here can also be used on the web landing page:

```bash
# Copy to web repo
cp public/images/qr-scan-flow.gif ../web/public/images/

# Or create a symlink (if both repos are always together)
# ln -s ../../presentations/public/images/qr-scan-flow.gif ../web/public/images/
```

Update the web landing page in `web/src/components/landing/Features.tsx` or
create a new demo section.
