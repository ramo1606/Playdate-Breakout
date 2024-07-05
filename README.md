# Breakout Game for Playdate

This is a Breakout-style game developed for the Playdate console using C89.

## Project Structure

```
breakout_playdate/
│
├── CMakeLists.txt
├── README.md
├── .gitignore
└── Source/
    ├── src/
    │   ├── main.c
    │   ├── game.h
    │   ├── game.c
    │   ├── paddle.h
    │   ├── paddle.c
    │   ├── ball.h
    │   ├── ball.c
    │   ├── brick.h
    │   ├── brick.c
    │   ├── utils.h
    │   └── utils.c
    ├── assets/
    │   ├── images/
    │   ├── sounds/
    │   └── music/
    └── tests/
        ├── CMakeLists.txt
        ├── minunit.h
        ├── test_paddle.c
        ├── test_ball.c
        └── test_brick.c
```

## Setup Instructions

1. **Install Playdate SDK**
   - Download and install the Playdate SDK from the official Playdate developer website.
   - Set the `PLAYDATE_SDK_PATH` environment variable to the SDK installation directory.

2. **Install Visual Studio 2022**
   - Download and install Visual Studio 2022 with C++ development tools.

3. **Install CMake**
   - Download and install CMake (version 3.14 or higher) from the official website.
   - Ensure CMake is added to your system PATH.

4. **Clone the Repository**
   - Clone this repository to your local machine:
     ```
     git clone https://github.com/yourusername/breakout_playdate.git
     cd breakout_playdate
     ```

5. **Configure CMake**
   - Open a command prompt in the project root directory.
   - Run the following commands:
     ```
     mkdir Build
     cd Build
     cmake -G "Visual Studio 17 2022" -A Win32 ..
     ```

6. **Build the Project**
   - Open the generated `breakout_playdate.sln` file in Visual Studio 2022.
   - Build the solution in both Debug and Release configurations.

7. **Run in Simulator**
   - In Visual Studio, set the `PlaydateSimulator` project as the startup project.
   - Press F5 to build and run in the Playdate Simulator.

8. **Compile for Playdate**
   - In Visual Studio, build the `PlaydateDevice` project.
   - The `.pdx` file for the device will be generated in the `Build/Debug` or `Build/Release` directory.

## Development Guidelines

- Use C89 (ANSI C) standard for all C code.
- Follow the Playdate SDK coding style as outlined in the official documentation.
- Use Allman brace style for all C code.
- Implement modular code by separating concerns into different files (e.g., paddle.c, ball.c, brick.c).
- Use sprites for game objects to optimize performance.
- Place all image assets in the `Source/assets/images/` directory.
- Place all sound effects in the `Source/assets/sounds/` directory.
- Place all music files in the `Source/assets/music/` directory.

## Testing

- Use the `minunit.h` single header library for unit testing.
- Write unit tests in the `Source/tests/` directory.
- Run tests by building and running the `Tests` project in Visual Studio.

## Version Control

- Use Git for version control.
- Commit frequently with meaningful commit messages.
- Use feature branches for developing new features.
- Create pull requests for code review before merging into the main branch.

## License

[Add your chosen license here]

