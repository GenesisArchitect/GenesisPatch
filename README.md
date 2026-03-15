 Genesis Plugin Development Guide
Welcome to the Aether Plugin Engine. This guide outlines the protocols for constructing and integrating internal modules into the Genesis Smart Shell environment.
1. Plugin Architecture
Every plugin must be contained within its own directory and follow this mandatory structure:
 * .manifest: A plain text file containing a single word. This word becomes the alias used to trigger your plugin from the shell.
 * logic.sh: The execution core. This is the Bash script that the engine runs when the alias is called.
2. Step-by-Step Creation
Step I: Initialize Directory
Create a unique folder for your plugin.
mkdir ~/MyGenesisPlugin
cd ~/MyGenesisPlugin

Step II: Define the Manifest
Create the .manifest file and write your desired command name inside.
echo "my-tool" > .manifest

Step III: Develop Logic
Create logic.sh. You can use Zenity to maintain the Genesis GUI aesthetic.
cat << 'EOF' > logic.sh
#!/bin/bash
zenity --info --title="Geno-Link" --text="Plugin 'My-Tool' is operational."
# Insert your Bash or Python logic here
EOF

chmod +x logic.sh

3. Deployment Protocol
To inject your plugin into the Genesis core, follow these commands within the shell:
 * Install: Type plugin install and select your plugin directory via the GUI.
 * Sync: Type reload to refresh neural links and activate the new alias.
 * Execute: Simply type your alias (e.g., my-tool) to run the plugin.
4. Best Practices
 * GUI Consistency: Use zenity for all user interactions (confirmations, progress bars, file selection).
 * Path Safety: Use $GENESIS_ROOT to reference the shell's installation path.
 * Cleanup: Ensure your plugin cleans up any temporary files in $GENESIS_ROOT/tmp/.
