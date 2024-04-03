# FileAppender

FileAppender is a specialized Java utility crafted for appending or removing text blocks within `.tf` configuration files based on specific conditions. It was initially designed to automate configuration adjustments across a structured set of files within a defined project environment. This utility exemplifies a targeted solution to a particular business requirement, demonstrating the manipulation of file content under certain conditions.

## Features

- Conditional appending/removal of text blocks in `.tf` files, contingent on client names and module presence.
- Dual operation modes: `apply` for appending text and `undo` for removal.
- Configurable logging.

## Current Configuration

The utility is pre-configured with specific file paths and expects a certain directory structure and file naming convention:

- `baseDir`: Target directory for `.tf` files, set to a specific path within a development project.
- `clientNamesFile`, `payaraTextFile`, `defaultTextFile`: Paths to files containing client names and text blocks, tailored to the utility's current use case.

**Important Note**: The paths and logic embedded within FileAppender are tightly coupled with its initial deployment environment. It performs specific text manipulations based on a predetermined directory layout and file content criteria. **To adapt FileAppender for different projects or requirements, you'll likely need to modify the code**, especially the paths and the logic determining how text blocks are appended or removed.

## Requirements

- Java 8 or higher

## Configuration

Before running FileAppender, ensure the paths to the client names file, text block files, and the base directory are correctly set within the program:

- `baseDir`: The root directory to start the search for `.tf` files.
- `clientNamesFile`: Path to a text file containing the list of client names, one per line.
- `payaraTextFile`: Path to the text file containing the block of text to append/remove for files containing the "payara-client" module.
- `defaultTextFile`: Path to the text file containing the default block of text to append/remove.

## Usage

To use FileAppender, compile the Java file and run the program with the desired mode:

```shell
java FileAppender apply
java FileAppender undo
```

If no mode is specified at runtime, the program will prompt for one. It accepts `apply` to append text or `undo` to remove text from the targeted `.tf` files.

## Logging

FileAppender uses Java's built-in logging framework to log operations. By default, the logging level is set to `FINE`. Adjust the logging level within the program if necessary to suit your monitoring needs.
