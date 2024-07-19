# Breakout Game for Playdate

This is a modern take on the classic Breakout game, developed for the Playdate handheld gaming system. The game features enhanced gameplay mechanics, visual effects, and power-ups, all implemented in C using the Playdate SDK.

## Project Structure

```
Playdate-Breakout/
│
├── CMakeLists.txt
├── README.md
├── .gitignore
├── docs/
└── Source/
    ├── include/
    │   ├── game.h
    │   ├── paddle.h
    │   ├── ball.h
    │   ├── brick.h
    │   └── utils.h
    ├── src/
    │   ├── main.c
    │   ├── game.c
    │   ├── paddle.c
    │   ├── ball.c
    │   ├── brick.c
    │   └── utils.c
    ├── lib/
    ├── assets/
    │   ├── images/
    │   ├── sounds/
    │   ├── music/
    │   └── levels/
    └── tests/
        ├── CMakeLists.txt
        ├── minunit.h
        ├── test_paddle.c
        ├── test_ball.c
        └── test_brick.c
```

## How to Build

To build this project, you'll need the Playdate SDK and CMake installed on your system. [Playdate Building on Windows](https://sdk.play.date/2.5.0/Inside%20Playdate%20with%20C.html#_building_on_windows)

1. Set up the Playdate SDK:
   - Download and install the [Playdate SDK](https://play.date/dev/).
   - Set the `PLAYDATE_SDK_PATH` and `SDK` environment variables to point to your SDK installation.

2. Set up GNU ARM Embedded Toolchain
   - Download and install the [GNU Arm Embedded Toolchain](https://developer.arm.com/downloads/-/gnu-rm/10-3-2021-10).
   - Set the `PLAYDATE_ARM_GCC` environment variable to point to C:\Program Files (x86)\GNU Arm Embedded Toolchain\10 2021.10

3. Clone this repository:
   ```
   git clone https://github.com/ramo1606/Playdate-Breakout.git
   cd breakout_playdate
   ```

4. Create a build directory and run CMake:
   ```
   mkdir build
   cd build
   cmake ..
   ```

5. Build the project:
   - For Visual Studio: Open the generated `.sln` file and build the project.
   - For Make: Run `make` in the build directory.

6. To build for the Playdate device:
   - Open a Visual Studio Developer Command Prompt from the Start Menu or from within Visual Studio
   ```
   cmake .. -G "NMake Makefiles" --toolchain=C:/Users/Ramo/Documents/PlaydateSDK/C_API/buildsupport/arm.cmake -DCMAKE_BUILD_TYPE=Release
   nmake
   ```

7. The output will be a `.pdx` file, which can be run on the Playdate simulator or transferred to a Playdate device.

## Running Tests

This project includes a test suite using the minunit testing framework. To build and run the tests:

1. From the main build directory:
   ```
   cmake ..
   make
   make test
   ```

2. Or, to build and run tests directly:
   ```
   cd tests
   cmake .
   make
   ./run_tests
   ```

The test setup is configured in two CMakeLists.txt files:

- The main CMakeLists.txt file in the project root includes the tests subdirectory.
- The CMakeLists.txt file in the tests directory sets up the test executable and links it with the main project.

If you add new test files or need to include additional resources for testing, you'll need to update the tests/CMakeLists.txt file accordingly.

## Coding Style

This project follows a specific coding style to maintain consistency and readability:

1. **C Standard**: We use C89 (ANSI C) to ensure maximum compatibility with the Playdate SDK.

2. **Naming Conventions**:
   - Use descriptive names for functions, variables, and types.
   - Functions use camelCase: `updateGameState()`, `drawPaddle()`.
   - Variables use camelCase: `playerScore`, `ballSpeed`.
   - Constants and macros use UPPER_SNAKE_CASE: `MAX_PLAYERS`, `INITIAL_BALL_SPEED`.
   - Typedef structs use PascalCase: `typedef struct { ... } GameState;`

3. **Braces**: We use Allman style braces:
   ```c
   if (condition)
   {
       // code
   }
   else
   {
       // code
   }
   ```

4. **Indentation**: Use 4 spaces for indentation, not tabs.

5. **Comments**: 
   - Use C-style comments for multi-line explanations: `/* ... */`
   - Use C++-style comments for single-line comments: `// ...`
   - Each function should have a brief comment explaining its purpose.

6. **File Structure**:
   - Each `.c` file should have a corresponding `.h` file.
   - Use include guards in header files:
     ```c
     #ifndef GAME_H
     #define GAME_H
     // content
     #endif /* GAME_H */
     ```

7. **Modularity**: Keep functions small and focused on a single task. If a function grows too large, consider breaking it into smaller functions.

8. **Error Handling**: Use appropriate error handling mechanisms. Return error codes or use the Playdate SDK's error handling functions where appropriate.

9. **Documentation**: Use C-style documentation comments for functions in header files:
   ```c
   /**
    * @brief Updates the game state for one frame
    * @param game_state Pointer to the current game state
    * @param delta_time Time elapsed since last frame in seconds
    * @return 0 on success, non-zero error code on failure
    */
   int update_game_state(GameState* game_state, float delta_time);
   ```

Please adhere to these guidelines when contributing to the project. Consistent style helps maintain code readability and makes collaboration easier.

## License

[Include your chosen license here]

## Contributing

[If you want to accept contributions, include guidelines here]