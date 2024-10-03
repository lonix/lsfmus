# LSFMUS CONTEXT

This script is designed to manage and update Factorio mods by fetching the latest versions from the Factorio mod portal and downloading them if necessary. It uses a configuration file to store user-specific settings and relies on `jq` and `curl` for processing JSON data and making HTTP requests, respectively.

## Functions

### `load_config()`
- Loads the configuration from `lsfmus.config` located in `$HOME/.config` or the current directory.
- If the configuration file is not found, it creates a default configuration file and exits.
- Ensures that required variables (`MOD_DIR`, `USERNAME`, `TOKEN`) are set.

### `check_dependencies()`
- Checks if `jq` and `curl` are installed on the system.
- Exits with an error message if any of the dependencies are missing.

### `update_mods()`
- Fetches the list of enabled mods from `mod-list.json`.
- For each mod, it checks if the latest version is already installed.
- If not, it downloads the latest version from the Factorio mod portal.
- Updates global counters for the number of mods updated, already up-to-date, and failed to update.
- Executes commands based on the update results (`CMDON_UPDATE`, `CMDON_NOUPDATE`, `CMDON_FAILURE`).

## Global Variables
- `updated_count`: Counter for the number of mods updated.
- `uptodate_count`: Counter for the number of mods already up-to-date.
- `failed_count`: Counter for the number of mods that failed to update.

## Usage
1. Ensure `jq` and `curl` are installed.
2. Create and configure `lsfmus.config` with the necessary details (`MOD_DIR`, `USERNAME`, `TOKEN`).
3. Run the script to update the mods.

## Configuration File (`lsfmus.config`)
- `MOD_DIR`: Directory where mods are stored.
- `USERNAME`: Factorio username.
- `TOKEN`: Factorio token.
- `CMDON_UPDATE`: Command to execute when mods are updated.
- `CMDON_NOUPDATE`: Command to execute when no updates are necessary.
- `CMDON_FAILURE`: Command to execute when some mods fail to update.
- `CMDON_BEFORE`: Optional command to execute before updating mods.

## Summary
At the end of the script execution, a summary is printed showing the number of mods updated, already up-to-date, and failed to update.
