# Learn Angular
## About Angular?
- Used to build single page applications 
- Follows component-oriented approach to develop completely resuable and modularized web applications.
- Its powerful features allows us to create
  - complex
  - customizable
  - modern
  - responsive
  - and user friendly web applications.

## Why Angular?
- Angular 1 is a JS framework developed by Google which was used for the development of web applications.
- Reasons to migrate from Angular JS to latest Angular
  - Cross-Bowser Compliant
  - TypeScript Support
  - Web Components Support
  - Better support for web development
  - Better Performance
  
## What is Angular?
- Open Source JS framework for building both mobile and web apps.
- Used to build SPA(Single Page Application).
- Angular is completely rewritten(Not an upgrade to Angular 1).
- Many Developers prefer TypeScript to build Angular apps, but you can also write code using JS.
- AOT Compiler
  
## Why TS for Angular?
- TS is Microsoft extension for JS which supports object-oriented features and has a strong typing system that enhances productivity.
- TS code is compiled to JS code using build tools like npm, gulp, webpack etc to make the browser understand the code.

## Local System Setup
- Install node in your system.
- And angular cli via below command.
  ```bash
  npm install -g @angular/cli
  ```
  - In windows OS, also paste this command
    ```bash
    Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
    ```
  - To check Angular is installed successfully in your system
    ```bash
    ng v
    ```
- And VS Code.

## Some Most Used commands
- Installs Angular CLI globally.
    ```bash
    npm install -g @angular/cli
    ```
- Creates a new Angular Application
    ```bash
    npm new <project_name>
    ```
- Build and run application on lite-server and lauches a browser
    ```bash
    ng serve --open
    ```
- Create a class, component, directive, interface, module, pipe and service
    ```bash
    ng generate <name>
    ```
- Buils the applications
    ```bash
    ng build
    ```
- Updates Angular to latest version
    ```bash
    ng udpate @angular/cli @angular/core
    ```

## Create project
- Open terminal and paste the command.
  ```bash
  ng new FirstAngularApp
  ```
  - Than based on your requirement allow routing or not.
  - Then Hit enter on CSS.

- Open VS code in FirstAngularApp folder.
- Now, open package.json file
  - and update thee start in scripts
  ```bash
  "start": "ng serve -o",
  ```

## Components
- Index.html ke andar hume  <app-root></app-root> tag dikh rha hai,
- Ye tag hai hamara component, Jo ki ek app level component hai
- Ab hum src/app mey jate hai to wahan .html file hai, usmey ye sara code likha huwa hai
- Now, change the prebuild code to <h1>Hello World</h1>, and see the changes.
- Component website ka ek part hai, chota sa hissa hai jaise footer, sidebar, navbar etc
- Sbse jayda imp file hoti hai app.component.ts wali
- Ab hum suru se iss file ko bnate hai
  ```bash
    class AppComponent{
      
    }
  ```
- Sbse phle hume ek class bnani hoti hai, ab iss class ko export krna hota taki hum isko import kar ske
  ```bash
    export class AppComponent{
      
    }
  ```
- Jb hum sirf export likhte hai to import k time, hume { } lgane pdte hai
  ```bash
    import { AppComponent } from './app.component';
  ```
- Agr main **export default** likhta tb mujhe { } ki zarurt nhi hoti, main direct likh deta
  ```bash
    import AppComponent from './app.component';
  ```