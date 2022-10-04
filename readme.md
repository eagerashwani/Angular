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
- Iss class ke andar hum likhte hai logical code, property, function etc.
- Sirf class bnane se hmara component nhi banta, hume ek decorator(@Component iss case mey, jo ki ek object leta hai) bhi chahiye
  ```bash
  import { Component } from '@angular/core';

  @Component({
    selector: 'app-root',
    templateUrl: './app.component.html',
    styleUrls: ['./app.component.css']
  })

  ```
- templateUrl mey hum file dete hai, template mey `` ke andar inline html code likhte hai, aisa same styles k saath hum inline CSS likhte hai.
- Ab humne iss component ko ek naam bhi dena hai, wo hum selector ka use kr k dete hai, jo selector ki value hogi usi ko hum html tag ki trh use kar skte hai.
- agar hum selector ko .app-root likh de, to index.html mey hume div ko app-root as class dena hoga.
- agr hum [app-root] likhte hai selector mey, to hume attribute dena hoga
  ```bash
  <div app-root></div>
  ```

### app.module.ts file
- @NgModule ek decorator hai, jiske andar declaration mey hum components dete hai(Humko Angular ko btana pdta hai ki ye component main use krna chahte hoon).
- bootstrap: [AppComponent], yahan bhi AppComponent hai, bootstrap mey hum jo app level component ko uska use krenge
- Jb hum angular cli ka use kr k component generate krte hai, to automatic declaration k andr add ho jata hai nya component.
- Nya component bnane ke liye hum ng g c <name> command use krte hai

## Interpolation
- Ab kuch property define kar lete hai profile.ts mey
  ```bash
    name: string = "Ashwani";
    status: string = "Complicated";
    salary: number = 20000;
    age: number = 24;
  ```
- Ab main inn properties ko profile.html mey use kar skta hoon.
- {{}} iss ko khte hai interpolation, ismey hum properties/expression dete hai.
  ```html
  <h2>Mera naam {{name}} hai, main {{age}} ka hoon, meri salary {{salary * 80}} itni hai aur love life {{status}} hai</h2>
  ```
- {{status * 80}} ye ek expression hai, aur name ke andr hum sbhi string k methods use kr skte hai like toUpperCase() etc.
- Ab humne ek function bhi define kr diya aur wo bhi html mey show krwa liya, interpolation ki help se.
  ```ts
    getName(){
    const aka: string = "Ironman";
    return `I am ${this.myname} aka ${aka}`;

    }
  ```
  ```html
    <h1>{{getName()}}</h1>
  ```

## Property Binding
