# sts_lightspeed

For tree search and simulation of the popular rogue-like deckbuilder game Slay The Spire

**Features**
* c++ 17 compiled with gcc
* Standalone
* Designed to be 100% RNG accurate*
* Playable in console
* Speed: 1M random playouts in 5s with 16 threads
* Loading from save files (loading into combat currently only supported)
* Tree Search (best result, knowing the state of the game's rng)

**Planned Features**
* Tree search of possible game outcomes (not given the state of rng)

**Implementation Progress**
* All enemies
* All relics
* All Ironclad cards
* All colorless cards
* Everything outside of combat / all acts

**Getting Started**
* The project was built with Clion2021 and the [mingw64 toolchain](https://www.msys2.org/) on Windows 10
* The main target creates a simulator of the game that can be played in console.
* The test target creates a program with various commands that can be run, including random simulation
* Click the star button at the top of the repo :)

**Build tips**
Requires a C++17 compiler, Python 3.12 with development headers, and
Make or another CMake build tool. pybind11 is installed into the Python
environment rather than bundled as a submodule.

From the repository root on Linux or macOS:

```bash
git submodule update --init --recursive
python3.12 -m venv .venv
.venv/bin/python -m pip install -r requirements-build.txt
.venv/bin/cmake -S . -B build \
  -DCMAKE_BUILD_TYPE=Release \
  -DPython_EXECUTABLE="$PWD/.venv/bin/python"
.venv/bin/cmake --build build --parallel 4
```

On Windows, use the executables under `.venv\Scripts` and select an appropriate
CMake generator for your compiler. Build outputs include the `slaythespire`
Python extension and the `main`, `test`, and `small-test` executables. To import
the extension, add the build output directory to `PYTHONPATH`.

* If your build fails with an error about not-return-only `constexpr` methods, ensure your compiler supports c++17.
* If CLion shows an error about not finding python libs when loading the cmake project, try opening CLion from the msys2 shell.
