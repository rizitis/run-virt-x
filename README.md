# 🏃‍♂️-virt-x

`🏃‍♂️-virt-x` is a lightweight 🖥️📜 to 🏃 apps in a 🖼️ X 🌍 (`Xvfb`) on 🐧 Slackware. This 📜 cleans stale X ⚙️, starts a 🆕 `Xvfb` ⚙️, & runs the 🏁 app in the 🖼️ display 🌍.

## ✨ Features

- **🧹 Auto-Cleanup**: Stops active X ⚙️ on the chosen display.
- **🚮 Resource 🧹**: Clears `.X<DISPLAY>-lock` & `/tmp/.X11-unix/X<DISPLAY>` 🗂️.
- **📝 Error Logging**: Logs 🛑s to a 📂.
- **🔢 Custom Display**: Run 🖥️ on various 🌍s.
- **🤝 Graceful Exit**: Ends `Xvfb` post-app exit.

---

## 📋 Requirements

- `Xvfb` must exist 🛠️.
- 📦-free 📜 since Slackware 🐧 all ⚒️.

---

This script allows you to run graphical applications or tests in a virtual X server environment using Xvfb (X virtual framebuffer). It is designed to work on Slackware and other Linux distributions that support Xvfb.
Features

    Runs graphical applications and tests in a virtual X server using Xvfb.
    Supports both CMake and Meson build systems.
    Automatically detects the build system in your project and runs the corresponding test command.
    Provides options to specify the X server number and error log file.

Usage
Basic Command Format

./run-virt-x [OPTIONS] -- COMMAND

Where COMMAND can be:

    A graphical application to run.
    A test command (ctest for CMake or meson test for Meson).

Options:

    -n NUM: Specify the X server number (default: 99).
    -e FILE: Log errors to the specified file (default: /tmp/xvfb.log).
    -h: Display the help message and exit.

Examples:
Run a graphical application (e.g., Firefox) in a virtual X server:

./run-virt-x -n 101 -- firefox

Run CMake tests:

./run-virt-x -n 101 -- ctest --test-dir build --output-on-failure

Run Meson tests:

./run-virt-x -n 101 -- meson test -C build --output-on-failure

Requirements

    Xvfb (X virtual framebuffer)
    dbus-run-session (for running commands in a session with DBus support)
    CMake or Meson (depending on your project)
    make (for building the project, if needed)

Installation

    Ensure that Xvfb, dbus, CMake, and Meson are installed on your system.
    Make the script executable:

    chmod +x run-virt-x

    Run the script using the desired options.

How it works

The script performs the following steps:

    Detects the build system:
        If a CMakeLists.txt file is found, it assumes the project uses CMake.
        If a meson.build file is found, it assumes the project uses Meson.

    Starts an Xvfb instance:
        The script checks if an existing X server is running on the specified display and terminates it if necessary.
        A new X server is started using Xvfb on the specified display (default: :99).

    Runs the specified command:
        If CMake is detected, it runs ctest to execute the tests.
        If Meson is detected, it runs meson test to execute the tests.

    Cleans up:
        After running the command, the script cleans up by stopping the Xvfb server.

Notes

    You can use this script to run tests or graphical applications that require an X server environment, even on headless machines.
    The script uses dbus-run-session to ensure that commands like ctest or meson test run in a session with DBus support.
    The default X server display number is :99, but you can specify a different number using the -n option.

Troubleshooting

    If the script fails to start the Xvfb server, check the error log (/tmp/xvfb.log) for more details.
    Ensure that the appropriate build system is installed (either CMake or Meson) based on your project.
    If you encounter permission issues, ensure that the script has execute permissions (chmod +x run-virt-x).

---

## 🪪 License

🎁 [unlicense](https://unlicense.org). ⚠️ No ⛑️.

---

## ✍️ Author

✒️ For 🐧 Slackware fans 🛠️ stable graphical X ⚙️s.

---

