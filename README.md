# Better Safe - On Demand Snapper Snapshot CLI

A simple command-line interface for creating BTRFS snapshots using snapper.

## Prerequisites

- A Linux distribution with BTRFS file system
- Snapper installed and configured

## Installation

1. Clone this repository or download the `bettersafe` script
2. Make the script executable (if not already):
   ```
   chmod +x bettersafe
   ```
3. Move the script to a directory in your PATH:
   ```
   sudo mv bettersafe /usr/local/bin/
   ```

## Usage

### Basic Usage

Simply run the command without any parameters to enter interactive mode:

```
bettersafe
```

You will be prompted to enter a description for the snapshot.

### With Description Parameter

You can also provide a description directly using the `-d` parameter:

```
bettersafe -d "My snapshot description"
```

Note: Any quotation marks in the description will be automatically removed.

## How It Works

The `bettersafe` CLI is a wrapper around the `snapper` command that simplifies the process of creating snapshots. It:

1. Checks if it's running with sudo privileges and automatically elevates if needed
2. Checks if snapper is installed
3. Accepts a description via parameter or interactive prompt
4. Removes any quotation marks from the description
5. Creates a snapshot using snapper
6. Displays detailed information about the created snapshot
7. Shows information about the previous snapshot and calculates how long ago it was taken

The output will show the complete snapshot details in the same format as `snapper list`, including:
- Snapshot number
- Type
- Date and time
- User
- Description

It will also show the previous snapshot's details and calculate the time difference between the two snapshots.

Example output:
```
Snapshot generated:
785  | single |       | Fri 18 Apr 2025 04:37:05 IDT | root |          | Testing

Previous snapshot:
784  | single |       | Fri 18 Apr 2025 04:30:12 IDT | root |          | Daily backup

Last snapshot was taken 6 minutes, 53 seconds ago.
```

The script automatically handles sudo privileges, so you don't need to manually type `sudo` when running the command. If the script detects it doesn't have the necessary privileges, it will re-run itself with sudo and prompt for your password if needed.

## Compatibility

This tool should work on any Linux distribution that supports BTRFS and has snapper installed, including:

- Ubuntu
- Fedora
- openSUSE
- Arch Linux
- And others

## Troubleshooting

If you encounter any issues:

1. Ensure snapper is properly installed and configured
2. Verify that you have the necessary permissions to create snapshots
3. Check that your file system is BTRFS
