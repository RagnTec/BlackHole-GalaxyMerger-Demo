# BlackHole-GalaxyMerger-Demo

[中文](README.md) | English

> Single-file, zero-dependency WebGL2 demo: a Gargantua-style black hole rendered with per-pixel Schwarzschild geodesic ray tracing, a Milky Way × Andromeda merger/flyby simulation (restricted three-body), an accretion disk, and Miller's tide-locked planet. Open `index.html` in any modern browser — no build step, no server required.

**Live demo**: https://ragntec.github.io/BlackHole-GalaxyMerger-Demo/

## Features

- **Per-pixel Schwarzschild ray tracing**: black-hole shadow, photon ring, gravitational lensing
- **Accretion disk**: spin-dependent ISCO inner edge (Bardeen), Novikov–Thorne temperature profile, Doppler beaming and gravitational redshift
- **Galaxy merger & flyby**: Milky Way (barred spiral) × Andromeda (spiral) restricted three-body simulation with merger and flyby scenarios; tidal bridges and tails emerge naturally
- **Miller's planet**: giant waves, tidal locking, time-dilation readout
- **Interstellar rogue planet**: adjustable impact parameter (4–24M), full evolution: flyby / capture & inspiral / tidal disruption at 7M Roche limit (shatters into 140-particle debris stream) / plunge, high-visibility cyan-glow rendering; **auto-spawn mode**: random impact parameter & approach direction, one at a time, next spawns 10s after the previous ends (old planet fades out smoothly), manual launch overrides anytime
- **Continuous galaxy collision parameter**: 0–100 slider seamlessly blends head-on / off-center merger / close & distant flybys; **manual evolution**: ~15s main evolution, then physics continues to a stable end state (merger relaxation / separation) with no auto-replay — restart manually
- **Immersive mode**: one-click hide all UI (pulsing 👁 at bottom-right to restore)
- **Starfield controls**: background star density (10–100%) & brightness (0–2×), galaxies unaffected
- **Film-accurate time dilation**: Miller's planet strictly follows *Interstellar* — 1 hour = 7 years (dτ/dt = 1/61,320)
- **Display filters**: accretion disk, Miller's planet, rogue planet, Milky Way, Andromeda, background stars can be toggled independently
- **Mobile ready**: one-finger rotate, pinch zoom, virtual joystick, bottom control drawer on small screens
- **Bilingual UI**: auto-detects browser language, manual toggle at top-right (choice is remembered)
- **Adaptive rendering**: HDR bloom pipeline on desktop (RGBA16F + separable Gaussian bloom + ACES), single-pass direct output on mobile (designed around iPhone WebGL constraints)

## Run Locally

Just open `index.html` in a browser; or serve it locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/
```

Requires WebGL2. Latest Chrome / Edge / Safari recommended on desktop; use Safari on iPhone.

## Code Structure

The whole project is a single `index.html` (~86KB) — intentionally dependency-free, so it can be deployed to any static hosting as-is:

| Part | Description |
| --- | --- |
| GLSL fragment shader | geodesic integration, disk shading, analytic glow (impact-parameter driven, single pass) |
| JS physics | restricted three-body galaxy sim, planet/camera dynamics, adaptive resolution |
| JS UI | desktop panel, mobile gestures & drawer, demo looping, bilingual toggle, display filters |

`.nojekyll` tells GitHub Pages to skip Jekyll processing.

## Contributing

PRs are welcome — let's make this little universe better together:

1. Fork the repo and create a branch (`git checkout -b feat/your-idea`)
2. Keep it **single-file, zero-dependency** — this is the project's core constraint; any PR introducing build steps or CDN dependencies will not be accepted
3. Mobile (especially iPhone Safari) is the top priority: please verify on a real device or at least a mobile emulator that there is no black screen and no major frame drops
4. Open the PR describing what changed and which devices you tested on

Feel free to open an Issue first to discuss ideas (physics accuracy, visuals, and performance are all great topics).

## License

MIT — see [LICENSE](LICENSE).
