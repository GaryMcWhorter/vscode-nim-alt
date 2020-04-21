# Nim for Visual Studio Code

**NOTE:**
_This is currently a mirror of [the original Nim extension](https://marketplace.visualstudio.com/items?itemName=kosz78.nim)_

Changes include:
- Fixes for syntax highlighting bugs
- Changes to syntax highlighting to more properly reflect idiomatic practice. 
    This will look different and many words will now not be highlighted as you may have been used to, but this is more consistent and correct to the language standard.
- A pretty new icon

Potential problems:
- Some syntax may still not be properly highlighted due to rewriting the syntax highlighting. These issues will be fixed as they are found.

**NOTE:**
You can enable optional coloring for basic types in your settings.json
You have to set the color yourself in #RRGGBB format. You can't make it match your current them automatically.
```json
    "editor.tokenColorCustomizations": {
        "textMateRules": [
            {
                "scope": "basicTypes.nim",
                "settings": {
                    "foreground": "#ff0000",
                }
            }
        ]
    }
```


This extension adds language support for the Nim language to VS Code, including:

- Syntax Highlight (nim, nimble, nim.cfg)
- Code Completion
- Signature Help
- Goto Definition
- Find References
- File outline
- Build-on-save
- Workspace symbol search
- Quick info
- Nim check result reported in `Nim` output channel (great for macro development).

![output channel demo](images/nim_vscode_output_demo.gif)

## Using

First, you will need to install Visual Studio Code `0.10`.
In the command palette (`cmd-shift-p`) select `Install Extension` and choose `Nim`.

The following tools are required for the extension:
* Nim compiler - http://nim-lang.org

_Note_: It is recommended to turn `Auto Save` on in Visual Studio Code (`File -> Auto Save`) when using this extension.

### Options

The following Visual Studio Code settings are available for the Nim extension.  These can be set in user preferences (`cmd+,`) or workspace settings (`.vscode/settings.json`).
* `nim.buildOnSave` - perform build task from `tasks.json` file, to use this options you need declare build task according to [Tasks Documentation](https://code.visualstudio.com/docs/editor/tasks), for example:
	```json
	{
		"taskName": "Run module.nim",
		"command": "nim",
		"args": ["c", "-r", "module.nim"],
		"options": {
			"cwd": "${workspaceRoot}"
		},
		"type": "shell",
		"group": {
			"kind": "build",
			"isDefault": true
		}
	}
	```
* `nim.lintOnSave` - perform the project check for errors on save
* `nim.project` - optional array of projects file, if nim.project is not defined then all nim files will be used as separate project
* `nim.licenseString` - optional license text that will be inserted on nim file creation


#### Example

```json
{
	"nim.buildOnSave": false,
	"nim.buildCommand": "c",
	"nim.lintOnSave": true,
	"nim.project": ["project.nim", "project2.nim"],
	"nim.licenseString": "# Copyright 2017.\n\n"
}
```

### Commands
The following commands are provided by the extension:

* `Nim: Run selected file` - compile and run selected file, it uses `c` compiler by default, but you can specify `cpp` in `nim.buildCommand` config parameter.
This command available from file context menu or by `F6` keyboard shortcut.

## TODO

* Rename support
* Debug support

## ChangeLog

ChangeLog is located [here](https://github.com/GaryM-exkage/vscode-nim-alt/blob/master/CHANGELOG.md)

