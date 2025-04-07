# My macOS Ansible Setup

This Ansible playbook automates the setup of a new macOS machine by installing essential tools, applications via Homebrew, and creating specified directories.

## Prerequisites

Before running the playbook, you need a few things installed on your Mac:

1.  **Xcode Command Line Tools:** These are required by Homebrew and Ansible. If you don't have them, open `Terminal.app` and run:
    ```bash
    xcode-select --install
    ```
    Follow the prompts to install.

2.  **Python 3 & pip:** macOS usually includes Python 3. `pip` is Python's package installer and is needed to install Ansible. If you installed Python via Homebrew (`brew install python`), `pip3` should be available.

3.  **Ansible:** This is the automation tool that runs the playbook. Install it using pip:
    ```bash
    pip3 install ansible
    ```
    *(Alternatively, if you already have Homebrew installed, you could run `brew install ansible`)*

## Usage

1.  **Clone the Repository (Optional):**
    If you've uploaded this to GitHub, clone it to your local machine:
    ```bash
    git clone <your-repository-url>
    cd <repository-directory>
    ```

2.  **Customise the Playbook (`setup-mac.yml`):**
    **IMPORTANT:** Open the `setup-mac.yml` file in a text editor. Review and modify the lists under the `vars:` section to match your preferences:
    * `homebrew_packages`: List of command-line tools to install.
    * `homebrew_casks`: List of GUI applications to install.
    * `directories_to_create`: List of directories to create in your home folder.
    * *(Add/remove items as needed)*

3.  **Run the Playbook:**
    Open `Terminal.app`, navigate (`cd`) to the directory containing the `setup-mac.yml` file, and run the following command:
    ```bash
    ansible-playbook setup-mac.yml
    ```
    Ansible will now execute the tasks defined in the playbook. You may be prompted for your password during the installation of some applications (via Homebrew Cask) or need to approve macOS security prompts.

## Notes

* **Idempotency:** This playbook is designed to be run multiple times safely. Ansible will skip tasks that are already completed (e.g., if an application is already installed).
* **Xcode Application:** This script does **not** install the full Xcode application from the App Store, only the command-line tools. You will need to install Xcode manually if required.
* **Manual Configuration:** After the script finishes, you will still need to log into applications and potentially grant specific macOS permissions (e.g., Accessibility for window managers, System Extensions for Docker).