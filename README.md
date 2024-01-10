# technical_tasks
# internsctl

A command-line tool for server administration tasks.

Overview
internsctl provides a convenient way to manage various server-related tasks, including:
  Retrieving system information (CPU, memory)
  Managing users (creating, listing)
  Obtaining file details

Make the script executable:
Bash
chmod +x internsctl

For using tool globally in linux terminal, move the script to /usr/local/bin with root user.

For installing manual page of this tool:
Bash
sudo install -g 0 -o 0 -m 0644 internsctl.1 /usr/share/man/man1/

Usage:
Bash
internsctl <command> [options] [arguments]

Commands:
  cpu getinfo: Get detailed CPU information.
  memory getinfo: Display memory usage information.
  user create <username>: Create a new user with a home directory.
  user list [--sudo-only]: List all users or only those with sudo privileges.
  file getinfo [options] <filename>: Display information about a file.

Options
  Global options:
    --help: Display the help message.
    --version: Print the script version.

  file getinfo options:
    --size, -s: Print the file size in bytes.
    --permissions, -p: Show file access permissions.
    --owner, -o: Display the file owner username.
    --last-modified, -m: Print the file's last modification time.

Screenshots
![1](https://github.com/rohanmehta98/technical_tasks/assets/54761819/f47f7c0c-5a9e-4d9d-8ebd-41f154ec321a)
![2](https://github.com/rohanmehta98/technical_tasks/assets/54761819/acee3c93-c1ae-468e-bc87-4ccd91ae3e8c)
![3 1](https://github.com/rohanmehta98/technical_tasks/assets/54761819/f2a48ea9-f81e-4cff-b363-b2f35da7efee)
![3 2](https://github.com/rohanmehta98/technical_tasks/assets/54761819/b1fbafba-d2ad-47e3-803d-0dd255a9abc3)
![4](https://github.com/rohanmehta98/technical_tasks/assets/54761819/287e2637-c178-49e7-a111-7109857392a4)
![5](https://github.com/rohanmehta98/technical_tasks/assets/54761819/1357ef2a-b61a-42cb-991f-ee5ee65afcbd)
![6](https://github.com/rohanmehta98/technical_tasks/assets/54761819/b2893ab9-d0a9-4586-a57a-d2ec9682076b)
![7](https://github.com/rohanmehta98/technical_tasks/assets/54761819/e008f723-a676-4fb6-9256-e48365f85e14)
![8](https://github.com/rohanmehta98/technical_tasks/assets/54761819/1d0e950e-93b4-48a5-957e-ed092a3f9aa1)
![9](https://github.com/rohanmehta98/technical_tasks/assets/54761819/1081aa7f-a76f-4779-bc0e-59a89c37be8b)
![10](https://github.com/rohanmehta98/technical_tasks/assets/54761819/b605dfaf-60a8-412f-8a1e-bcc226975524)
![11](https://github.com/rohanmehta98/technical_tasks/assets/54761819/02d0caf4-9281-480c-a883-6c0353ade277)
![12](https://github.com/rohanmehta98/technical_tasks/assets/54761819/9d29ce5a-ef05-41c2-be91-a6e615bf947e)
![13](https://github.com/rohanmehta98/technical_tasks/assets/54761819/528b2032-268e-4ef9-b445-554486fdaeee)


Authors
Rohan Mehta
