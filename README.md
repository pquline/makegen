# makegen

[`makegen`](./makegen) is a Bash script designed to automate the generation of source file lists in a Makefile from C source files in a structured project directory. It traverses the project's source directories and creates the necessary lines for inclusion in a Makefile, making it easier to manage and compile your project.

## Table of Contents

- [Features](#features)
- [Example Output](#example-output)
- [Usage](#usage)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Script Breakdown](#script-breakdown)
- [Customization](#customization)
- [Contributing](#contributing)

## Features

- **Automated Makefile Generation**: Automatically generates the necessary source file list for your Makefile based on your project structure.
- **Structured Output**: Neatly formatted and organized output in your Makefile.
- **Dynamic Pathnames**: Automatically detects subdirectories and creates corresponding variable names for them.
- **Easy Integration**: Can be easily added to your workflow with minimal setup.

## Example Output

Here's an example of what the output might look like when you run the script:

```makefile
# --------------------------------- PATHNAMES -------------------------------- #

SRC_FOLDER1			:=    folder1/
SRC_FOLDER2			:=    folder2/

# ---------------------------------- PROGRAM --------------------------------- #

SRC				+=    main.c

# ---------------------------------- FOLDER1 --------------------------------- #

SRC				+=    $(SRC_FOLDER1)file1.c
SRC				+=    $(SRC_FOLDER1)file2.c

# ---------------------------------- FOLDER2 --------------------------------- #

SRC				+=    $(SRC_FOLDER2)file3.c
SRC				+=    $(SRC_FOLDER2)file4.c
```
This output can be directly included in your Makefile.

## Usage

1. **Copy the Script**: Copy the `makegen` script provided in this repository to the root directory of your C project or any location you prefer.

2. **Run the Script**:
    ```bash
    ./makegen
    ```
    This will generate the necessary lines for your Makefile and output them to the console.

3. **Include the Output**: Copy and paste the generated lines into your Makefile.

### Optional: Create an Alias

To make the script easier to run from any project directory, you can add an alias to your shell configuration file (e.g., `.bashrc`, `.zshrc`):

1. **Move the Script**: Place the script in a directory of your choice, for example, `~/scripts/`.

2. **Edit Your Configuration File**:
    ```bash
    vim ~/.zshrc  # or ~/.bashrc
    ```

3. **Add an Alias**:
    ```bash
    alias makegen="bash ~/scripts/makegen"
    ```

4. **Reload Your Configuration**:
    ```bash
    source ~/.zshrc  # or ~/.bashrc
    ```

Now, you can simply run `makegen` from any project root directory to generate your Makefile entries.

## Installation

No installation is required. Simply copy the script into your project directory or create an alias for easy access.

## Project Structure

This script expects your project structure to look something like this:

```txt
project-root/
│
├── Makefile
├── srcs/
│ ├── main.c
│ ├── folder1/
│ │ ├── file1.c
│ │ └── file2.c
│ └── folder2/
│ │ ├── file3.c
│ │ └── file4.c
```

The script will detect `folder1` and `folder2` and generate Makefile entries for all `.c` files found within.

## Script Breakdown

Here's a breakdown of what the script does:

- **Define Source Directory**: The script starts by defining the source directory (`srcs`) where all the C source files are located.
- **Initialize Arrays**: It then initializes arrays to hold subfolder names and the formatted Makefile output.
- **Find Subfolders**: The script uses the `find` command to locate all subdirectories within the `srcs` directory.
- **Generate Headers**: For each subdirectory, the script generates a Makefile variable name based on the subfolder's name and lists all `.c` files within that subdirectory.
- **Output Generation**: The script formats this information into Makefile-compatible lines, ready to be copied into your Makefile.

## Customization

### Change the Source Directory

If your source files are located in a different directory, you can modify the `SRC_DIR` variable at the beginning of the script:

```bash
SRC_DIR="your_source_directory"
```
### Modify Header Width

If you need to change the width of the generated headers, adjust the TOTAL_WIDTH variable:

```bash
TOTAL_WIDTH=100  # or any other width
```

## Contributing

Contributions are welcome! If you have ideas for new features, find a bug, or want to improve the script, feel free to open an issue or submit a pull request.

### How to Contribute

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Make your changes and commit them.
4. Push your changes to your fork.
5. Submit a pull request.
