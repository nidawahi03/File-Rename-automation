# File-Rename-automation
import os

def rename_files_in_directory(directory, prefix):
    try:
        # Get the list of files in the specified directory
        for filename in os.listdir(directory):
            # Construct the full file path
            old_file_path = os.path.join(directory, filename)

            # Check if it's a file (and not a directory)
            if os.path.isfile(old_file_path):
                # Create a new file name
                new_filename = f"{prefix}{filename}"
                new_file_path = os.path.join(directory, new_filename)

                # Rename the file
                os.rename(old_file_path, new_file_path)
                print(f'Renamed: {filename} -> {new_filename}')
            else:
                print(f'Skipped: {filename} (not a file)')

    except Exception as e:
        print(f"An error occurred: {e}")

# Usage
if __name__ == "__main__":
    directory_path = input("Enter the directory path: ")
    prefix = input("Enter the prefix to add: ")
    
    rename_files_in_directory(directory_path, prefix)

