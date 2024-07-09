# Python Project Template

This is a python project template to let you start your python project more easily. This
project mainly provides the environment setup for the [Visual Studio Code](https://code.visualstudio.com/).

You should install the following extensions in the market:

+ `Python` and `Pylance`: the language server part.
+ `black`: the code formatter.
+ `isort`: the import module formatter.

## The Build System

This project uses `pyproject.toml` as the build system. It's more modern than the ordinary `setup.py`.
You could see [pip documentation](https://pip.pypa.io/en/stable/reference/build-system/pyproject-toml/)
for more details.

## The VsCode Extensions Settings

This project provides the settings of the VsCode at the workspace in the `.vscode/settings.json`.

```json
{
  "python.analysis.typeCheckingMode": "strict",
  "python.analysis.autoImportCompletions": true,
  "python.analysis.inlayHints.pytestParameters": true,
  "python.analysis.inlayHints.variableTypes": true,
  "[python]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "ms-python.black-formatter",
    "editor.codeActionsOnSave": {
      "source.organizeImports": "always",
    },
    "editor.tabSize": 4
  },
}
```

It will do the following things:

1. For the language server, it will automatically import the module and test the type
strictly to provide type safety. And also it would provide the type hint if there is
no type annotation.
2. For the language self, it will format the code using `black` and sort
the import using `isort` every time you save the code.

## The Debugger Setup

In VsCode, we could debug only one simple file, or the whole module. I think if we write
a project, we should debug the program as the module, it is defined in the `.vscode/launch.json`

```json
{
  // Use IntelliSense to learn about possible attributes.
  // Hover to view descriptions of existing attributes.
  // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Debug the module",
      "type": "debugpy",
      "request": "launch",
      "module": "anonymous.main",
      "justMyCode": true
    }
  ]
}
```

## The Test Setup

The VsCode provides two built-in test framework:

+ `unittest`.
+ `pytest`.

I decide to use `pytest`:

```json
{
  "python.testing.pytestArgs": [
    "anonymous"
  ],
  "python.testing.unittestEnabled": false,
  "python.testing.pytestEnabled": true,
}
```
