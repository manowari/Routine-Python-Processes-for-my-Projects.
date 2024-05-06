```bash
import os

def create_init_files(directory, custom_data=None):
    """
    Create '__init__.py' files in the given directory and all its subdirectories.

    Parameters:
        directory (str): The path to the directory where '__init__.py' files will be created.
        custom_data (str or None): Custom data to write into the '__init__.py' files.
                                    If None, empty '__init__.py' files will be created.

    Returns:
        None
    """
    for root, dirs, files in os.walk(directory):
        for dir_name in [root] + dirs:  # Include the current directory as well
            init_file_path = os.path.join(dir_name, "__init__.py")
            if custom_data:
                with open(init_file_path, "w") as init_file:
                    init_file.write(custom_data)
            else:
                open(init_file_path, "a").close()

if __name__ == "__main__":
    # Get the current directory
    current_directory = os.getcwd()

    # Define custom data to write into the '__init__.py' files
    custom_data = """
# This is a custom '__init__.py' file
# Feel free to add your own code here
"""

    # Call the function to create '__init__.py' files
    create_init_files(current_directory, custom_data)

