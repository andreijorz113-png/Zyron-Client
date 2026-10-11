# Zyron Client (V1)

Client-side Fabric utility mod for Minecraft **26.1.2** with a ClickGUI, per-module settings and a HUD editor.

- **Right Shift**: open the ClickGUI (rebindable in Controls)
- **Left-click** a module: toggle it
- **Right-click** a module: open its settings (sliders, colors, modes, checkboxes, keybind)
- **Right-click a category header**: GUI theme settings (accent color)
- **HUD Editor** (Misc panel): drag HUD elements, arrow keys nudge, R resets
- Config is saved to `config/zyron-client.json`

## Included in V1

- **Fullbright**: client-side infinite night vision
- **Storage ESP**: chests, trapped chests, ender chests, shulker boxes, barrels (plus hoppers, dispensers/droppers,
  furnaces, brewing stands, off by default). Per-type toggle and color (color alpha = fill opacity), outline/filled/both,
  through-walls toggle, range, outline thickness, scan interval
- **Music HUD**: current game music track with elapsed time
- **HUD Editor** and HUD elements: Watermark, Coordinates, FPS, Module List

Long settings windows scroll with the mouse wheel.

## Build

Needs JDK 25.

    gradle build          # or ./gradlew build after running `gradle wrapper`

The jar lands in `build/libs/zyron-client-1.1.0.jar`. Pushing to GitHub builds it automatically via
`.github/workflows/build.yml` (download it from the Actions run, or tag `v1.1.0` for a release).

## Adding a module

Extend `Feature`, call `add(new BoolSetting(...))` etc. for settings, override `onTick()`,
then `features.register(...)` in `ZyronClient`. It automatically gets a toggle dot, right-click
settings window, keybind and config persistence.

For use on your own worlds and servers you have permission to use client mods on.

## Install (players)

1. Install Fabric Loader for Minecraft 26.1.2 and Fabric API.
2. Drop `zyron-client-<version>.jar` into your `.minecraft/mods` folder.
3. Launch, join a world, press **Right Shift**.

## Develop

    gradle runClient      # launches Minecraft with the mod from source
    gradle build          # builds the jar

Open the folder in IntelliJ IDEA (Gradle project, JDK 25).
