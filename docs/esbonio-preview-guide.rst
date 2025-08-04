Using Esbonio for reStructuredText Preview
==========================================

Since version 190.1.17 of the reStructuredText extension, preview functionality has been moved to the Esbonio extension. This guide explains how to use Esbonio for previewing your reStructuredText documents.

Prerequisites
------------

1. **Required Extensions**:
   - `lextudio.restructuredtext` (reStructuredText extension) - for syntax highlighting and linting
   - `swyddfa.esbonio` (Esbonio language server) - for preview functionality

2. **Python Dependencies**:
   ```bash
   cd docs
   pip install -r requirements.txt
   ```

Configuration
-------------

VS Code Settings (``.vscode/settings.json``)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

```json
{
  // Esbonio configuration for preview functionality
  "esbonio.server.enabled": true,
  "esbonio.sphinx.confDir": "${workspaceFolder}/docs",
  "esbonio.sphinx.buildDir": "${workspaceFolder}/_build/html",
  "esbonio.sphinx.srcDir": "${workspaceFolder}/docs",
  "esbonio.server.logLevel": "info",

  // reStructuredText extension configuration (no preview - handled by Esbonio)
  "restructuredtext.confPath": "${workspaceFolder}/docs/conf.py",
  "restructuredtext.buildPath": "${workspaceFolder}/_build/html",
  "restructuredtext.makefilePath": "${workspaceFolder}/docs/Makefile",

  // Editor settings
  "files.associations": {
    "*.rst": "restructuredtext"
  }
}
```

Using Esbonio Preview
--------------------

1. **Open an RST File**:
   - Open any `.rst` file in your `docs/` directory
   - The file should be recognized as reStructuredText (check bottom-right corner)

2. **Esbonio Commands**:
   - Press ``Ctrl+Shift+P`` (or ``Cmd+Shift+P`` on Mac)
   - Type "Esbonio" to see available commands:
     - "Esbonio: Restart Server"
     - "Esbonio: Show Preview"
     - "Esbonio: Show Preview to the Side"

3. **Live Preview**:
   - Esbonio provides live preview functionality
   - Changes in your RST files are reflected in real-time
   - Preview opens in a new tab or panel

4. **Alternative Preview Methods**:
   - **Manual Build**: ``cd docs && make html``
   - **Browser Preview**: Open `_build/html/index.html` in browser
   - **Live Server**: Use Live Server extension on `_build/html/index.html`

Troubleshooting Esbonio
----------------------

1. **Esbonio Server Not Starting**:
   - Check Output panel: View → Output → Select "Esbonio"
   - Look for error messages
   - Try "Esbonio: Restart Server" command

2. **Preview Not Working**:
   - Ensure Sphinx configuration is valid
   - Check that `docs/conf.py` exists and is properly configured
   - Verify Python dependencies are installed

3. **Build Errors**:
   - Check for RST syntax errors
   - Verify image paths and references
   - Look at the Problems panel for linting issues

4. **Extension Conflicts**:
   - Disable other RST extensions that might conflict
   - Ensure only `lextudio.restructuredtext` and `swyddfa.esbonio` are active

Verification Steps
-----------------

1. **Check Extensions**:
   ```bash
   code --list-extensions | grep -E "(restructured|esbonio)"
   ```

2. **Test File Recognition**:
   - Open a `.rst` file
   - Bottom-right should show "reStructuredText"

3. **Test Esbonio Commands**:
   - ``Ctrl+Shift+P`` → Type "Esbonio"
   - Should see multiple Esbonio commands

4. **Check Output Panel**:
   - View → Output → Select "Esbonio"
   - Should show server status and any errors

5. **Test Manual Build**:
   ```bash
   cd docs
   make html
   ```

Key Differences from Old Preview
-------------------------------

- **No "reStructuredText: Preview Sphinx" command** - This was removed from the main extension
- **Esbonio handles all preview functionality** - Use "Esbonio: Show Preview" instead
- **Better live preview** - Esbonio provides more responsive live preview
- **Improved error handling** - Better error reporting and diagnostics

Getting Help
-----------

- **Esbonio Documentation**: https://esbonio.readthedocs.io/
- **Esbonio GitHub**: https://github.com/swyddfa/esbonio
- **reStructuredText Extension**: https://github.com/vscode-restructuredtext/vscode-restructuredtext

This setup provides the modern, recommended way to preview reStructuredText documents in VS Code. 