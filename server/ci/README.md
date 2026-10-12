# Build and diagnostics

The server remains in the Project-Ravoc monorepo with its existing history and license. Run local commands from `server`; active GitHub Actions workflows are in `.github/workflows` at the repository root. GitHub Actions builds and tests Windows and Linux configurations. Linux server integration tests use a disposable MariaDB service, never a local game database.

## Profiles

Original presets preserve production compilation, runtime and optimization flags. Optional `windows-debug-cache`, `windows-release-cache`, `linux-debug-cache` and `linux-release-cache` presets include the same common header normally instead of generating a precompiled header, allowing persistent compiler object reuse. Cold builds can take longer; choose using measured configure, compile, test and cache times.

For example, after configuring `VCPKG_ROOT` and entering the appropriate compiler environment:

```sh
cmake --preset windows-release-cache
cmake --build --preset windows-release-cache --parallel 2
ctest --preset windows-release-cache
```

Dependency packages, verified source downloads and compiler objects have separate persistent caches. Package reuse is checked by vcpkg ABI; compiler reuse is checked by sccache/ccache. Build directories and installed dependency trees are not restored from a cache. Local cache/tool directories are ignored by Git.

Each build stage records exit status, elapsed wall time and complete output. Artifacts include tool/runner identity, compiler cache statistics, CMake configuration, Ninja task timings and CTest JUnit. Ninja task durations overlap and must not be interpreted as build wall time. Diagnostic and binary artifacts expire after 14 days. Binary artifacts require runtime resources from the repository; they are not complete game installations.

Lua syntax checks compile tracked scripts with LuaJIT without executing game code. Existing workflows inside the server directory are preserved; GitHub executes the new workflows from the repository root.

Local test presets run unit tests only; database integration tests require a separate disposable database. The missing schema was restored from the exact credited original server base, with provenance in `ci/schema-provenance.json`.

CI uses the measured profiles shown in the workflows and four parallel jobs. Original presets remain available. Server Debug has an opt-in unity/cache profile. Release production keeps LTO; fast test profiles use a separate non-LTO core.

A separate trusted cache-retention workflow runs without checking out repository code. It retains two compiler snapshots and one complete dependency snapshot per namespace/ref, preventing repeated snapshots from evicting dependency caches. CMake probe counters are recorded separately from source compilation.
