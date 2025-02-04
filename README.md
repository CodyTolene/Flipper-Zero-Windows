<div align="center">
  <img align="center" src=".github/images/blank-flipper.png" />
  <h2 align="center">Flipper Zero - Development Toolkit</h2>
  <p align="center">
    Hey there, fellow developer!
  </p>
  <p align="center">
    Welcome to the repository that houses a comprehensive and user-friendly guide for crafting your very own Flipper Zero application. By simply following along with this curated readme, and customizing it to your preferences along the way, you'll have your app up and published in no time. No need to reinvent the wheel, I've got your back!
  </p>
  <p align="center">
    Let's build something awesome together! 💪💻
  </p>
  <a href="https://shop.flipperzero.one/">
    <img src=".github/images/flipper-zero-buy-now.svg" />
  </a>
  <a href="https://docs.flipperzero.one/">
    <img src=".github/images/flipper-zero-docs.svg" />
  </a>
</div>

---

## Table of Contents <a name="index"></a>

- [Previews](#previews)
- [Hardware Requirements](#hardware-requirements)
- [Hardware Installation](#hardware-installation)
- [Firmware Installation](#firmware-installation)
- [Software Installation](#software-installation)
- [Software Guide](#software-guide)
- [Development Guide](#development-guide)
- [Flipper Application Catalog](#flipper-application-catalog)
- [Contributions](#contributions)
- [Special Thanks To](#special-thanks-to)
- [Donators](#donators)
- [Wrapping Up](#wrapping-up)

## Previews <a name="previews"></a>

Add in-app screenshot previews in this section or GIF's to demonstrate your application in action. You can use [ScreenToGif][link-screen-to-gif] to record GIF's of your application.

<!--
<img align="center" src=".github/images/preview_01.png" />
<img align="center" src=".github/images/preview_02.png" />
<img align="center" src=".github/images/preview_03.png" />
-->

<p align="right">[ <a href="#index">Back to top</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

## Hardware Requirements <a name="hardware-requirements"></a>

Define hardware requirements to run your application here. For example, if your application requires a Flipper Zero GPIO device, you would add a link to the Flipper Zero GPIO device here.

<p align="right">[ <a href="#index">Back to top</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

## Hardware Installation <a name="hardware-installation"></a>

Add hardware installation instructions here. Useful for when you need to demonstrate GPIO device pinout guides and the like.

<p align="right">[ <a href="#index">Back to top</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

## Firmware Installation <a name="firmware-installation"></a>

Add firmware installation instructions here. As an example this would be useful for when you need a guide for flashing a custom firmware to your Flipper Zero GPIO device. Add firmware files to the "firmware/" directory.

<p align="right">[ <a href="#index">Back to top</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

## Software Installation <a name="software-installation"></a>

Add software installation instructions here.

This repository includes GitHub Actions that lint and compile your application automatically. In the latest [GitHub Actions][link-github-action] for this repository you will find zip files containing the FAP application compatible with either the "dev" or "release" build of the latest Flipper Zero firmware. To manually install the application (for instance your application is not yet available in the [Flipper Application Catalog][link-flipper-application-catalog]) you can download those files and manually install them on your Flipper Zero device via USB.

<p align="right">[ <a href="#index">Back to top</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

## Software Guide <a name="software-guide"></a>

Demonstrate how the application works regarding the Flipper Zero's button layout. You can use this to guide your users on how to use your application more clearly.

| Button | Action                       |
| :----- | :--------------------------- |
| 🔼     | Up button does **\_\_**.     |
| 🔽     | Down button does **\_\_**.   |
| ◀️     | Left button does **\_\_**.   |
| ▶️     | Right button does **\_\_**.  |
| ↩️     | Back button does **\_\_**.   |
| 🔵     | Center button does **\_\_**. |

<p align="right">[ <a href="#index">Back to top</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

## Development Guide <a name="development-guide"></a>

1. Make sure you have [Git][link-git] and [Visual Studio Code][link-visual-studio-code] installed on your system.
2. Clone the repository and its submodule dependencies using the following command:
   ```bash
   git clone https://github.com/CodyTolene/Flipper-Zero-Development-Toolkit.git --recurse-submodules
   ```
3. Download and install [Python][link-python].
4. Open a new terminal in the "fap" directory of this project.
5. Run `py -m pip install --upgrade ufbt` to ensure you have the latest [uFBT][link-ufbt] installed.
6. Run `ufbt vscode_dist` to download the Windows toolchain and set up Visual Studio Code files.

   > ![Info][img-info] You may need to set your system PATH before running `ufbt` ie: `setx PATH "%PATH%;C:\Users\%USERNAME%\AppData\Local\Programs\Python\Python313\Scripts"`

7. Open the project "fap" directory ("fap") in Visual Studio Code. Make sure you have "Microsoft C/C++" extension installed and enabled.
8. In Visual Studio Code, open the command palette (CTRL+SHIFT+P) and type "C/C++ Edit Configurations (UI)" to find and open its settings. Add the following directory to the "Include path" option:
   ```
   ${workspaceFolder}/../.submodules/**
   ```
   This includes the Flipper Zero firmware library for your project (you can update it to a custom firmware if needed).
9. If Visual Studio Code shows import errors after saving the above settings from step 8, run the build script (see step 10) to resolve them.
10. It should now be possible perform various tasks within Visual Studio Code using Ctrl+Shift+B or "Terminal -> Run Task." Alternatively, you can use [uFBT][link-ufbt] scripts in the terminal. Here are some useful commands to get started:
    | Command | Description |
    | ------------- | -------------------------------------------------- |
    | `ufbt cli` | Starts a CLI session with the Flipper Zero device. |
    | `ufbt build` | Build the application. |
    | `ufbt lint` | Lint the application. |
    | `ufbt format` | Format the application. |
    | `ufbt launch` | Upload and start application over USB. |
11. You're now ready to begin programming your application within the directory "fap/" with "fap/toolkit.c" -> `toolkit_app(...)` being your entry point.
12. After making changes, linting, testing, etc., please refer to the [contributions section](#contributions) for a guide on how to submit your code for review (to make changes to this repo) or forking for your own use.

<p align="right">[ <a href="#index">Back to top</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

## Flipper Application Catalog <a name="flipper-application-catalog"></a>

Use the following flow to verify build requirements for the [Flipper Application Catalog][link-flipper-application-catalog]:

1. Open a new terminal at the root of this project.
2. Run `py -m venv venv` to install a [virtual environment][link-python-venv] for use.
3. Activate the virtual environment with the command `venv\Scripts\activate`.
4. Install the required dependencies by running `pip install -r .submodules/flipper-application-catalog/tools/requirements.txt`.
5. Ensure that "fap\manifest.yml" has the latest commit sha that will be used for submission. Also, verify that the version is correct.
6. Run `py .submodules/flipper-application-catalog/tools/bundle.py fap/manifest.yml bundle.zip` to verify and bundle the application.
7. If the above command succeeds, the application is ready for submission. Otherwise, fix any errors and try again.
8. Use `deactivate` to exit the virtual environment and return to your normal terminal.

For more information on Flipper Application Catalog contribution requirements, see [here][link-flipper-application-catalog-contribution].

<p align="right">[ <a href="#index">Back to top</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

## Contributions <a name="contributions"></a>

To create your own variation:

1. Fork the repository.
2. Add your code, push.

To add feedback to this repository:

1. Fork the repository.
2. Create a new branch with a descriptive name: `<username>/[<issue-#>]-<feature-or-bug-fix-desc>`
3. Refer to the Development Guide to get started. Program, commit changes, and push to your branch.
4. Publish a pull request [here][link-pull-request] for review from your branch.
5. Wait for review and merge. Thank you for your contribution!

<p align="right">[ <a href="#index">Back to top</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

## Special Thanks To <a name="special-thanks-to"></a>

- [Flipper Devices][link-flipper-devices] for providing the [Flipper Application Catalog][link-flipper-application-catalog], [uFBT][link-ufbt], their [firmware][link-flipper-zero-firmware], and the incredible [Flipper Zero][link-flipper-zero] hardware itself.
- Derek Jamison for his insightful [YouTube videos][link-derek-jamison-youtube] on Flipper Zero application development.
- GitHub user [leedave][link-leedave] for helping me learn more about Flipper Zero development by [boilerplate example][link-flipper-zero-boilerplate].
- The [Unleashed Firmware][link-unleashed] community and their valuable contributions.
- [WillyJL][link-github-profile-willyjl] for your guidance and wisdom, contributions to the F0 community, and the amazing [Momentum Firmware][link-flipper-zero-momentum-firmware]!
- [TalkingSasquach][link-github-profile-talkingsasquach] for your contributions to the F0 community, for all of your helpful [YouTube videos][link-youtube-talkingsasquach], and the [Discord community][link-discord-squachtopia]!
- [RogueMaster][link-github-profile-roguemaster] for your contributions to the F0 community, and the amazing [RogueMaster Firmware][link-flipper-zero-roguemaster-firmware]!
- The project images were drawn using the a application called "[link-lopaka][link-lopaka]" by [sbrin][link-github-profile-sbrin]. Thanks sbrin for your help in creating the images for this project!
- The Flipper Zero community for all your support and feedback!

<p align="right">[ <a href="#index">Back to top</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

## Donators <a name="donators"></a>

Below is a list of donators who have contributed to this project:

- rechtsanwalt.okan.dogan
- CodeAllNight (MrDerekJamison)
- RocketGod

Thank you for your support! 🙏

<p align="right">[ <a href="#index">Back to top</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

## Wrapping Up <a name="wrapping-up"></a>

Thanks to all the people and projects that made this possible! I hope you enjoy this project as much as I enjoyed working on it. If you have any questions, please let me know by opening an issue [here][link-link-url-new-issue].

| Type                                                                      | Info                                                           |
| :------------------------------------------------------------------------ | :------------------------------------------------------------- |
| <img width="48" src=".github/images/ng-icons/email.svg" />                | webmaster@codytolene.com                                       |
| <img width="48" src=".github/images/simple-icons/github.svg" />           | https://github.com/sponsors/CodyTolene                         |
| <img width="48" src=".github/images/simple-icons/buymeacoffee.svg" />     | https://www.buymeacoffee.com/codytolene                        |
| <img width="48" src=".github/images/simple-icons/bitcoin-btc-logo.svg" /> | bc1qfx3lvspkj0q077u3gnrnxqkqwyvcku2nml86wmudy7yf2u8edmqq0a5vnt |

Fin. Happy programming friend!

Cody Tolene

<p align="right">[ <a href="#index">Index</a> ]</p>

<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->
<!---------------------------------------------------------------------------->

<!-- IMAGES -->
[img-info]: .github/images/ng-icons/info.svg

<!-- LINKS -->

[link-derek-jamison-youtube]: https://www.youtube.com/@MrDerekJamison
[link-discord-squachtopia]: https://discord.gg/squachtopia
[link-flipper-application-catalog-contribution]: https://github.com/flipperdevices/flipper-application-catalog/blob/main/documentation/Contributing.md
[link-flipper-application-catalog]: https://github.com/flipperdevices/flipper-application-catalog
[link-flipper-devices]: https://github.com/flipperdevices/
[link-flipper-zero-boilerplate]: https://github.com/leedave/flipper-zero-fap-boilerplate
[link-flipper-zero-firmware]: https://github.com/flipperdevices/flipperzero-firmware
[link-flipper-zero-momentum-firmware]: https://github.com/Next-Flip/Momentum-Firmware
[link-flipper-zero-roguemaster-firmware]: https://github.com/RogueMaster/flipperzero-firmware-wPlugins
[link-flipper-zero]: https://docs.flipperzero.one/
[link-git]: https://git-scm.com/downloads
[link-github-action]: https://github.com/CodyTolene/Flipper-Zero-Development-Toolkit/actions
[link-github-profile-roguemaster]: https://github.com/RogueMaster
[link-github-profile-sbrin]: https://github.com/sbrin
[link-github-profile-talkingsasquach]: https://github.com/skizzophrenic
[link-github-profile-willyjl]: https://github.com/Willy-JL
[link-leedave]: https://github.com/leedave
[link-link-url-new-issue]: https://github.com/CodyTolene/Flipper-Zero-Development-Toolkit/issues
[link-lopaka]: https://github.com/sbrin/link-lopaka
[link-pull-request]: https://github.com/CodyTolene/Flipper-Zero-Development-Toolkit/pulls
[link-python-venv]: https://docs.python.org/3/library/venv.html
[link-python]: https://www.python.org/downloads/
[link-screen-to-gif]: https://www.screentogif.com/
[link-ufbt]: https://github.com/flipperdevices/flipperzero-ufbt
[link-unleashed]: https://github.com/DarkFlippers/unleashed-firmware
[link-visual-studio-code]: https://code.visualstudio.com/download
[link-youtube-talkingsasquach]: https://www.youtube.com/@TalkingSasquach
