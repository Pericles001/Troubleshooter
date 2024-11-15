# Compiling C++ Source Files with External Libraries (jsoncpp)

This command compiles a C++ file (`ProductManager.cpp`) with the `jsoncpp` library, specifying the output directory and necessary include paths.

---

## Command to Compile with jsoncpp Library

To compile `ProductManager.cpp` and link it with `jsoncpp`, use the following command:

\`\`\`bash
g++ ProductManager.cpp -o tests/test_00_01 -ljsoncpp -I/usr/include/jsoncpp
\`\`\`

- **`ProductManager.cpp`**: The C++ source file to be compiled.
- **`-o tests/test_00_01`**: Specifies the output location and filename for the compiled binary. In this case, it will be located in the `tests` directory with the name `test_00_01`.
- **`-ljsoncpp`**: Links the `jsoncpp` library, enabling JSON parsing capabilities in the compiled program.
- **`-I/usr/include/jsoncpp`**: Specifies the path to the `jsoncpp` include files, which is necessary for the compiler to locate the library headers.

---

## Additional Notes

- **Library Path**: Ensure `jsoncpp` is installed, and the path (`/usr/include/jsoncpp`) points to the correct directory. If `jsoncpp` is installed elsewhere, adjust the path accordingly.
- **Directory Structure**: Organizing binaries in a `tests` folder helps maintain a clean project structure, especially for unit tests and debugging.
- **Compilation Optimization**: For development, add `-g` to include debugging symbols, or `-O2` for optimization in production builds.

By following these steps, you can compile C++ files with `jsoncpp` support, making it easy to manage JSON data within your C++ programs.
