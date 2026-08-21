---
layout: page
title: Themes
permalink: /themes/
---

# Choose Your Theme

Click a theme below — it applies instantly and is saved in your browser. The switcher also lives at the bottom-right on every page.

<div style="display:grid; grid-template-columns: repeat(auto-fit, minmax(240px,1fr)); gap:1rem; margin:1.5rem 0;">
  <div class="theme-card" style="border:1px solid #e8e8e8; border-radius:12px; padding:1rem; text-align:center;">
    <div style="height:80px; background: linear-gradient(135deg,#0f0f23 0%,#e94560 100%); border-radius:8px; display:flex; align-items:center; justify-content:center; color:#fff; font-weight:700;">VHS / Retro</div>
    <h3 style="margin:0.75rem 0 0.25rem;">VHS <small style="font-weight:400; color:#666;">(default)</small></h3>
    <p style="font-size:0.85rem; color:#666;">Scanlines, VHS rewind button, red/amber glow — loss.backward identity</p>
    <button onclick="localStorage.setItem('alinikkhah-theme','vhs'); document.body.className=document.body.className.replace(/theme-\w+/g,''); document.getElementById('theme-variant')?.remove(); location.reload();" style="padding:0.35rem 0.9rem; border-radius:999px; border:1px solid #e94560; background:#fff; cursor:pointer;">Apply</button>
  </div>
  <div class="theme-card" style="border:1px solid #e8e8e8; border-radius:12px; padding:1rem; text-align:center;">
    <div style="height:80px; background: linear-gradient(135deg,#00ffcc 0%,#ff00ff 100%); border-radius:8px;"></div>
    <h3 style="margin:0.75rem 0 0.25rem;">Cyberpunk</h3>
    <p style="font-size:0.85rem; color:#666;">Neon cyan/magenta, high contrast, glitch</p>
    <button onclick="localStorage.setItem('alinikkhah-theme','cyberpunk'); location.reload();" style="padding:0.35rem 0.9rem; border-radius:999px; border:1px solid #00ffcc; background:#fff; cursor:pointer;">Apply</button>
  </div>
  <div class="theme-card" style="border:1px solid #e8e8e8; border-radius:12px; padding:1rem; text-align:center;">
    <div style="height:80px; background:#f5f3ef; border:1px solid #e8e6e1; border-radius:8px; display:flex; align-items:center; justify-content:center; color:#5a7a6a;">Aa Zen</div>
    <h3 style="margin:0.75rem 0 0.25rem;">Zen</h3>
    <p style="font-size:0.85rem; color:#666;">Ultra-clean, generous whitespace, sage accent</p>
    <button onclick="localStorage.setItem('alinikkhah-theme','zen'); location.reload();" style="padding:0.35rem 0.9rem; border-radius:999px; border:1px solid #8da399; background:#fff; cursor:pointer;">Apply</button>
  </div>
  <div class="theme-card" style="border:1px solid #e8e8e8; border-radius:12px; padding:1rem; text-align:center;">
    <div style="height:80px; background:#fdf6ec; border:1px solid #e8dcc6; border-radius:8px; display:flex; align-items:center; justify-content:center; font-family:serif; color:#1a1a1a;">Academic</div>
    <h3 style="margin:0.75rem 0 0.25rem;">Academic</h3>
    <p style="font-size:0.85rem; color:#666;">Crimson Pro serif, paper texture, citations</p>
    <button onclick="localStorage.setItem('alinikkhah-theme','academic'); location.reload();" style="padding:0.35rem 0.9rem; border-radius:999px; border:1px solid #c9a86a; background:#fff; cursor:pointer;">Apply</button>
  </div>
  <div class="theme-card" style="border:1px solid #e8e8e8; border-radius:12px; padding:1rem; text-align:center;">
    <div style="height:80px; background:#0a0e0a; border:1px solid #33ff33; border-radius:8px; display:flex; align-items:center; justify-content:center; color:#33ff33; font-family:monospace;">&gt;_</div>
    <h3 style="margin:0.75rem 0 0.25rem;">Terminal</h3>
    <p style="font-size:0.85rem; color:#666;">JetBrains Mono, green on black, cursor blink</p>
    <button onclick="localStorage.setItem('alinikkhah-theme','terminal'); location.reload();" style="padding:0.35rem 0.9rem; border-radius:999px; border:1px solid #33ff33; background:#fff; cursor:pointer;">Apply</button>
  </div>
  <div class="theme-card" style="border:1px solid #e8e8e8; border-radius:12px; padding:1rem; text-align:center;">
    <div style="height:80px; background:#000; border:1px solid #222; border-radius:8px; display:flex; align-items:center; justify-content:center; color:#e94560;">● Midnight</div>
    <h3 style="margin:0.75rem 0 0.25rem;">Midnight</h3>
    <p style="font-size:0.85rem; color:#666;">Pure OLED black, single red accent, battery saver</p>
    <button onclick="localStorage.setItem('alinikkhah-theme','midnight'); location.reload();" style="padding:0.35rem 0.9rem; border-radius:999px; border:1px solid #222; background:#fff; cursor:pointer;">Apply</button>
  </div>
</div>

> Tip: the floating switcher at bottom-right persists your choice via `localStorage:alinikkhah-theme`.

### Comparison

| Theme | Base | Accent | Font | Best for |
|---|---|---|---|---|
| **VHS** | Minima antique + custom | Red `#e94560` / cyan | System sans | Default, loss.backward identity, retro |
| **Cyberpunk** | Dark `#0a0a12` | Neon cyan/magenta | Sans + mono headings | Hype, demos, bold |
| **Zen** | Warm `#fdfcf8` | Sage `#5a7a6a` | Georgia serif body | Long-form reading |
| **Academic** | Paper `#fefefe` | Gold `#c9a86a` | Crimson Pro | Papers, citations |
| **Terminal** | Hacker `#0a0e0a` | Green `#33ff33` | JetBrains Mono | Code, hacker vibe |
| **Midnight** | OLED `#000` | Red `#e94560` | Sans | Dark mode, OLED |

All 6 are tested at `https://alinikkhah2001.github.io/` — styles served as `assets/css/style.css` (VHS base) + `assets/css/theme-{name}.css` variants. Switcher injects variant CSS dynamically via `theme-switcher.html`.

### Other Jekyll Themes Researched (10+)

See `JEKYLL_THEMES_RESEARCH.md` in OpenClaw workspace for 15 options: Minima, Just the Docs, Chirpy, Minimal Mistakes, TeXt, Huxpro, Lanyon, Poole, Al-folio, Jekyll-Serif, Tale, Kiko, Yat, Type on Strap, + custom VHS. Recommendation: stay on **Minima v2.5.0** with custom variants (fastest, GitHub Pages native, no `remote_theme` lag).

*Last updated: {{ site.time | date: "%B %Y" }}*