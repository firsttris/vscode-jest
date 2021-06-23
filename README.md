# vscode-jest-runner

## Visual Studio Code Marketplace

[VisualStudio Marketplace](https://marketplace.visualstudio.com/items?itemName=firsttris.vscode-jest-runner)   
[Open VSX Registry](https://open-vsx.org/extension/firsttris/vscode-jest-runner)

## Comparison with [vscode-jest](https://github.com/jest-community/vscode-jest)

[vscode-jest-runner](https://github.com/firsttris/vscode-jest-runner) is focused on running or debugging a specific test or test-suite, while [vscode-jest](https://github.com/jest-community/vscode-jest) is running your current test-suite everytime you change it.

## Features

Simple way to run or debug a specific test
*As it is possible in IntelliJ / Webstorm*

Run & Debug your Jest Tests from
- Context-Menu
- CodeLens
- Command Palette (strg+shift+p)

## Supports 
- yarn & vscode workspaces (monorepo)
- dynamic jest config resolution  
- yarn 2 pnp   
- CRA & and similar abstractions   

![Extension Example](https://github.com/firsttris/vscode-jest/raw/master/public/vscode-jest.gif)

## Usage with Create React App / CRA

Add the following command to settings, to run tests
```
"jestrunner.jestCommand": "npm run test --"
```

Add the following commands to settings, to debug tests
```
"jestrunner.jestPath": "${workspaceRoot}/node_modules/.bin/react-scripts",
"jestrunner.debugOptions": {
		"args": ["test", "--no-cache"],
		"disableOptimisticBPs": true,
		"env": {
			"CI": "true"
		},
	},
```

Check that debugger works:
![image](https://user-images.githubusercontent.com/1709260/120468727-d542ae00-c3a1-11eb-85ac-986c35ac167f.png)

## Extension Settings

Jest Runner will work out of the box, with a valid Jest config.   
If you have a custom setup use the following options to configure Jest Runner:

| Command | Description |
| --- | --- |
| jestrunner.configPath | Jest config path (relative to ${workFolder} e.g. jest-config.json) |
| jestrunner.jestPath | Absolute path to jest bin file (e.g. /usr/lib/node_modules/jest/bin/jest.js) |
| jestrunner.debugOptions | Add or overwrite vscode debug configurations (only in debug mode) (e.g. `"jestrunner.debugOptions": { "args": ["--no-cache"] }`) |
| jestrunner.runOptions | Add CLI Options to the Jest Command (e.g. `"jestrunner.runOptions": ["--coverage", "--colors"]`) https://jestjs.io/docs/en/cli |
| jestrunner.jestCommand | Define an alternative Jest command (e.g. for Create React App and similar abstractions) |
| jestrunner.disableCodeLens | Disable CodeLens feature |
| jestrunner.codeLensSelector | CodeLens will be shown on files matching this pattern (default **/*.{test,spec}.{js,jsx,ts,tsx}) |
| jestrunner.enableYarnPnpSupport | Enable if you are using Yarn 2 with Plug'n'Play |
| jestrunner.projectPath | Absolute path to project directory (e.g. /home/me/project/sub-folder) |
| jestrunner.changeDirectoryToWorkspaceRoot | Changes directory to workspace root before executing the test |

## Shortcuts

click File -> Preferences -> Keyboard Shortcuts -> "{}" (top right)
the json config file will open
add this:

```javascript
{
  "key": "alt+1",
  "command": "extension.runJest"
},
{
  "key": "alt+2",
  "command": "extension.debugJest"
},
```

## Want to start contributing features?

[Some open topics get you started](https://github.com/firsttris/vscode-jest-runner/issues)

## Steps to run in development mode

- npm install
- Go to Menu "Run" => "Start Debugging"

Another vscode instance will open with the just compiled extension installed.

## Notes from contributors

- Babel compile Issue when starting Debug in JSX/TSX, 
    - check the post of @Dot-H https://github.com/firsttris/vscode-jest-runner/issues/136
    - https://github.com/firsttris/vscode-jest-runner/issues/174

- By default **Jest** finds its config from the `"jest"` attribute in your `package.json` or if you export an object `module.export = {}` in a `jest.config.js` file in your project root directory.   
Read More: [Configuring Jest Docs](https://jestjs.io/docs/en/configuration)

- If Breakspoints are not working properly, try adding this to vscode config:

```javascript
"jestrunner.debugOptions": {
    "args": ["--no-cache"],
    "sourcemaps": "inline",
    "disableOptimisticBPs": true,
}
```
