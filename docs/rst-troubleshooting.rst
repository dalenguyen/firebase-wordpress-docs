reStructuredText Preview Troubleshooting
========================================

This guide helps you resolve common issues with reStructuredText preview functionality in VS Code.

Common Issues and Solutions
--------------------------

1. **"reStructuredText: Preview Sphinx" Not Appearing**
   ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

   **Problem**: The preview commands don't appear in the command palette.

   **Solutions**:

   a) **Install Required Extensions**:
      - Install `lextudio.restructuredtext` (reStructuredText extension)
      - Install `swyddfa.esbonio` (Esbonio language server)

   b) **Reload VS Code**:
      - Press ``Ctrl+Shift+P`` (or ``Cmd+Shift+P`` on Mac)
      - Type "Developer: Reload Window"
      - Press Enter

   c) **Check File Association**:
      - Ensure .rst files are associated with reStructuredText
      - Open a .rst file and check the language mode in the bottom right

2. **Preview Commands Available but Not Working**
   ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

   **Problem**: Commands appear but don't generate preview.

   **Solutions**:

   a) **Check Python Dependencies**:
      ```bash
      cd docs
      pip install -r requirements.txt
      ```

   b) **Verify Sphinx Configuration**:
      - Ensure `docs/conf.py` exists and is valid
      - Check that `docs/Makefile` exists

   c) **Test Build Manually**:
      ```bash
      cd docs
      make html
      ```

3. **Esbonio Server Not Starting**
   ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

   **Problem**: Esbonio language server fails to start.

   **Solutions**:

   a) **Check VS Code Settings**:
      ```json
      {
        "esbonio.server.enabled": true,
        "esbonio.sphinx.confDir": "${workspaceFolder}/docs",
        "esbonio.sphinx.buildDir": "${workspaceFolder}/_build/html",
        "esbonio.sphinx.srcDir": "${workspaceFolder}/docs"
      }
      ```

   b) **Check Output Panel**:
      - Open Output panel (View → Output)
      - Select "Esbonio" from dropdown
      - Look for error messages

   c) **Restart Esbonio Server**:
      - Press ``Ctrl+Shift+P``
      - Type "Esbonio: Restart Server"
      - Press Enter

4. **Preview Shows Errors**
   ~~~~~~~~~~~~~~~~~~~~~~~~

   **Problem**: Preview works but shows build errors.

   **Solutions**:

   a) **Fix RST Syntax Errors**:
      - Check for missing colons after directives
      - Verify proper indentation
      - Fix broken links and references

   b) **Check Image Paths**:
      - Ensure images exist in the specified paths
      - Use relative paths from the docs directory

   c) **Update Dependencies**:
      ```bash
      pip install --upgrade sphinx docutils sphinx_rtd_theme
      ```

Step-by-Step Verification
------------------------

1. **Verify Extensions**:
   ```bash
   code --list-extensions | grep -E "(restructured|esbonio)"
   ```

2. **Check File Recognition**:
   - Open any .rst file
   - Look at bottom-right corner for language mode
   - Should show "reStructuredText"

3. **Test Command Palette**:
   - Press ``Ctrl+Shift+P`` (or ``Cmd+Shift+P`` on Mac)
   - Type "reStructuredText"
   - Should see multiple options including:
     - "reStructuredText: Preview Sphinx"
     - "reStructuredText: Preview Docutils"
     - "reStructuredText: Build Sphinx"

4. **Check Output Panel**:
   - View → Output
   - Select "Esbonio" from dropdown
   - Look for any error messages

5. **Test Manual Build**:
   ```bash
   cd docs
   make html
   ```

Alternative Preview Methods
--------------------------

If the VS Code preview doesn't work, you can:

1. **Use Browser Preview**:
   ```bash
   cd docs
   make html
   # Open _build/html/index.html in browser
   ```

2. **Use Live Server**:
   - Install Live Server extension
   - Right-click on `_build/html/index.html`
   - Select "Open with Live Server"

3. **Use Python HTTP Server**:
   ```bash
   cd docs/_build/html
   python -m http.server 8000
   # Open http://localhost:8000 in browser
   ```

Getting Help
-----------

If you're still having issues:

1. **Check Extension Logs**:
   - Help → Toggle Developer Tools
   - Look for errors in Console tab

2. **Report Issues**:
   - reStructuredText Extension: https://github.com/vscode-restructuredtext/vscode-restructuredtext
   - Esbonio: https://github.com/swyddfa/esbonio

3. **Community Support**:
   - Stack Overflow: Tag questions with `restructuredtext` and `vscode`
   - GitHub Discussions: Check extension repositories

This troubleshooting guide should help resolve most common preview issues. 