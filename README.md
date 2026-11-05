# setup-pyside6-win7

[![Test composite action](https://github.com/DevelopersQi/LorenEteval_setup-pyside6-win7/actions/workflows/test.yml/badge.svg?branch=main)](https://github.com/LorenEteval/setup-pyside6-win7/actions/workflows/test.yml)

GitHub action that sets up a Windows7–compatible version of PySide6.

## Usage

```yaml
- name: Setup PySide6 for Windows7  
  uses: DevelopersQi/LorenEteval_setup-pyside6-win7@aa0989d281e3dab9c8e08f112401ec7e92e3a164
  with:
    # required: PySide6 version
    pyside6-version: "6.8.3"
    # optional: x86 or x64, default is x64
    architecture: x64
    # optional: PySide6 relative library path, default is Lib/site-packages
    relative-lib-path: Lib/site-packages
    # optional: setup PySide6 for windows7 from this repo
    github-repo: crystalidea/qt6windows7
    # optional: release tag for the github repo, default is v{{ inputs.pyside6-version }}
    release-tag: v6.8.3
- name: Check PySide6 for Windows7 version
  shell: bash
  run: |
    python -c "import sys; print(sys.version)"
    python -c "import PySide6; print(PySide6.__version__)"
```


## Compatibility notes

The action replaces the Qt runtime with a Windows 7-compatible build. The GitHub-hosted Windows runner test verifies installation and import behavior on a modern Windows runner only; it does not prove Windows 7 runtime compatibility. Validate GUI startup, platform plugins, and required Qt modules on a real Windows 7 x64 machine or VM. This repository currently documents a pinned commit because no `v1` release tag is published.
