# Minecraft
Minecraft is a **Linux-native** game that works using **OpenGL**.
## Get Started
First of all, I definitely suggest you to use [Prism Launcher](https://github.com/PrismLauncher/PrismLauncher) because it is **open-source** and provides more options than the original launcher.
### Install Prism Launcher
You can install Prism Launcher following [these steps according to your distribution](https://prismlauncher.org/download/linux/), the recommended way is installing it from Flatpak and it will configure everything itself including Java builds.
### Install Java
Prism Launcher now allows you to install Java inside the app instead of installing manually. To do so, follow the steps below:
- `Settings - Java - Management - Download - Adoptium - Install the latest builds for all 3 Java versions`
  - After installing Java, if Minecraft doesn't launch, change the instance's Java build to the relevant one.
    - **For 1.20.5 and above:** Java 21
    - **From 1.18 to 1.20.4:** Java 17
    - **For 1.17 and 1.17.1:** Java 16 - but in the app, there is no Java 16 in Adoptium, so you might want to install another Java build if you want to play the specific version.
    - **For 1.16.5 and below:** Java 8
### Install Minecraft
- When you first launched the launcher, it'll ask you what language would you like to use. After that question, you're going to see a page about Java.
- Make sure to change `Maximum memory allocation`. Some people claim you should allocate half your RAM but this is not good for **some cases**. If you have at least 32 GB RAM and don't perform RAM intensive tasks, you can allocate half your RAM. However:
  - If you have **4/6/8/12/16 GB RAM**, I suggest you to allocate **2048 MiB** if you're not going to install heavy mods or shaders. However, you should allocate at least **3072 MiB** RAM if you're going to use Optifine without mods.
- After completing quick setup, add your Microsoft account to connect to your account in the launcher.
- Now we can finally install Minecraft. Let's click on `Add Instance` button on top left and continue:
  - On `Version` section, choose the version you'd like to play and scroll down a bit. You should see a big "**No mod loader is selected.**" warning. There is a `Mod loader` section next to the warning. We're going to choose **Fabric** from there and hit `OK`.
## Optimization
### Before Getting Started
- **OpenGL and Java** are already **better optimized** on Linux. However, we can still boost our GL performance, we're going to add an **environment variable**. I'm not sure about GNOME but on XFCE and KDE, adding an environment variable for **non Flatpak** version is possible via these steps:
  - Right click on Prism Launcher and go to `Properties`
    - **For XFCE**: Make sure `command` section looks like this:
      - **For Intel/AMD GPUs:**
      ```
      env mesa_glthread=true prismlauncher %U
      ```
      - **For NVIDIA GPUs:**
      ```
      env __GL_THREADED_OPTIMIZATIONS=1 prismlauncher %U
      ```
    - **For KDE**: Go to `Application` section and make sure `environment variables` section looks like this
      - **For Intel/AMD GPUs:**
      ```
      mesa_glthread=true
      ```
      - **For NVIDIA GPUs:**
      ```
      __GL_THREADED_OPTIMIZATIONS=1
      ```
- If you installed the launcher from **Flatpak**, you might not be able to add environment variable using the previous steps. However, you can add an environment variable via a custom **.desktop** file. You can follow these steps to do so:
  -  Create a *.desktop* file and edit it via text editor. Paste the content below and save the file:
-  **For Intel/AMD GPUs:**
```
[Desktop Entry]
Name=Prism Launcher
Comment=Prism Launcher
Exec=env mesa_glthread=true flatpak run org.prismlauncher.PrismLauncher %U
Icon=org.prismlauncher.PrismLauncher
Terminal=false
Type=Application
Categories=Game;
```
  - **For NVIDIA GPUs:**
  ```
[Desktop Entry]
Name=Prism Launcher
Comment=Prism Launcher
Exec=env __GL_THREADED_OPTIMIZATIONS=1 flatpak run org.prismlauncher.PrismLauncher %U
Icon=org.prismlauncher.PrismLauncher
Terminal=false
Type=Application
Categories=Game;
```
- Another and an easier way is to run Prism Launcher via terminal using one of the commands for your GPU like this:
  - **For non Flatpak version:**
  ```
  mesa_glthread=true prismlauncher
  ```
  - **For Flatpak version:**
  ```
  mesa_glthread=true flatpak run org.prismlauncher.PrismLauncher
  ```
- Now, let's enable some settings for even better performance in Prism Launcher.
  - Click on `Settings` and go to `Minecraft` section and click on `Tweaks`. Enable `Enable Feral GameMode` (only if you have gamemode installed) and `Use discrete GPU` (only if you have 2 GPUs).
- If you reached here, you are ready to play vanilla Minecraft. However since this guide is also an optimization guide, I assume that you'd like to continue reading. Next, I will show you how to optimize your game via **Sodium** or **Optifine**. Let's go!
## Sodium Method - Recommended For Version 1.16.3 And Later
- Now, let's install some performance mods! I will be installing mods for **1.20.1** version, that means if you are going to use a newer version of the game, some of those mods **may not** be available for the version you play.
- First of all, click on your Minecraft instance once and then click on `Edit` from the right side bar.
- In the opened page, click on `Mods` from the left side bar and click on `Download mods` from the right side bar and make sure `Modrinth` is selected. We're ready to install some mods!
  - Don't forget to click on `Select mod for download` after selecting each mod.
- These are the mods I suggest you to use for a smoother gameplay with similar features of Optifine:
  - `Alternate Current`
  - `Async Locator`
  - `BadOptimizations`
  - `Bedrodium`
  - `Blanket`
  - `Capes` - Optional, it allows you to use capes. However, I suggest you to use **MinecraftCapes** Mod with it if you don't have your own capes because this mod allows you to use capes for free. You can check [their website](https://minecraftcapes.net/) for more information.
  - `Cloth Config`
  - `Clumps`
  - `Concurrent Chunk Management Engine`
  - `Continuity` - Optional, it provides connected textures feature just like how Optifine does.
  - `CoroUtil`
  - `Cull Leaves`
  - `Disable Custom Worlds Advice`
  - `Dynamic FPS`
  - `Enhanced Block Entities`
  - `EntityCulling`
  - `Exordium`
  - `Fabric API`
  - `Fabric Language Kotlin`
  - `Fast Items`
  - `Faster Random`
  - `FastQuit`
  - `FerriteCore`
  - `Fzzy Config`
  - `Icterine`
  - `ImmediatelyFast`
  - `Indium`
  - `Iris` - Optional, it allows you to use shaders just like how Optifine does.
  - `Krypton`
  - `Ksyxis`
  - `LambDynamicLights` - Optional, it allows you to use dynamic lighting just like how Optifine does.
  - `LazyDFU`
  - `Let Me Despawn`
  - `Lithum`
  - `Memory Leak Fix`
  - `Mobtimizations`
  - `Model Gap Fix`
  - `ModernFix`
  - `More Culling`
  - `More Culling Extra`
  - `No Chat Reports`
  - `No Report Button`
  - `No Resource Pack Warnings`
  - `No Telemetry`
  - `Noisium`
  - `Noxesium`
  - `Particle Core`
  - `Reese's Sodium Options`
  - `Remove Reloading Screen`
  - `Skip Transitions`
  - `Sodium`
  - `Sodium Extra`
  - `Starlight`
  - `StutterFix`
  - `ThreadTweak`
  - `Zoomify` - Optional, it allows you to zoom via C keybind just like how Optifine does.
### Sodium - In Game Optimized Settings
- **If you're going to use Zoomify**:
  - Click on `Options` and go to `Controls` - `Key Binds` and scroll down until you see a red key bind.
  - `Save Hotbar Activator` has C button as a key bind, change it to something else and hit `Done`
- Go to `Options` and go to `Resource Packs`. Now move `Default Connected Textures` and `Glass Pane Culling Fix` from left section to right section and hit `Done`.
- Go back to `Options` and go to `Video Settings`. These are optimized settings for performance:
  - **General**
    - `Render Distance`: 6 chunks
    - `Max Shadow Distance`: Disabled
    - `Simulation Distance`: 5 chunks
    - `VSync`: OFF
    - `Max Framerate`: Same number as your monitor's refresh rate (for 60 hz screens, change the value to 70)
  - **Quality**
    - `Graphics`: Fast
    - `Clouds`: OFF
    - `Weather`: Fast
    - `Leaves`: Fast
    - `Particles`: Decreased
    - `Biome Blend`: 1 block(s)
    - `Entity Distance`: 50%
    - `Entity Shadows`: OFF
    - `Distortion Effects`: 60%
    - `FOV Effects`: 60%
    - `Mipmap Levels`: 1x
- We're done!
## Optifine Method - Recommended For Version 1.16.2 And Earlier
- For Optifine, you should use **Forge** mod loader instead of **Fabric**.
- First of all, install [Optifine](https://optifine.net/downloads) for the Minecraft version you want to play.
- Next, click on your Minecraft instance once and then click on `Edit` from the right side bar.
- In the opened page, click on `Mods` from the left side bar and drag **Optifine file** into the page.
### Optifine - In Game Optimized Settings
- Go to options
  - **Video Settings**
    `Graphics`: Fast
    - `Smooth Lighting`: ON
    - `Smooth Lighting Level`: 50%
    - `Render Distance`: 6 chunks
    - `Simulation Distance`: 5 chunks
    - `Max Framerate`: Same number as your monitor's refresh rate (for 60 hz screens, change the value to 70)
    - `Entity Shadows`: OFF
    - **Quality...**
      - `Mipmap Levels`: 1
      - `Emissive Textures`: OFF
      - `Custom Fonts`: OFF
      - `Connected Textures`: Fast
      - `Custom Sky`: OFF
      - `Custom Entity Models`: OFF
      - `Random Entities`: OFF
      - `Custom Colors`: OFF
      - `Natural Textures`: OFF
      - `Custom Items`: OFF
      - `Custom GUIs`: OFF
      - `Distortion Effects`: 60%
      - `FOV Effects`: 60%
    - **Details...**
      - `Clouds`: OFF
      - `Trees`: Fast
      - `Fog`: OFF
      - `View Bobbing`: OFF
      - `Vignette`: Fast
      - `Rain & Snow`: Fast
      - `Stars`: Subjective
      - `Swamp Colors`: OFF
      - `Alternate Blocks`: OFF
      - `Entity Distance`: 50%
      - `Biome Blend`: 3x3
    - **Performance...**
      - `Render Regions`: OFF
      - `Smart Animations`: ON
      - `Smooth FPS`: ON
      - `Fast Render`: ON
      - `Fast Math`: ON
      - `Smooth World`: ON
    - **Animations...**
      - `Redstone Animated`: OFF
      - `Rain Splash`: OFF
      - `Lava Animated`: OFF
      - `Dripping Water/Lava`: OFF
      - `Textures Animated`: OFF
      - `Particles`: Decreased
    - **Other...**
      - `Telemetry`: OFF
- We're done! 
## Conclusion
So, that was my Minecraft installation and optimization guide! I hope you enjoyed it while reading and I hope the guide can be useful for you. Have a nice day! 🐧
