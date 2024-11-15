# Installing Software from Massgrave Repository

The following command is used to download and execute a script from the Massgrave repository. This script is often used to automate software installations or configurations.

---

## Command

To run the installation, use the following command:

\`\`\`powershell
iwr -useb https://massgrave.dev/get | iex
\`\`\`

- **Explanation**:
  - **`iwr -useb`**: Stands for `Invoke-WebRequest -UseBasicParsing`. This part downloads the content of the URL without any complex HTML parsing.
  - **`https://massgrave.dev/get`**: The URL pointing to the script you want to execute.
  - **`| iex`**: Pipes the downloaded script to `iex` (Invoke-Expression), which runs the script immediately after downloading.

---

## Important Notes

- **Security Warning**: Be cautious when executing scripts directly from the internet, as it can expose your system to risks. Always verify the source and understand the contents of the script.
- **Administrative Privileges**: Running this command might require administrative privileges. Run PowerShell as Administrator if prompted.

By using this command, you automate the download and execution of a script from the Massgrave repository.
