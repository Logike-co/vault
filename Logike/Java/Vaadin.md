
https://marketplace.visualstudio.com/items?itemName=vaadin.vaadin-vscode
Launch VS Code Quick Open (`Ctrl+P`), paste the following command, and press enter.
ext install vaadin.vaadin-vscode

Steps to enable hotswap in VS Code for Vaadin:

- **Install the Vaadin VS Code Extension:** 
    
    This extension provides tools for developing Vaadin applications within VS Code, including features related to hotswap. You can find it in the Visual Studio Marketplace by searching for "Vaadin."
    
- **Setup Hotswap Agent:** 
    
    Use the Vaadin extension's command palette to set up Hotswap Agent.
    
    - Open the command palette (Ctrl+Shift+P or Cmd+Shift+P).
    - Type and select "Vaadin: Setup Hotswap Agent."
    - This command prepares your environment by downloading the necessary JetBrains Runtime (JBR), installing the Hotswap Agent library, and updating your project configuration.