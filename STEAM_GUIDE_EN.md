# Minecraft × Teardown — installation and launch

By **Gefik23**.

This experimental mod connects two running games. A Workshop subscription alone is not enough: you also need the companion installer from the project's GitHub Releases. Minecraft and Teardown are obtained separately.

## Required downloads

- Windows x64 and Steam Teardown build **25295735**.
- [Prism Launcher](https://prismlauncher.org/download/).
- Your own Minecraft Java installation/account. Tested configuration: **26.3**, Fabric Loader **0.19.5**, Fabric API **0.161.0+26.3**, Java **25**.
- The attached companion installer ZIP from [GitHub Releases](https://github.com/Gefik23/minecraft-teardown-bridge/releases), when available. Do not choose the automatic Source code download. If the repository/release is private, wait for the public download; a subscription cannot replace these files.

## Optional modpack

The separate **Minecraft-only Prism modpack** is a convenient profile import. It contains the bridge mod, Fabric API and settings, without either game's client or assets. Import its ZIP using **Add instance → Import** in Prism. It does not install the Teardown bridge/compositor: the companion installer is still required.

The companion installer already creates a Prism profile, so the separate import is optional. Authentication and game downloads remain the launcher's responsibility. No account bypass or bundled pirated game is provided. Other compatible Fabric profiles may use the included mod JAR, but other launchers have not been tested.

## Setup

1. Install Prism, complete its normal Minecraft sign-in and run it once. Close both games.
2. Extract the companion installer to a writable folder. Do not run it inside the ZIP.
3. Run **INSTALL.cmd**. It finds Teardown and Prism, checks compatibility, installs the host mod, separate Minecraft profile and GPU compositor. The official ReShade download is checksum-verified.
4. If the installer reports an unsupported build, existing loader or profile, read its message. It preserves unrelated files and worlds; do not delete them blindly.
5. Restart Prism. Launch **Teardown Bridge Workshop** and wait for its world to load.
6. Keep Minecraft open and unminimized; switch to Teardown.
7. Enable **Minecraft x Teardown Bridge**, then load a sandbox. Enable only one Lua copy if you have both the local mod and Workshop copy.
8. Run **START_BRIDGE.cmd** from the extracted companion folder. Leave its console open and wait for the Minecraft connection message.
9. Press **F7** in Teardown to activate the bridge.

For nonstandard paths, run `INSTALL.ps1` with `-TeardownPath` and `-PrismInstances` pointing to their actual folders.

## Controls

- **F7:** enable/disable the bridge.
- **1–9 / mouse wheel:** select an item.
- **Left / right mouse:** attack/use.
- **I:** open/close Minecraft inventory. Mouse interaction inside inventory currently requires the Minecraft window.
- **E:** normal Teardown interaction, including doors and vehicle entry/exit.
- **C:** first-person view remains enforced while active.

Hands and inventory hide in vehicles and return after exiting. Minecraft music is muted in the profile. Teardown health appears at the top right. Death uses a **You died!** screen without a death reason; button availability and actions remain controlled by Teardown.

## Troubleshooting

- **No hands/HUD:** check the loaded Minecraft world, Lua mod, bridge console and F7.
- **Connection lost:** the bridge retries. Press F7 after recovery if it disabled itself.
- **Another bridge is running:** close the previous console; use one bridge at a time.
- **No image after minimizing Minecraft:** restore its window. Minimized rendering is not supported.
- **Existing ReShade or unsupported build:** differing files are not overwritten. This configuration needs separate compatibility testing.
- **Low FPS:** start in a normal sandbox, disable other global mods/overlays, close heavy applications and keep the Minecraft profile's resolution unchanged for the first test.
- **Crash or stalled level transition:** preserve Teardown's `ReShade.log`, the Prism profile's `logs/latest.log` and the bridge's `live-link-status.json`. Remove personal information before sharing logs. A stalled level transition remains under investigation.

## Known limits

Single-player only. Teardown quicksave does not create a synchronized backup of Minecraft. Moving TNT, sharp vehicle turns and destroyed supports need more testing. The ground, raised-object and moving-vehicle creeper checks cover specific cases, not every surface. This is an experimental alpha, not an official Mojang or Tuxedo Labs add-on.

## Removal

Disable the bridge and close both games. Run **UNINSTALL_NATIVE.ps1** from the companion package through PowerShell. It removes only added files whose checksums still match and restores the original HUD presentation. Disable/unsubscribe from the Lua mod. Remove the separate Prism instance through Prism if desired; the uninstaller does not delete Minecraft worlds.

## Credits

Author: **Gefik23**. Based on rehan / universal-modder (MIT), developed with assistance from OpenAI Codex. ReShade: crosire; Fabric API: FabricMC. Cover artwork generated with OpenAI image generation. Library licenses are included. Neither game's files are redistributed.
