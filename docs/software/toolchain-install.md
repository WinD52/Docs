---
template: main.html
---

<img src="https://raw.githubusercontent.com/ExpressLRS/ExpressLRS-Hardware/master/img/software.png">

**Note:** The following section is intended for advanced users who intend to dabble with the source code directly.

## Toolchain Setup (Advanced)

`ExpressLRS` is written in C++ using the Arduino framework. 

 * Rather than using the Arduino IDE (which let's face it, 🗿 is pretty clunky), we use [platformio](https://platformio.org/)
 * To ease the use of `pio` we recommend to use the [according extension](https://platformio.org/install/ide?install=vscode) for `Visual Studio Code`

### PlatformIO

1. 🔽 **Download** a copy of [vscode](https://code.visualstudio.com/) for your computer 
2. 📂 **Open** vscode, and click on the "__Extensions__" icon in the toolbar on the right (see [Managing Extensions](https://code.visualstudio.com/docs/editor/extension-gallery) 📘)
3. 🔎 In the search box, enter `platformio`, and **install** the **extension** (see [the `pio install` documentation](https://platformio.org/install/ide?install=vscode) 📚)

### Git Setup

We recommend using VSCode's built-in Git client, as it requires the least 3rd party software 🤖.

1. 🔽 **Download** a copy of [git](https://git-scm.com/downloads) (this is also needed for `PlatformIO`)
2. Install `git`, click **yes** to the default options (there are a **LOT** 💯)
3. IMPORTANT! Make sure you select this option during install, it adds git to PATH which is necessary for VScode cloning (the next step). 

<img src="https://raw.githubusercontent.com/ExpressLRS/ExpressLRS-hardware/master/img/git_path_option.png" width=50%>


### Cloning the Repo
* In VSCode open the `command pallete` (using `Cmd+Shift+P` on MacOS or `Ctrl+Shift+P` on Windows)
* Enter `Git: Clone` 

<img src="https://cdn.discordapp.com/attachments/738450139693449258/771844893642457128/Screen_Shot_2020-10-30_at_2.15.56_PM.png" width=100%>

* Click that! 👈 
* Then, enter ExpressLRS Repo URL -> `https://github.com/AlessandroAU/ExpressLRS.git` 💻 
* Choose a folder for ExpressLRS. 📂 

### Selecting the Latest Release
Before we can do any building, you need to select a release build of ELRS. For example, release [0.1.0-RC1](https://github.com/AlessandroAU/ExpressLRS/releases/tag/0.1.0-RC1). In Visual Studio Code select that tag. The location of the selector is shown below. 🖱️ 

<img src="https://media.discordapp.net/attachments/738450139693449258/796510597041881088/Screen_Shot_2021-01-06_at_2.48.38_PM.png?width=2330&height=1456" width=40%>
<img src="https://cdn.discordapp.com/attachments/738450139693449258/796510905605029918/Screen_Shot_2021-01-06_at_2.49.52_PM.png" width=38.5%>

Click the selector, and then type in the name of the tag, in this case `0.1.0-RC1`. 

### PlatformIO Building

Once you had the time of your life setting up your toolchain 🧰 you are **ready** to Flash ⚡ ExpressLRS to supported [hardware](https://github.com/AlessandroAU/ExpressLRS/wiki/Supported-Off-The-Shelf-Hardware).

### Building Targets using PlatformIO

1. 📂 When you first launch `Visual Studio Code`, you should see the `PlatformIO Home Page` in a tab.
Click the `Open Project` button. Navigate to the `ExpressLRS` repo directory. Navigate into the `src` folder (i.e. `./ExpressLRS/src/`). Finally, press the `Open` button.
2. ✏️ Edit the file [`./src/user_defines.txt`](https://github.com/AlessandroAU/ExpressLRS/blob/master-dev/src/user_defines.txt) to define user specific variabls. 😈 Please make sure you did edit the file according to __your__ needs! 
3. 📊 In the toolbar on the left, click the PlatformIO icon, which will show the list of tasks. Now, select Project Tasks, expand your desired target and select Build/Upload (depending on the method). You should see the result in the terminal.
4. 🙃 If something went wrong - please check the `Terminal`, too. It will contain at least a hint on what the issue is. Please ask the [community](https://github.com/AlessandroAU/ExpressLRS/wiki#community) for further help🧑‍🔧!

## Updating your Local Repo

You've cloned the repository and are now wondering how to get new updates down the line? Then this document is meant for you!
Here's a primer on how to keep your local copy of the repository up-to-date.

### Method 1: The Clean Way - Fetch & Reset

Probably the **easiest and least troublesome method**, however, it'll overwrite any changes you've made to your local copy. :warning:

1. Open the terminal

    You can either straight up open `bash/cmd` and navigate to your project folder or open an integrated terminal in VSCode:

    - Open the `command pallete` (using `Cmd+Shift+P` on MacOS or `Ctrl+Shift+P` on Windows)
    - Enter: `Create New Integrated Terminal`

        ![Terminal](../assets/images/vscodeTerminal.png)

2. In the terminal, type: `git fetch -pu && git reset --hard origin/master`

    This will get you the latest version and destroy any local changes you've made.

### Method 2: The lazy way - Commit, Pull & Merge

The advantage this method has over the first method is that all your changes to the user_defines.txt (or any other file, for that matter) will get merged together with any new updates. There's a possibility that, if changes are too big, you could end up with a merge conflict. If that doesn't appeal to you, stick to the first method.

1. Commit your changes to your local repository

    - In VSCode open the `command pallete` (using `Cmd+Shift+P` on MacOS or `Ctrl+Shift+P` on Windows)
    - Enter: `Git: Commit`

        VSCode will tell you that there are unstaged changes and ask if you want to add them to the commit. Confirm this! This will just commit your changes to the user_defines.txt to your local repository. No worries, you're not overwriting anything on github! :octocat:

2. Open the terminal, how-to is detailed in method 1

3. In the terminal, type: `git pull -f`

    This will pull a new revision of the remote repository to your own local repository and automatically merge it with your own changes.