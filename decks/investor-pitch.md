---
marp: true
theme: default
paginate: true
backgroundColor: #fff
color: #333
style: |
  section {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    padding: 40px 60px;
  }
  h1 {
    color: #7c3aed;
    margin-bottom: 0.5em;
  }
  h2 {
    color: #555;
    font-weight: 400;
    margin-top: 0;
  }
  section.lead {
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    background: linear-gradient(135deg, #7c3aed 0%, #5b21b6 100%);
    color: white;
  }
  section.lead h1 {
    color: white;
    font-size: 4rem;
    margin-bottom: 0.2em;
  }
  section.lead h2 {
    color: rgba(255,255,255,0.9);
    font-size: 1.8rem;
  }
  section.invert {
    background: #18181b;
    color: #fff;
  }
  section.invert h1 {
    color: #a78bfa;
  }
  .stat-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
    margin-top: 2rem;
  }
  .stat-box {
    text-align: center;
    padding: 1.5rem;
    background: #f4f4f5;
    border-radius: 12px;
  }
  .stat-box .number {
    font-size: 2.5rem;
    font-weight: bold;
    color: #7c3aed;
  }
  .stat-box .label {
    font-size: 0.9rem;
    color: #666;
    margin-top: 0.5rem;
  }
  .feature-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1.5rem;
    margin-top: 1.5rem;
  }
  .feature-box {
    padding: 1.2rem;
    background: #faf5ff;
    border-left: 4px solid #7c3aed;
    border-radius: 0 8px 8px 0;
  }
  .feature-box h3 {
    margin: 0 0 0.5rem 0;
    color: #7c3aed;
    font-size: 1.1rem;
  }
  .feature-box p {
    margin: 0;
    font-size: 0.9rem;
    color: #555;
  }
  table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 1rem;
  }
  th {
    background: #7c3aed;
    color: white;
    padding: 12px;
    text-align: left;
  }
  td {
    padding: 12px;
    border-bottom: 1px solid #e5e5e5;
  }
  tr:nth-child(even) {
    background: #fafafa;
  }
  .demo-placeholder {
    background: #f4f4f5;
    border: 2px dashed #ccc;
    border-radius: 12px;
    padding: 2rem;
    text-align: center;
    color: #888;
  }
---

<!-- _class: lead -->

# Discr

## Never Lose a Disc Again

---

# The Problem

## Disc golfers lose millions of discs every year

<div class="stat-grid">
<div class="stat-box">
<div class="number">5-10</div>
<div class="label">Discs lost per player annually</div>
</div>
<div class="stat-box">
<div class="number">$15-25</div>
<div class="label">Cost per premium disc</div>
</div>
<div class="stat-box">
<div class="number">~10%</div>
<div class="label">Industry recovery rate</div>
</div>
</div>

**Current solutions fail:** Sharpie fades, no standardized return process, found discs sit in lost & found boxes forever.

---

# The Solution

## Smart QR Stickers + Mobile App

<div class="feature-grid">
<div class="feature-box">
<h3>1. Register Your Discs</h3>
<p>Apply durable QR code stickers that survive any course conditions</p>
</div>
<div class="feature-box">
<h3>2. Finder Scans</h3>
<p>Anyone can scan with their phone camera - no app download required</p>
</div>
<div class="feature-box">
<h3>3. Instant Notification</h3>
<p>Owner gets push notification the moment their disc is found</p>
</div>
<div class="feature-box">
<h3>4. Coordinate Return</h3>
<p>Built-in messaging and meetup scheduling to get your disc back</p>
</div>
</div>

---

# How It Works

<!-- TODO: Add scan-to-recovery GIF demo -->

<div class="demo-placeholder">

**[GIF: Complete scan-to-recovery flow]**

Finder scans QR → Owner notified → Meetup scheduled → Disc returned

</div>

**Key differentiator:** Finders don't need the app. The QR code opens a web page that handles everything.

---

<!-- _class: invert -->

# AI-Powered Features

## Beyond Simple QR Codes

<div class="feature-grid">
<div class="feature-box" style="background: #27272a; border-color: #a78bfa;">
<h3 style="color: #a78bfa;">AI Disc Identification</h3>
<p style="color: #a1a1aa;">Snap a photo of any disc and instantly identify the manufacturer, mold, and flight numbers</p>
</div>
<div class="feature-box" style="background: #27272a; border-color: #a78bfa;">
<h3 style="color: #a78bfa;">Visual Disc Recovery</h3>
<p style="color: #a1a1aa;">No QR code? Photo the phone number on the disc - AI extracts it and finds the owner</p>
</div>
<div class="feature-box" style="background: #27272a; border-color: #a78bfa;">
<h3 style="color: #a78bfa;">AI Shot Advisor</h3>
<p style="color: #a1a1aa;">Photograph any hole from the tee and get personalized disc and throw recommendations</p>
</div>
<div class="feature-box" style="background: #27272a; border-color: #a78bfa;">
<h3 style="color: #a78bfa;">Smart Inventory</h3>
<p style="color: #a1a1aa;">Track your entire collection with photos, flight numbers, and wear tracking</p>
</div>
</div>

---

# Product Demo

<div style="display: flex; gap: 1.5rem; justify-content: center; margin-top: 1rem;">
<div style="text-align: center; flex: 1;">
<div class="demo-placeholder" style="height: 300px;">

**[GIF: QR Scan Flow]**

</div>
<p style="margin-top: 0.5rem; font-weight: 500;">Scan & Report</p>
</div>
<div style="text-align: center; flex: 1;">
<div class="demo-placeholder" style="height: 300px;">

**[GIF: AI Identification]**

</div>
<p style="margin-top: 0.5rem; font-weight: 500;">AI Disc ID</p>
</div>
<div style="text-align: center; flex: 1;">
<div class="demo-placeholder" style="height: 300px;">

**[GIF: Recovery Flow]**

</div>
<p style="margin-top: 0.5rem; font-weight: 500;">Get It Back</p>
</div>
</div>

---

# Market Opportunity

## Disc Golf is the Fastest Growing Sport in America

<div class="stat-grid">
<div class="stat-box">
<div class="number">50M+</div>
<div class="label">Rounds played annually (US)</div>
</div>
<div class="stat-box">
<div class="number">40%</div>
<div class="label">Participation growth since 2020</div>
</div>
<div class="stat-box">
<div class="number">15,000+</div>
<div class="label">Courses worldwide</div>
</div>
</div>

- Average player owns **15-20 discs** and actively purchases more
- Passionate, engaged community with strong social networks
- Low barrier to entry driving continued growth
- Underserved by technology solutions

---

# Business Model

## Multiple Revenue Streams

| Revenue Stream | Description | Status |
|----------------|-------------|--------|
| **Sticker Sales** | $10-15 per sheet of premium QR stickers | Active |
| **Premium Subscription** | Advanced features, unlimited disc tracking | Planned |
| **Reward Facilitation** | Small fee on optional reward payments | Active |
| **B2B Partnerships** | Course lost & found integration, tournaments | Pipeline |

**Unit economics:** High margin on stickers, recurring revenue from subscriptions, network effects drive growth.

---

# Competitive Landscape

## Why Discr Wins

| Feature | Discr | Sharpie | Other Apps |
|---------|:-----:|:-------:|:----------:|
| Durable identification | QR Sticker | Fades/Smears | Varies |
| No app needed to report | **Yes** | N/A | No |
| AI disc identification | **Yes** | No | No |
| Visual phone recovery | **Yes** | No | No |
| Built-in reward system | **Yes** | N/A | Limited |
| Works on any disc | **Yes** | Yes | Some |

**Moat:** AI capabilities, network effects, first-mover advantage in QR-based recovery.

---

# Traction

## Early Momentum

<div class="stat-grid">
<div class="stat-box">
<div class="number">X</div>
<div class="label">Discs Registered</div>
</div>
<div class="stat-box">
<div class="number">X%</div>
<div class="label">Recovery Rate</div>
</div>
<div class="stat-box">
<div class="number">X</div>
<div class="label">Monthly Active Users</div>
</div>
</div>

**Milestones:**

- iOS app launched and live on App Store
- Android in development
- Sticker fulfillment operational
- AI features deployed and improving

---

# Go-to-Market Strategy

## Community-First Growth

1. **Grassroots Marketing**
   - Partner with disc golf influencers and content creators
   - Sponsor local leagues and tournaments
   - Course pro shop partnerships

2. **Viral Mechanics**
   - Every found disc introduces a new potential user
   - Social sharing of recovery stories
   - Referral incentives

3. **B2B Expansion**
   - Course lost & found digitization
   - Tournament integration
   - Retail partnerships

---

# The Team

## Passionate Disc Golfers Building for Disc Golfers

<!-- TODO: Add team photos -->

<div style="display: flex; gap: 2rem; margin-top: 1.5rem;">
<div style="flex: 1;">

### [Founder Name]

CEO / Co-founder

[Background, experience, disc golf credentials]

</div>
<div style="flex: 1;">

### [Co-founder Name]

CTO / Co-founder

[Technical background, relevant experience]

</div>
</div>

---

# The Ask

## Seed Round

<div style="display: flex; gap: 3rem; margin-top: 1.5rem;">
<div style="flex: 1;">

### Use of Funds

- **Product Development** - AI features, Android app
- **Marketing** - User acquisition, influencer partnerships
- **Operations** - Sticker manufacturing scale-up
- **Team** - Key engineering and growth hires

</div>
<div style="flex: 1;">

### Key Milestones

- **X** registered discs
- **X** monthly active users
- Launch premium subscription tier
- **X** B2B course partnerships
- Android app launch

</div>
</div>

---

<!-- _class: lead -->

# Let's Get Your Discs Home

## Questions?

**<hello@discrapp.com>**
**<https://discrapp.com>**
