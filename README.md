# Velocity HTML

A local VS Code extension that provides basic syntax highlighting for Apache Velocity (`.vm`) templates containing HTML.

## Features

- Velocity syntax highlighting.
- Single-line comments with `##`.
- Multi-line comments with `#* ... *#`.
- Velocity directives:
  - `#if`
  - `#else`
  - `#elseif`
  - `#end`
  - `#foreach`
  - `#set`
  - `#macro`
  - `#include`
  - `#parse`
  - `#evaluate`
- Velocity variables such as `$user`, `$user.name`, and `${variable}`.
- HTML syntax highlighting inside Velocity templates.
- Automatic `.vm` file association.

## Structure

```text
velocity-html/
├── package.json
├── language-configuration.json
├── syntaxes/
│   └── velocity-html.tmLanguage.json
└── README.md
```
```bash
npm install -g @vscode/vsce
vsce package
```

### This generates:

```text
velocity-html-0.0.1.vsix
```

## Install the extension with:

```bash
code --install-extension velocity-html-0.0.1.vsix
```

If VS Code is connected to WSL, run the command from the WSL terminal.

## Configuration
No manual .vm file association is required.
Remove any existing configuration such as:

```json
"files.associations": {
    "*.vm": "java"
}
```

The extension automatically registers:

```text
*.vm → Velocity HTML
```

## Example

```java
## Velocity comment

#set($name = $user.name)

#if($user.loggedIn)
    <div class="user">
        Hello $name
    </div>
#else
    <div class="guest">
        Please log in
    </div>
#end

#foreach($item in $items)
    <a href="$item.url">
        $item.title
    </a>
#end
```

## Limitations
This extension currently focuses on syntax highlighting.
It does not provide Velocity IntelliSense, variable navigation, semantic validation, or template compilation.