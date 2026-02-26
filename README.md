# futuremobilityalliance
Fictitious website concept 

Check out the deployed site here: [Future Mobility Alliance](https://mataibender.github.io/futuremobilityalliance/)

This site showcases concepts for next‑generation transportation, including Hyperloop pod interiors and modular station designs. Built with HTML and CSS, it demonstrates responsive layouts, external stylesheets, and optimized workflow for a multi‑page project.
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<title>Dials & Switches UI</title>
<style>
  :root {
    --bg: #05060a;
    --panel: #11141c;
    --accent: #5cf2c8;
    --accent-soft: #5cf2c833;
    --track: #262a36;
    --text: #f5f5f7;
    --muted: #8b8fa0;
  }

  * {
    box-sizing: border-box;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, "SF Pro Text", sans-serif;
  }

  body {
    margin: 0;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: radial-gradient(circle at top, #1b2235 0, #05060a 55%);
    color: var(--text);
  }

  .control-panel {
    background: linear-gradient(145deg, #0b0e16, #151927);
    border-radius: 24px;
    padding: 24px 28px;
    display: flex;
    gap: 32px;
    box-shadow:
      0 24px 60px rgba(0, 0, 0, 0.7),
      0 0 0 1px rgba(255, 255, 255, 0.03);
  }

  .group {
    display: flex;
    flex-direction: column;
    gap: 12px;
    min-width: 180px;
  }

  .label {
    font-size: 12px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
  }

  /* DIAL / KNOB */

  .dial-wrapper {
    display: flex;
    align-items: center;
    gap: 18px;
  }

  .dial {
    position: relative;
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background: radial-gradient(circle at 30% 20%, #3b4257, #151927 65%);
    box-shadow:
      0 10px 25px rgba(0, 0, 0, 0.7),
      inset 0 0 0 1px rgba(255, 255, 255, 0.06);
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: grab;
    transition: box-shadow 0.15s ease, transform 0.15s ease;
  }

  .dial:active {
    cursor: grabbing;
    transform: translateY(1px);
    box-shadow:
      0 6px 18px rgba(0, 0, 0, 0.8),
      inset 0 0 0 1px rgba(255, 255, 255, 0.03);
  }

  .dial-inner {
    width: 54px;
    height: 54px;
    border-radius: 50%;
    background: radial-gradient(circle at 30% 20%, #5f6780, #252a3a 70%);
    box-shadow:
      inset 0 0 0 1px rgba(0, 0, 0, 0.7),
      0 0 0 1px rgba(255, 255, 255, 0.04);
    position: relative;
  }

  .dial-indicator {
    position: absolute;
    width: 4px;
    height: 18px;
    border-radius: 999px;
    background: var(--accent);
    top: 6px;
    left: 50%;
    transform: translateX(-50%);
    box-shadow: 0 0 10px var(--accent-soft);
  }

  .dial-ring {
    position: absolute;
    inset: -6px;
    border-radius: 50%;
    border: 2px solid rgba(255, 255, 255, 0.04);
    border-top-color: var(--accent-soft);
    border-right-color: var(--accent-soft);
    filter: blur(0.2px);
  }

  .dial-value {
    font-size: 24px;
    font-variant-numeric: tabular-nums;
  }

  .dial-unit {
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 0.16em;
    color: var(--muted);
  }

  /* TOGGLE SWITCH */

  .switch {
    position: relative;
    width: 64px;
    height: 32px;
    border-radius: 999px;
    background: var(--track);
    box-shadow:
      inset 0 0 0 1px rgba(0, 0, 0, 0.7),
      0 10px 25px rgba(0, 0, 0, 0.7);
    padding: 3px;
    cursor: pointer;
    display: inline-flex;
    align-items: center;
    transition: background 0.2s ease, box-shadow 0.2s ease;
  }

  .switch-thumb {
    width: 26px;
    height: 26px;
    border-radius: 50%;
    background: radial-gradient(circle at 30% 20%, #ffffff, #cfd3e0 70%);
    box-shadow:
      0 4px 10px rgba(0, 0, 0, 0.6),
      0 0 0 1px rgba(255, 255, 255, 0.6);
    transform: translateX(0);
    transition: transform 0.2s ease;
  }

  .switch.on {
    background: radial-gradient(circle at 20% 20%, var(--accent-soft), #1a222f);
    box-shadow:
      0 10px 25px rgba(0, 0, 0, 0.7),
      0 0 18px var(--accent-soft);
  }

  .switch.on .switch-thumb {
    transform: translateX(30px);
  }

  .switch-label-row {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .switch-state {
    font-size: 13px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .switch-state.on {
    color: var(--accent);
  }
</style>
</head>
<body>

<div class="control-panel">
  <!-- DIAL -->
  <div class="group">
    <div class="label">Torque control</div>
    <div class="dial-wrapper">
      <div class="dial" id="dial">
        <div class="dial-ring"></div>
        <div class="dial-inner">
          <div class="dial-indicator" id="dial-indicator"></div>
        </div>
      </div>
      <div>
        <div class="dial-value" id="dial-value">50</div>
        <div class="dial-unit">percent</div>
      </div>
    </div>
  </div>

  <!-- SWITCH -->
  <div class="group">
    <div class="label">Assist mode</div>
    <div class="switch-label-row">
      <div class="switch" id="switch" role="switch" aria-checked="false">
        <div class="switch-thumb"></div>
      </div>
      <div class="switch-state" id="switch-state">Off</div>
    </div>
  </div>
</div>

<script>
  // ----- DIAL LOGIC -----
  const dial = document.getElementById('dial');
  const dialIndicator = document.getElementById('dial-indicator');
  const dialValue = document.getElementById('dial-value');

  let dialAngle = 0;      // 0–270 degrees
  let isDragging = false;

  const minAngle = -135;
  const maxAngle = 135;

  function angleToValue(angle) {
    const normalized = (angle - minAngle) / (maxAngle - minAngle);
    return Math.round(normalized * 100);
  }

  function valueToAngle(value) {
    const clamped = Math.min(100, Math.max(0, value));
    return minAngle + (maxAngle - minAngle) * (clamped / 100);
  }

  function updateDialFromAngle(angle) {
    dialAngle = Math.min(maxAngle, Math.max(minAngle, angle));
    const value = angleToValue(dialAngle);
    dialIndicator.style.transform =
      `translateX(-50%) rotate(${dialAngle}deg)`;
    dialValue.textContent = value;
  }

  function getAngleFromEvent(e) {
    const rect = dial.getBoundingClientRect();
    const cx = rect.left + rect.width / 2;
    const cy = rect.top + rect.height / 2;
    const x = (e.touches ? e.touches[0].clientX : e.clientX) - cx;
    const y = (e.touches ? e.touches[0].clientY : e.clientY) - cy;
    const rad = Math.atan2(y, x);
    let deg = rad * (180 / Math.PI) + 90; // rotate so top is 0
    if (deg < -180) deg += 360;
    if (deg > 180) deg -= 360;
    return deg;
  }

  function startDrag(e) {
    isDragging = true;
    document.addEventListener('mousemove', onDrag);
    document.addEventListener('mouseup', endDrag);
    document.addEventListener('touchmove', onDrag, { passive: false });
    document.addEventListener('touchend', endDrag);
    onDrag(e);
  }

  function onDrag(e) {
    if (!isDragging) return;
    e.preventDefault();
    const angle = getAngleFromEvent(e);
    updateDialFromAngle(angle);
  }

  function endDrag() {
    isDragging = false;
    document.removeEventListener('mousemove', onDrag);
    document.removeEventListener('mouseup', endDrag);
    document.removeEventListener('touchmove', onDrag);
    document.removeEventListener('touchend', endDrag);
  }

  dial.addEventListener('mousedown', startDrag);
  dial.addEventListener('touchstart', startDrag, { passive: false });

  // Initialize dial at 50%
  updateDialFromAngle(valueToAngle(50));

  // ----- SWITCH LOGIC -----
  const sw = document.getElementById('switch');
  const switchState = document.getElementById('switch-state');

  function toggleSwitch() {
    const isOn = sw.classList.toggle('on');
    sw.setAttribute('aria-checked', isOn ? 'true' : 'false');
    switchState.textContent = isOn ? 'On' : 'Off';
    switchState.classList.toggle('on', isOn);
  }

  sw.addEventListener('click', toggleSwitch);
  sw.addEventListener('keydown', (e) => {
    if (e.key === 'Enter' || e.key === ' ') {
      e.preventDefault();
      toggleSwitch();
    }
  });
</script>

</body>
</html>
