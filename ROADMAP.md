# 🗺️ NavRoom Card – Roadmap & Feature Backlog

This document tracks planned features, community requests, and future architecture improvements for **NavRoom Card**.

---

## 📌 Upcoming Features & Enhancements

### 1. 🎨 Smart White Fallback & Manual Accent Color *(Issue #1)*
* **Problem:** On light themes with a white background and lights set to pure white (`rgb(255, 255, 255)`), icons, badge text, and power buttons become pure white on white background (invisible).
* **Proposed Solution:**
  - **Smart Contrast Safeguard:** Automatic luminance/contrast check that gracefully falls back to `accent_fallback` or adjusts brightness when computed RGB is near pure white (`R, G, B > 235`).
  - **Manual Accent Override:** An optional setting in the visual editor allowing users to lock a custom fixed color instead of dynamic light RGB tinting.
* **Priority:** High (Bugfix / Usability)
* **Status:** 📝 Specified & Ready for implementation

---

### 2. 🚨 Smoke Detector & Safety Sensor Integration (`smoke`)
* **Goal:** Native support for smoke, fire, gas, and heat sensors (`binary_sensor` with `device_class: 'smoke' / 'gas' / 'heat'`).
* **Design & Structure:**
  - **Auto-Discovery:** Automatically scans and detects safety binary sensors within the room's area.
  - **Visual Editor Support:** Dedicated entity selector for smoke sensors and sortable chip order integration.
  - **Normal State:** Subtle status chip with `mdi:smoke-detector-variant` and localized `OK` indicator.
  - **Alert State:** High-visibility emergency alert chip (`class="chip alert"` with pulsing red warning) featuring `mdi:fire-alert` and localized warning text (`Smoke!` / `Brand!`).
* **Priority:** High (Safety Feature)
* **Status:** 📝 Specified & Ready for implementation

---

### 3. 🔽 Built-in Collapsible Dropdown / Accordion (`collapsible: true`)
* **Goal:** Integrate collapsible sub-card grid (accordion) natively within the card, eliminating the need for wrapping in external custom cards like `expander-card`.
* **Design & Structure:**
  - **Animated Toggle:** Chevron icon on the header that rotates smoothly on state toggle.
  - **Custom Child Cards:** Support nesting arbitrary Lovelace cards via `cards: [...]` configuration using HA's native `loadCardHelpers()` and `createCardElement()`.
  - **Auto-Populated Grid:** Support an `auto_entities: true` mode which automatically finds all active devices/lights in the area and displays them in a 2-column grid layout of standard Tile cards.
* **Priority:** Medium
* **Status:** 📝 Research & Architecture Approved

---

### 4. 🗂️ Config Editor Schema Re-categorization
* **Goal:** Reorganize the Lovelace visual editor schema (`rkBuildSchema`) into cleaner, logically grouped expandable sections to improve usability as features grow.
* **Proposed Structure:**
  - **Room & Entities** (Always visible): Area selection, Light group/single entity, and Sensor entities (Temp, Humidity, CO2, Smoke).
  - **Appearance**: Layout variant selector (`badge`, `chip`, `pur`, `compact`), left accent border toggle, and status chip sort list.
  - **Colors**: Integrated color pickers for custom accent color, border color, fallback color, and background tint slider.
  - **Sizes & Spacing**: Sliders for card height, corner radius, font size overrides, power button dimensions, etc.
  - **Name & Icon**: Text inputs for custom name override and custom icon override.
  - **Interactions**: Tap, hold, double tap, and power button action configuration.
* **Priority:** Medium
* **Status:** 💡 Specified & Pending Implementation

---

### 5. 🚪 Extended Door, Window & Climate State Integration
* **Goal:** Support summary badges for open doors/windows within the area (e.g. `1 open`) or active HVAC states.
* **Priority:** Low / Backlog
* **Status:** 💡 Backlog

---

## 📋 Completed Milestones
- [x] **v2.3.1:** Compact horizontal row layout variant (`variant: compact`) with space-efficient flex row design, left border accent, and mobile optimization.
- [x] **v2.3.0:** Native localization for Nordic languages (Swedish, Danish, Norwegian, Finnish, Icelandic) and enhanced locale normalization.
- [x] **v2.2.0:** Auto-discovery pre-fill in the visual editor.
- [x] **v2.0.0:** Area discovery, layout variants (`badge`, `chip`, `pur`), and dynamic RGB light color tinting.
