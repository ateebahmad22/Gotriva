
---

# 2) `assets/banner.svg` (save this file as `assets/banner.svg`)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<svg xmlns="http://www.w3.org/2000/svg" width="960" height="180" viewBox="0 0 960 180" preserveAspectRatio="xMidYMid meet">
  <style>
    /* fonts fallback */
    .title { font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; font-weight:700; font-size:44px; fill:#0f172a; }
    .subtitle { font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; font-size:14px; fill:#334155; }
    .plane { fill:#06b6d4; stroke: #036b6b; stroke-width:0.6; }
    .cloud { fill:#eef2ff; opacity:0.9; }
  </style>

  <!-- background rounded -->
  <rect x="10" y="10" rx="16" ry="16" width="940" height="160" fill="white" stroke="#e6eef6" />

  <!-- clouds (decorative) -->
  <g transform="translate(120,40)">
    <ellipse class="cloud" cx="0" cy="20" rx="36" ry="14" />
    <ellipse class="cloud" cx="22" cy="10" rx="24" ry="10" />
  </g>
  <g transform="translate(760,30)">
    <ellipse class="cloud" cx="0" cy="18" rx="40" ry="15" />
    <ellipse class="cloud" cx="-22" cy="8" rx="26" ry="11" />
  </g>

  <!-- animated plane path -->
  <path id="flightPath" d="M40 120 C 180 60, 420 60, 600 90 C 720 110, 840 40, 920 60" fill="none" stroke="transparent"/>

  <!-- paper plane (group) -->
  <g id="planeGroup" transform="translate(40,120)">
    <g class="plane" transform="scale(1)">
      <polygon points="0,-6 22,0 0,6 4,0"/>
      <polygon points="14,0 30,-2 34,0 30,2" fill="#0ea5a4" stroke="#036b6b"/>
    </g>
  </g>

  <!-- Gotriva title -->
  <text x="40" y="60" class="title" id="titleText" opacity="0">Gotriva</text>
  <text x="40" y="86" class="subtitle" id="subText" opacity="0">Create your own trip • Share your journey</text>

  <!-- Animate title fading in -->
  <animate xlink:href="#titleText" attributeName="opacity" from="0" to="1" dur="0.9s" begin="0.2s" fill="freeze"/>
  <animate xlink:href="#subText" attributeName="opacity" from="0" to="1" dur="0.9s" begin="0.6s" fill="freeze"/>

  <!-- plane movement along path -->
  <animateMotion xlink:href="#planeGroup" dur="6s" begin="0.5s" repeatCount="indefinite" rotate="auto">
    <mpath xlink:href="#flightPath" />
  </animateMotion>

  <!-- plane gentle bobbing (scale) -->
  <animateTransform xlink:href="#planeGroup" attributeName="transform" type="scale"
    values="1 1; 1.06 1.06; 1 1" dur="1.8s" repeatCount="indefinite" begin="0.5s"/>

  <!-- subtle shimmer on rectangle -->
  <linearGradient id="grad" x1="0" x2="1">
    <stop offset="0%" stop-color="#ffffff" stop-opacity="0.0" />
    <stop offset="50%" stop-color="#ffffff" stop-opacity="0.08" />
    <stop offset="100%" stop-color="#ffffff" stop-opacity="0.0" />
  </linearGradient>
  <rect x="-250" y="10" width="240" height="160" fill="url(#grad)">
    <animate attributeName="x" values="-250;1100" dur="6s" repeatCount="indefinite"/>
  </rect>
</svg>
