# Installs

- [Visual Studio Professional 2019](https://visualstudio.microsoft.com/downloads/)
    - Make sure you have the [NPM Task Runner](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) extension
- [Git](https://git-scm.com/)
- [NPM](https://www.npmjs.com/get-npm)

# Getting the code

Checkout the `DevOps-Module-07-Workshop` repository from [CorndelWithSoftwire's Github](https://github.com/CorndelWithSoftwire/DevOps-Module-07-Workshop):

```bash
git checkout git@github.com:CorndelWithSoftwire/DevOps-Module-07-Workshop.git
```

You should now be able to open the solution in Visual Studio 2019 by finding and double-clicking the `DotnetTemplate.sln` file.

# Running the app

The project should now build. Confirm this via *Build* → *Build Solution* (or `CTRL+SHIFT+B`/`Cmd+SHIFT+B`).

You can now run the app by clicking the play button (▶).

This should launch the website at: [https://localhost:44363/](https://localhost:44363/)

# Running the tests

## Running the web tests
These tests are in the DotnetTemplate.Web.Tests project. No setup is required to run them. See the sections below for how to run one test, all tests in a file or all the tests in the project.

## Run one test
Open the test file, find the test you want to run, click the icon to the left of the test name.

## Run all tests in a file
Open the file and click the icon to the left of the class name.

## Run all the tests
Open the solution explorer. Right click the test project (DotnetTemplate.Web.Tests) and select "Run tests".

## Typescript tests
The typescript tests are run using Jasmine, and can be found in `DotnetTemplate.Web/Scripts/spec`. The tests can be run using the Task Runner Explorer, or from the terminal using `npm t` inside DotnetTemplate.Web.

## Typescript linting
The typescript is linted with eslint. In Visual Studio, go to `Tools>Options>Text Editor>Javascript/Typescript>Linting>General` and tick "Enable ESLint". This should highlight any lint errors in the editor. It's not the most reliable, and if in doubt, run the lint manually.

Linting can be run with `npm run lint` inside `DotnetTemplate.Web`. `npm run lint-fix` may autofix some errors.

# Troubleshooting

## Undeclared variable warning in `index.scss` (DotnetTemplate.Web)

This might be a result of the css directory not being built.

It should have been automatically built by the [NPM Task Runner](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) extension. Check if you have it installed in Visual Studio.

Otherwise, you can work around it by manually building the css by opening a console in the project directory and running `npm run dev` (for development) or `npm run build`.

## npm error when opening the project in Visual Studio
If you see an error that looks something like:
```bash
npm WARN lifecycle The node binary used for scripts is C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild\Microsoft\VisualStudio\NodeJs\win-x64\node.exe but npm is using C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild\Microsoft\VisualStudio\NodeJs\node.exe itself. Use the `--scripts-prepend-node-path` option to include the path for the node binary npm was executed with.
```
This can be fixed by making sure PATH is on the top of the 'External Web Tools' list:
1. Open the options menu in Visual Studio (F4).
2. Search for 'External Web Tools'.
3. In the list select `$(PATH)` and use the up arrow button to move it to the top of the list.
4. Restart Visual Studio or double click the build command in the Task Runner Explorer to rerun the npm build.

# Logging
We're using [serilog](https://serilog.net/), specifically [serilog for .net core](https://nblumhardt.com/2019/10/serilog-in-aspnetcore-3/). This will automatically log:
* Any ASP.NET Core logs with level warning or above
* Any requests (excluding requests to static files)

We can add any additional logs using the `.Log` method.

The log output will go to the console.

To view the console in Visual Studio select View -> Output and set "Show output from:" to "DotnetTemplate.Web - ASP.NET Core Web Server".
