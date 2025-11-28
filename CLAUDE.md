# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Wiwynn Visitor Management System - A smart visitor registration and analytics platform with a solar system theme, combining Three.js 3D animations with Chart.js data visualization.

**Tech Stack:**
- Pure HTML5 + CSS3 + JavaScript (ES6+)
- Three.js r160 for 3D planet rendering
- Chart.js for data visualization
- Glassmorphism design with cyan neon theme (#00f2ff)
- Planned integration: Supabase (DB), Python (daily HR sync), Power Automate (Teams notifications)

## Key System Pages

1. **index.html** - Landing page with navigation to registration and dashboard
2. **visitor-register.html** - Main visitor registration form with 9-planet solar system background
3. **dashboard.html** - Real-time analytics dashboard with 6 chart types

## Architecture & Data Flow (Planned)

Per PRD (`Wiwynn_Visitor_PRD_New.md`):

```
HR DB/API → Python Script (daily sync) → Supabase employees table
                                              ↓
QR Code → visitor-register.html → Supabase visitor_log table
                                              ↓
                                   Power Automate → Teams Adaptive Card
```

**Supabase Schema:**
- `employees`: name, email, department, updated_at
- `visitor_log`: name, phone, company, host_emails, photo_base64, signature_base64, rule_agreed, arrive_time, notified

## Three.js Solar System Implementation

**Planet Textures:** Located in `person-main/textures/`
- 9 planets (Mercury to Pluto) with realistic 2K textures
- Saturn includes ring texture (`2k_saturn_ring_alpha.png`)
- Sun at origin with pulsing glow effect

**Key Effects:**
- 3000+ twinkling stars with custom canvas-based point sprites
- Orbital mechanics with individual planet speeds
- Interactive camera controls (drag to rotate scene)
- Canvas texture generation for star cross-flare effects

**Performance:**
- PixelRatio capped at 2 for mobile optimization
- Shadow maps enabled with PCFSoftShadowMap

## Visitor Registration Flow

1. **Basic Info:** Name, company, phone (required fields)
2. **Photo Capture:** Camera input with Base64 encoding
3. **Employee Search:**
   - Mock data currently (`mockEmployees` array)
   - Will connect to Supabase `employees` table
   - Multi-select support with live counter
4. **Signature:** HTML5 Canvas with touch/mouse support
   - Device pixel ratio scaling for retina displays
5. **Rules Agreement:** Scrollable checkbox validation
6. **Validation:** Client-side error messages with cyan glow

## Dashboard Data Visualization

**6 Chart Types:**
1. Traffic Line Chart - 24h visitor flow
2. Department Bar Chart - 3D styled bars with rainbow colors
3. Visitor Type Doughnut - 70% cutout donut chart
4. Peak Hours Radar - Time-based activity analysis
5. Weekly Trend Multi-line - Visitors/check-ins/check-outs
6. Purpose Horizontal Bar - Indexed Y-axis

**Auto-refresh:** Mock data regenerates every 30 seconds

**Chart.js Global Config:**
- Font: Inter sans-serif
- Border color: `rgba(0, 242, 255, 0.1)` (cyan with 10% opacity)
- Tooltips: Dark glass background with cyan border

## CSS Design System

**CSS Variables:**
```css
--primary-color: #00f2ff (cyan)
--glass-bg: rgba(15, 25, 50, 0.7)
--glass-border: rgba(0, 242, 255, 0.2)
--text-color: #e0f7ff (light cyan)
```

**Key Patterns:**
- Glassmorphism: `backdrop-filter: blur(10px)` with semi-transparent backgrounds
- Hover effects: translateY(-10px) + box-shadow glow
- Animations: fade-in stagger, floating logo, text glow pulse

## Common Development Tasks

**Testing locally:**
```bash
# Serve with any static file server, e.g.:
python -m http.server 8000
# Or
npx serve
```

**Texture paths:** All planet textures use relative path `person-main/textures/` - ensure directory structure matches when deploying

**Module imports:** visitor-register.html uses importmap for Three.js from CDN:
```javascript
"three": "https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.module.js"
```

## Backend Integration (TODO per PRD)

**Python Daily Sync:**
- Use Supabase Python client
- Upsert employee data from HR API/CSV
- Service role key for backend, anon key for frontend

**Row Level Security:**
- `employees`: Allow SELECT (public read)
- `visitor_log`: Allow INSERT only (write-only for visitors)

**Power Automate Flow:**
- Poll `visitor_log.notified = false` every minute
- Send Adaptive Card to `host_emails`
- Update `notified = true`

## Deployment Notes

**GitHub Pages:**
```bash
git remote add origin https://github.com/USERNAME/wiwynn-visitor-system.git
git push -u origin main
# Enable Pages in Settings → Pages → Source: main branch
```

**Critical Files:**
- Logo: `Wiwynn_LOGO_with Chinese_Name_Blue_Green (2).png`
- Three.js: `three.min.js` (for index.html and dashboard.html)
- Chart.js: `chart.min.js`
- Texture directory: `person-main/textures/` (10 image files)

## Browser Compatibility

- Chrome/Edge (recommended for WebGL performance)
- Firefox, Safari supported
- Mobile responsive with media queries at 768px breakpoint
- Touch events supported for signature canvas

## Security Considerations

**No sensitive data in frontend:**
- Employee data limited to name/email/department
- Visitor photos/signatures stored as Base64 (will move to Supabase storage)
- RLS enforced at database level
- Anon key with minimal permissions for frontend API calls

## Known Mock Data

Current mock employee list in visitor-register.html:
- Alan Chen (IT Dept)
- Bob Lin (Sales)
- Debbie Wu (HR)
- Max Wang (RD)
- Demi Liu (Finance)

Replace `mockEmployees` array with Supabase query once database is connected.
