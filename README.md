# Demo of the application

https://github.com/alt440/SvelteTutorial/assets/35940672/97516b90-03f3-4555-9302-9d077f419703

# How to run the code on your machine (Windows) using VS Code
1- Download NodeJS.

2- Go to the command prompt (cmd). Run the command 
```bash
npm -g install degit
```
to install degit, a tool that will help us set up a Svelte project.

3- Use 'cd' in the command prompt to navigate to your desired project directory.

4- Execute:
```bash
degit sveltejs/template <nameOfProjectHere>
```
where <nameOfProjectHere> is the name of your project, without the <> signs. This will create the svelte project along with required files.

5- Open VS Code. Go to Extensions -> Add the Svelte extension 'Svelte for VS Code' by Svelte.

6- Open your project directory in VS Code.

7- Open a terminal in VS code by looking in the top bar for 'Terminal' -> 'Open a new terminal'.

8- Verify that the terminal is currently on your project directory. Then execute the command:
```bash
npm install
```
to install all the dependencies that svelte will need (which can be seen from the package.json file of your project).

9- Once this is complete, run from your terminal:
```bash
npm run dev
```


Your terminal will log information as to where the application is running. On my machine, it runs on port 8080, through localhost (localhost:8080/).



# IMPORTANT! SvelteJS is no longer supported. I didn't know when I started the project. Consider using `npm init vite` and selecting the `svelte` option or — if you want a full-fledged app framework — use [SvelteKit](https://kit.svelte.dev), the official application framework for Svelte.

Then, from within your project folder:

```bash
npm run build
surge public my-project.surge.sh
```
