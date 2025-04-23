# assignment
File Read & Write Challenge 🖋️: Create a program that reads a file and writes a modified version to a new file.
Error Handling Lab 🧪: Ask the user for a filename and handle errors if it doesn’t exist or can’t be read.

def modify_file(filename):
  """Reads a file, modifies its content, and writes it to a new file.

  Args:
    filename: The name of the file to read and modify.

  Returns:
    None
  """

  try:
    with open(filename, 'r') as f:
      content = f.read()

    # Modify the content (for example, add a prefix to each line)
    modified_content = content.replace('\n', '\nModified: ')

    # Write the modified content to a new file
    with open(filename + '_modified.txt', 'w') as f:
      f.write(modified_content)

    print(f"File '{filename}' modified and saved as '{filename}_modified.txt'")

  except FileNotFoundError:
    print(f"Error: File '{filename}' not found.")
  except PermissionError:
    print(f"Error: Permission denied to read file '{filename}'.")
  except Exception as e:
    print(f"Error: An unexpected error occurred: {e}")

if __name__ == '__main__':
  filename = input("Enter the filename: ")
  modify_file(filename)
```

This program:

1. Gets the filename: Asks the user for the filename.
2. Opens the file: Uses `open(filename, 'r')` to open the file for reading.
3. Handles errors: Uses a `try...except` block to catch `FileNotFoundError` (if the file doesn't exist) and `PermissionError` (if the user doesn't have permission to read the file).
4. Reads the content: Reads the entire content of the file using `f.read()`.
5. Modifies the content: Replaces each newline character (`\n`) with "Modified: " (you can change this modification as needed).
6. Writes the modified content: Opens a new file with the name `filename_modified.txt` and writes the modified content to it using `f.write()`.
7. Prints a success message: Informs the user that the file has been modified and saved.

Explanation:

- `with open(filename, 'r') as f:`: This line opens the file in read mode (`'r'`). The `with` statement ensures that the file is automatically closed after it's no longer needed, even if an error occurs.
- `content = f.read()`: Reads the entire content of the file and stores it in the `content` variable.
- `modified_content = content.replace('\n', '\nModified: ')`: This line modifies the content by adding "Modified: " to the beginning of each line.
- `with open(filename + '_modified.txt', 'w') as f:`: This line opens a new file named `filename_modified.txt` in write mode (`'w'`). If the file already exists, it will be overwritten.
- `f.write(modified_content)`: Writes the modified content to the new file.
- `print(f"File '{filename}' modified and saved as '{filename}_modified.txt'")`: Prints a success message to the console.
