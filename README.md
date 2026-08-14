# Sigma Spy

Sigma Spy is a Roblox remote spy for inspecting incoming and outgoing remote traffic. It supports Actors, remote grouping, decompilation, return spoofs, script dumps, mobile layouts, and a code editor.

## Recovery history

The original project was created by Depso under the `depthso` GitHub account. The original `depthso/Sigma-Spy` repository was later deleted, which broke its loadstring and its external parser and UI URLs.

The surviving recovery trail is:

1. `yukvx/Sigma-Spy` preserved an early standalone copy.
2. `WFYBGG/Spy` preserved the larger source, build files, assets, and commit history through the Beta 5 era.
3. Other public copies, including `Dexz00/Sigma-Spy`, preserved later edits and fixes.
4. This repository was rebuilt from the complete `WFYBGG/Spy` copy and published as `egoDtheTurtle/Sigma-Spy`.

Forks are listed for historical attribution. This repository is the maintained recovery copy and should be treated as the runnable release.

## Recovery changes

- `Main.lua` contains the runtime modules instead of downloading them.
- ReGui is bundled in `src/lib/ReGui.lua`.
- The parser is bundled in `src/lib/Roblox-parser.luau` using the interface expected by Sigma Spy's generation code.
- Configuration and return-spoof templates are embedded in `src/lib/Files.lua`.
- The release entrypoint has no runtime dependency on `depthso`, `yukvx`, `WFYBGG`, or any other raw GitHub URL.
- The original custom font remains in `assets/`; the default code font is used when an executor cannot load custom assets.
- The editable source is under `src/`. `Main.lua` is the bundled release file.

FastlyParse is the creator's newer parser project, but its public API differs from the parser API used by the recovered Sigma Spy generation module. The bundled compatibility parser is retained here to preserve the original feature set instead of silently dropping formatting, variable compression, or value replacement behavior.

## Features

- Actor support
- `__index` and `__namecall` hooking
- Incoming and outgoing remote logging
- Remote blocking
- Return value spoofs through `Return Spoofs.lua`
- Large-script decompilation support
- Variable compression and readable generated code
- Remote grouping
- Argument values in log titles
- Script and log dumping
- Mobile device support
- Pop-out editors and code editing
- Optional custom communication library

## Usage

Run `Main.lua` directly in a compatible Roblox executor. Do not use the old deleted-repository loadstring.

On first run, Sigma Spy creates its editable configuration files in the executor workspace folder:

- `Sigma Spy/Config.lua`
- `Sigma Spy/Return spoofs.lua`
- `Sigma Spy/assets/`

Use `ForceUseCustomComm` if the executor does not provide its communication library. The default configuration keeps the optional function patches disabled until confirmed by the user.

## Executor requirements

Required functions include:

- `hookmetamethod`
- `hookfunction`
- `getrawmetatable`
- `setreadonly`
- `getconnections`
- `newcclosure`
- File functions such as `isfile`, `writefile`, `isfolder`, and `makefolder`

Some executors may also need `getcustomasset`, `get_comm_channel`, or `create_comm_channel`. Those are optional because Sigma Spy has fallbacks.

## Source and licensing

The original project is MIT licensed. Dependency license copies are in `vendor/`. Preserve the original attribution when redistributing modified builds.

This repository contains recovered third-party code. Review the source and only run it in an environment you trust.
