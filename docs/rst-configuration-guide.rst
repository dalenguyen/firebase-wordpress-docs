reStructuredText Viewer Configuration Guide
============================================

This guide explains how to configure the reStructuredText viewer for optimal experience with the Firebase WordPress documentation project.

Prerequisites
------------

1. **VS Code Extensions Installed:**
   - `lextudio.restructuredtext` (reStructuredText extension)
   - `swyddfa.esbonio` (Esbonio language server - recommended)

2. **Python Dependencies:**
   The project already includes required dependencies in ``docs/requirements.txt``:
   
   - docutils==0.17.1
   - sphinx_rtd_theme==2.0.0

Configuration Files
------------------

VS Code Settings (``.vscode/settings.json``)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The project includes optimized VS Code settings for reStructuredText:

.. code-block:: json

    {
        "esbonio.server.enabled": true,
        "esbonio.sphinx.confDir": "${workspaceFolder}/docs",
        "esbonio.sphinx.buildDir": "${workspaceFolder}/_build/html",
        "esbonio.sphinx.srcDir": "${workspaceFolder}/docs",
        
        // Enhanced reStructuredText configuration
        "restructuredtext.confPath": "${workspaceFolder}/docs/conf.py",
        "restructuredtext.buildPath": "${workspaceFolder}/_build/html",
        "restructuredtext.makefilePath": "${workspaceFolder}/docs/Makefile",
        "restructuredtext.preview.sphinx": true,
        "restructuredtext.preview.docutil": true,
        
        // Editor settings for better RST experience
        "files.associations": {
            "*.rst": "restructuredtext"
        },
        
        // Auto-save and build settings
        "files.autoSave": "afterDelay",
        "files.autoSaveDelay": 1000
    }

Sphinx Configuration (``docs/conf.py``)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The project uses Sphinx for documentation building with the following key settings:

- **Theme**: sphinx_rtd_theme (Read the Docs theme)
- **Source files**: .rst files in the docs/ directory
- **Build output**: HTML in _build/html/ directory
- **Extensions**: sphinx_rtd_theme for enhanced styling

Using the reStructuredText Viewer
--------------------------------

1. **Opening RST Files:**
   - Open any .rst file in the docs/ directory
   - The file will automatically be recognized as reStructuredText

2. **Preview Options:**
   - **Sphinx Preview**: Press ``Ctrl+Shift+P`` (or ``Cmd+Shift+P`` on Mac) and type "reStructuredText: Preview Sphinx"
   - **Docutils Preview**: Press ``Ctrl+Shift+P`` and type "reStructuredText: Preview Docutils"
   - **Live Preview**: The Esbonio extension provides live preview capabilities

3. **Building Documentation:**
   - Use the Makefile: ``make html`` in the docs/ directory
   - Or use VS Code commands: "reStructuredText: Build Sphinx"

4. **Navigation:**
   - Use the table of contents in the built HTML
   - Navigate between RST files using internal links
   - Use the search functionality in the built documentation

Key Features
-----------

- **Live Preview**: See changes in real-time with Esbonio
- **Syntax Highlighting**: Proper highlighting for RST directives and roles
- **Auto-completion**: Intelligent suggestions for RST syntax
- **Error Detection**: Real-time validation of RST syntax
- **Cross-references**: Automatic linking between documents
- **Image Support**: Proper handling of images and diagrams

Troubleshooting
--------------

1. **Preview Not Working:**
   - Ensure Esbonio extension is installed and enabled
   - Check that Python dependencies are installed: ``pip install -r docs/requirements.txt``
   - Verify Sphinx configuration in docs/conf.py

2. **Build Errors:**
   - Check for syntax errors in RST files
   - Ensure all referenced files exist
   - Verify image paths are correct

3. **Extension Issues:**
   - Reload VS Code window: ``Ctrl+Shift+P`` → "Developer: Reload Window"
   - Check extension logs in the Output panel
   - Update extensions to latest versions

Additional Resources
-------------------

- `reStructuredText Extension Documentation <https://docs.restructuredtext.net>`_
- `Sphinx Documentation <https://www.sphinx-doc.org/>`_
- `Read the Docs Theme <https://sphinx-rtd-theme.readthedocs.io/>`_
- `Esbonio Language Server <https://esbonio.readthedocs.io/>`_

This configuration provides a professional documentation development environment with live preview, syntax highlighting, and comprehensive build capabilities. 