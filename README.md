# Harmonic Explorer

An interactive tool for understanding why notes sound consonant or dissonant
together, seen through the lens of a guitar fretboard.

The whole application is a single self-contained HTML document
([`index.html`](index.html)) — no build step, no external dependencies, no
network access. It is shipped as a Debian package that opens it in a
dedicated WebKitGTK window.

## Features

- Clickable guitar fretboard with capo and key selection
- Additive synthesis with selectable waveforms and an ADSR envelope editor
- Live waveform and spectrum visualization
- Live Plomp–Levelt dissonance curve for the selected notes
- Chord builder with consonance/dissonance analysis of every interval
- Melody playback in the selected key

## Running without installing

Open `index.html` in any modern browser, or run the launcher directly:

```sh
./bin/harmonic-explorer
```

## Building the Debian package

Build dependencies: `debhelper` (and optionally `devscripts` and `lintian`).

```sh
sudo apt install debhelper devscripts lintian
dpkg-buildpackage -us -uc          # or: debuild -us -uc
```

The `.deb` lands in the parent directory. Install and run it with:

```sh
sudo apt install ../harmonic-explorer_2.0.0_all.deb
harmonic-explorer                  # or launch "Harmonic Explorer" from the app menu
```

Remove it again with `sudo apt remove harmonic-explorer`.

## Repository layout

| Path | Purpose |
| --- | --- |
| `index.html` | The application (current version, formerly v2) |
| `archive/` | Older prototypes, not shipped in the package |
| `bin/harmonic-explorer` | Launcher: WebKitGTK window with `xdg-open` fallback |
| `data/` | Desktop entry, hicolor icons, AppStream metadata |
| `man/` | Man page |
| `debian/` | Debian packaging |

## Next steps (not yet done)

- Publish to a Launchpad PPA for `apt`-based updates
- Snap/Flatpak variants
- CI to build and lint the package on every push

## License

MIT — see [LICENSE](LICENSE).
