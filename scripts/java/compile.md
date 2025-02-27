# Compiling and Running Java Source Files with External Libraries

This guide provides commands to compile Java source files that depend on external libraries, such as `json-simple`, and to run the compiled program.

---

## Steps

1. **Compile Java Source Files with External Library**

    Use the `javac` command to compile Java files, specifying the `-cp` (classpath) option to include the external library:

    \`\`\`bash
    javac -cp json-simple-1.1.1.jar -d . *.java
    \`\`\`

    - **`-cp json-simple-1.1.1.jar`**: Sets the classpath to include the `json-simple` library. Adjust this path if the JAR file is located in a different directory.
    - **`-d .`**: Specifies the output directory for compiled `.class` files, which is the current directory in this case.
    - **`*.java`**: Compiles all `.java` files in the current directory.

2. **Run the Compiled Java Program**

    After compilation, use the `java` command to run the main class, including the library in the classpath:

    \`\`\`bash
    java -cp .:json-simple-1.1.1.jar PrescriptionManagement
    \`\`\`

    - **`-cp .:json-simple-1.1.1.jar`**: Sets the classpath to include both the current directory (where compiled classes are located) and the `json-simple` library. Use `;` instead of `:` on Windows (`-cp .;json-simple-1.1.1.jar`).
    - **`PrescriptionManagement`**: Replace with the name of your main class if it differs. This is the entry point of your Java program.

---

## Additional Notes

- **Classpath**: When working with multiple libraries, separate them with `:` on Linux/macOS or `;` on Windows.
- **Organization**: Consider placing your libraries in a dedicated folder (e.g., `libs/`) and adjust the `-cp` path accordingly (e.g., `-cp libs/json-simple-1.1.1.jar`).
- **Environment Variables**: Set the `CLASSPATH` environment variable to simplify classpath management for frequently used libraries.

By following these steps, you can compile and run Java programs that depend on external libraries, ensuring smooth integration and execution.
