# circlr

An orbital music workspace for songwriters and arrangers on macOS.

English · [한국어](README.ko.md)

Build songs from connected sections, edit MIDI and audio on circular timelines, and move between an arrangement and its details on one canvas.

![circlr 1.2.0 build253 with the bundled demo](docs/images/circlr-song-build253.jpg)

This source snapshot preserves the application code from **1.2.0 build253**. It is a source publication, not a new product release. The interface is in Korean.

## Working with music

- Plan song form with reusable sections, repetitions and arrangement variations.
- Edit MIDI notes and steps, import audio, split clips and apply fades.
- Route instruments/effects, edit automation, bounce tracks and restore their sources.
- Inspect and edit a project through the local command console and MCP interface.

In-app account chat is disabled by default. Physical listening, broad Korean IME coverage, the known 70ms video interval issue and compatibility with every device or plug-in are outside this snapshot's verified scope. [Validation](docs/validation.md)

<img src="docs/images/circlr-song-portrait-build253.jpg" width="280" alt="The same build253 demo in a portrait window">

Both screenshots are unmodified native captures of build253. [Capture details](docs/images/README.md)

## Build from source

Use **macOS 14+, full Xcode 26+ selected as the active developer directory, and Python 3**. The optional agent-kit installer requires **Python 3.11+**. Apple Silicon is the previously validated native platform. The local publication checks used Xcode 27.1 / Swift 6.4. CI is configured for macOS 26 with Xcode 26.6; its updated result is tracked separately in [validation](docs/validation.md).

```sh
./scripts/build-app.sh
```

The app is written to `dist/써클러.app` with its helpers, demos and agent kit. Local packages are ad-hoc signed and are not Apple-notarized. The build does not launch or install the app. [Build and tests](docs/build.md)

## Documentation

- [Architecture](docs/architecture.md)
- [Local MCP and agent kit](mcp/README.md)
- [Validation and known limits](docs/validation.md)
- [Demo sources and rights](docs/demo-sources.md)
- [Contributing](CONTRIBUTING.md) · [Change record](CHANGELOG.md)

## License

Code, documentation and project artwork use the [MIT License](LICENSE), subject to the [third-party notices](THIRD_PARTY_NOTICES.md).

Bundled music has separate terms. The unmodified demos may be redistributed with circlr and its forks when their notices are retained. The six percussion recordings remain CC0 and the original classical MIDI/LilyPond sources remain Public Domain. The compositions and new arrangements are not MIT or CC0. [Demo terms](Resources/Demos/DEMO-LICENSE.md) · [Classical terms](Resources/Demos/classical/ARRANGEMENT-TERMS.md)
