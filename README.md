# Thunder

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) 

![Linux Build](https://github.com/rdkcentral/Thunder/actions/workflows/Build%20Thunder%20on%20Linux.yml/badge.svg) ![Windows Build](https://github.com/rdkcentral/Thunder/actions/workflows/Build%20Thunder%20on%20Windows.yml/badge.svg) ![Unit Test](https://github.com/rdkcentral/Thunder/actions/workflows/Test%20Thunder.yml/badge.svg)


Thunder is an open-source plugin-based device abstraction layer, where business functionality can be implemented as plugins and applications can query and control those plugins. Using Thunder provides a consistent interface-driven development model for both plugins and client applications, with an RPC engine that is suited to both web-based and native apps.

Designed from the ground up for embedded platforms and written in C++11, Thunder can be run on even the most low-power of devices (including ARM and MIPS-based platforms).

# Documentation

All documentation and build instructions for Thunder can be found here: [Documentation](https://rdkcentral.github.io/Thunder/)

Interfaces documentation can be found here:
https://webplatformforembedded.github.io/ServicesInterfaceDocumentation

## EditorConfig policy

This repository includes a .editorconfig that enforces:
- LF line endings
- UTF-8 encoding
- Consistent indentation (spaces) and size per file type
- Trimming trailing whitespace and ensuring a final newline

Most IDEs respect .editorconfig automatically. Enable “Format on Save” if available.

## Developer tooling: cmake-format

A cmake-format configuration is provided at .cmake-format.yaml to keep all CMake files consistent.

- Install:
  ```
  pip install cmakelang
  ```
  (This provides the `cmake-format` tool.)

- Format in place:
  ```
  cmake-format -i CMakeLists.txt
  find . -type f \( -name 'CMakeLists.txt' -o -name '*.cmake' \) -print0 | xargs -0 cmake-format -i
  ```

- Preview (non-destructive) for a single file:
  ```
  cmake-format CMakeLists.txt | diff -u CMakeLists.txt -
  ```
  For CI-style checks you can format in place and then verify no diffs:
  ```
  find . -type f \( -name 'CMakeLists.txt' -o -name '*.cmake' \) -print0 | xargs -0 cmake-format -i
  git diff --exit-code
  ```

- Editor integration:
  - VS Code: use an extension that runs `cmake-format` or configure a task to format on save.
  - CLion/Visual Studio Code/Qt Creator: configure an external tool or save action to call `cmake-format -i` on CMake files.

## Optional: pre-commit hook (cmake-format)

Using pre-commit is optional but recommended for consistent formatting on commit.

1) Install and enable:
```
pip install pre-commit
pre-commit install
```

2) Example .pre-commit-config.yaml snippet:
```
repos:
  - repo: https://github.com/cheshirekow/cmake_format
    rev: v0.6.13
    hooks:
      - id: cmake-format
        files: "\\.(cmake|CMakeLists.txt)$"
```

3) Run manually on demand:
```
pre-commit run -a
```

Tip: The hook respects the repository’s `.cmake-format.yaml`.

# Copyright and License

Thunder is Copyright 2018 Metrological and licensed under the Apache License, Version 2.0. See the LICENSE and NOTICE files in the top level directory for further details.
