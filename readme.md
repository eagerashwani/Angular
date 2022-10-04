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
- Ab ek button bnate hai
- Maine tailwind css install kr li hai
  ```html
    <button class="bg-slate-900 text-white">click me</button>
  ```
- Ab main button ka color red krna chahta hoon, wo bhi ek property define kr k, btnRed : string = "bg-red-500";
- Ab class ko [] k andr likhenge, agr hume ts code use krna hai to.
  ```html
  <button [class]="btnRed">click me</button>
  ```
  ```ts
   btnRed : string = "bg-red-500 text-white";
  ```
- Ab main ek random color generator banana chahta hu, apne button ke liye
  ```ts
    bgColor : string;

    constructor() {
      const colors = ['red', 'cyan', 'orange'];
      this.bgColor = "bg-" + colors[Math.floor(Math.random() * 3)] + "-500";
    }
  ```
  ```html
    <button [class]="bgColor">click me</button>
  ```
- Error, agar phle color change kr diya to shi chalta hai, nhi to nhi chalta
- Ab main button ko enable krna chahta hu, 3 sec baad
  ```ts
   isDisable : boolean = true;

  constructor() {
    setTimeout(() => {
      this.isDisable = false;
    },3000);
    const colors = ['red', 'cyan', 'orange'];
    this.bgColor = "bg-" + colors[Math.floor(Math.random() * 3)] + "-500";
   }
  ```
  ```html
    <button [class]="bgColor" [disabled]="isDisable">click me</button>
  ```
- Error, button is disable for 3 sec but color remains on button.

### Event Binding
- In html, all events are start with on like : onclick, ondbclick etc
- but in angular, remove on
- and put event in () like : (click)
  ```ts
    mySalary(){
       alert(this.salary * 80);
    }
  ```
  ```html
    <button class="bg-green-600 text-white px-3 mx-3" (click)="mySalary()">Show salary in INR</button>
  ```

## Two Way Binding
- Both side communication.
  ```html
  <input type="text" [value]="fullname" class="my-10"/>
  <h2>{{fullname}}</h2>
  ```
- input field mey myname ki value show ho rhi h
- But main chahta hoon ki input field mey jo likhu wo h2 mey show ho jaye
- Event binding ko use krenge
  ```html
  <input type="text" [value]="fullname" class="my-10" (input)="getMyInput($event)" />
  ```
  - (input) : ye hai hamara event.
  - getMyInput() : ye hai function
  - $event : hum ye event pass kar rhe hai, function ke andr

  ```ts
    getMyInput(e:any){
      console.log(e.target.value);
      // jaise hi kuch likhna start kiya input field mey, to har letter new line mey console mey print hota rhega

      this.fullname = e.target.value;
      // ab h2 mey live update hota rhega

      }   
  ```
- Hum function na de kar, direct event.target.value de skte they kyuki ek hi line ka code tha
  ```html
    <input type="text" [(ngModel)] = "fullname">
  ```
  - Isko likhne se phle hummey module.ts mey formsModule import krna hoga aur imports array mey dena hoga

## Directives
- Now, hum apne webpage par kuch conditionally data show krna chahte hai
- Agar ye condition hai to ye kro, ye hai to ye kro
### *ngIf
```html
 <h2 *ngIf="salary > 25000">Party to banti hai</h2>
```
- Agar salary 25000 se jada hogi, to Party to banti hai show hoga, nhi to nhi hoga.
- But main else wala part bhi chahta hu
  ```html
  <h2 *ngIf="salary > 25000; else lowSal">Party to banti hai</h2>
  <ng-template #lowSal>
      <h2>Phle achi job le le</h2>
  </ng-template>
  ```