# Update-a-file-through-a-Python-algorithm

Overview

This Python project automates the management of an allow list of IP addresses. It reads a list of approved IPs from a file (allow_list.txt), removes any IP addresses specified in a separate remove_list, and updates the file with the revised list. This ensures that restricted content is accessible only to authorized IP addresses.

Features

Reads the allow list from a text file.

Converts file contents from string to list for easy manipulation.

Iterates through a remove_list to remove unauthorized IPs.

Converts the updated list back to a string and rewrites the allow list file.

Simple, reusable function for automating IP management.

Usage

Prepare your files:

allow_list.txt: contains the approved IP addresses, separated by whitespace or new lines.

remove_list: a Python list of IP addresses to be removed.

Run the algorithm:

# Define the remove list
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

# Call the update_file function
update_file("allow_list.txt", remove_list)


Verify changes:

with open("allow_list.txt", "r") as file:
    text = file.read()
    print(text)

Function Description
def update_file(import_file, remove_list):
    # Read the allow list
    with open(import_file, "r") as file:
        ip_addresses = file.read()
    
    # Convert string to list
    ip_addresses = ip_addresses.split()
    
    # Remove IPs in remove_list
    for element in ip_addresses[:]:
        if element in remove_list:
            ip_addresses.remove(element)
    
    # Convert list back to string and overwrite file
    ip_addresses = "\n".join(ip_addresses)
    with open(import_file, "w") as file:
        file.write(ip_addresses)

How It Works

Opens the allow_list.txt file and reads its contents as a string.

Splits the string into a list (ip_addresses) for easier manipulation.

Iterates through the remove_list, removing any IPs found in ip_addresses.

Converts the updated list back into a string using .join() and overwrites the original file.

Benefits

Automates allow list maintenance.

Prevents unauthorized IP access.

Can be reused for other text-based lists of authorized entities.
