# Hello World — Kivy

A minimal **Kivy** application, set up as the starting point for a cross-platform Python app that can be packaged for Android with **Buildozer**.

It is deliberately small: one app class, one widget, and the packaging configuration already in place so the first Android build is a single command.

---

## Highlights

| | |
|---|---|
| **Runs everywhere Kivy does** | Linux, macOS, Windows and Android from the same source |
| **Android-ready** | `buildozer.spec` is committed, so packaging needs no extra setup |
| **Clean package layout** | `src/hello_world/` is laid out for screens, widgets and services |
| **Modern tooling** | Declared in `pyproject.toml` and installable with `uv` |
| **Console entry point** | Installs a `hello-world` command alongside the module |

---

## The application

```python
from kivy.app import App
from kivy.uix.label import Label


class HelloWorldApp(App):
    def build(self):
        return Label(text="Hello World")


if __name__ == "__main__":
    HelloWorldApp().run()
```

---

## Getting started

### Prerequisites

- Python 3.10 or newer

### 1. Install

```bash
git clone https://github.com/harshlaxkar07/Hello_world.git
cd Hello_world

# with uv (recommended)
uv sync

# or with pip
python -m venv .venv && source .venv/bin/activate
pip install -e .
```

### 2. Run on the desktop

```bash
python main.py
```

or, using the installed entry point:

```bash
hello-world
```

---

## Building for Android

Buildozer is already a declared dependency and `buildozer.spec` is committed.

```bash
# Debug build — produces an APK under bin/
buildozer -v android debug

# Build, install and run on a connected device
buildozer android debug deploy run
```

The first build pulls the Android SDK, the NDK and python-for-android, so expect it to take a while. Later builds reuse that cache and are much quicker.

---

## Project structure

```
Hello_world/
├── main.py                       The Kivy application
├── buildozer.spec                Android packaging configuration
├── pyproject.toml                Project metadata and dependencies
└── src/hello_world/
    ├── __init__.py               Package entry point
    ├── app.py                    Application module
    ├── screens/                  Screen classes
    ├── widgets/                  Reusable widgets
    └── services/                 Background and platform services
```

The `screens/`, `widgets/` and `services/` packages give a growing app an obvious place for each kind of code from the first commit.
