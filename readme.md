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
- Index.html ke andar hume  `<app-root></app-root>` tag dikh rha hai,
- Ye tag hai hamara component, Jo ki ek app level component hai
- Ab hum src/app mey jate hai to wahan .html file hai, usmey ye sara code likha huwa hai
- Now, change the prebuild code to `<h1>Hello World</h1>,` and see the changes.
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
    const colors: string[] = ['red', 'cyan', 'orange'];
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
- It's a structural directive(Dom ka structure change karta hai)
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
### *ngFor
- Hamare pass ek array hai aur wo show krni hai
- Ek method to ye hai ki, interpolation ka use kr ke, index de do
- Dusra ngFor
  ```bash
   movies:string[] = ['Ironman', 'Batman', 'Thor', 'Captain America'];
  ```
  ```bash
  <ul>
    <li *ngFor="let f of movies">
        <h1>{{f}}</h1>
    </li>
  </ul>
  ```
- Now, I want ki length of array bhi bta aur saath hi index bhi show kro jb even index ho
  ```bash
    <ul>
        <li *ngFor="let f of movies; index as i; count as c; even as e">
            <h1 *ngIf="e">
              {{i}} {{f}}
            </h1>
        </li>
    </ul>
  ```
### ngClass
  ```bash
    <ul>
        <li *ngFor="let f of movies; index as i; count as c; even as e" [class]="e? 'bg-red-500' : 'bg-cyan-500'">
            <h1>
              {{i}} {{f}}
            </h1>
        </li>
    </ul>
  ```
- Above example works fine, lets look ngClass
```html
<ul>
    <li *ngFor="let f of movies; index as i; count as c; even as e" [ngClass]="{'bg-red-500': e, 'bg-cyan-500':!e}">
        <h1>
          {{i}} {{f}}
        </h1>
    </li>
</ul>
```
- ngClass works with array, string, object, classes and expression

## Pipes
### TitleCasePipe
```html
  <h2>{{myname | titlecase}}</h2>
```
- myname is in lower case but when we use pipe | with titlecase it become Ashwani Kumar

### CurrencyPipe
- {{salary * 80 | currency:'INR'}}

### DatePipe
- ts
  myDate! : Date;
- html
  <input type="date" [(ngModel)]="myDate" />
  {{myDate | date : 'medium' }}

## Parent to child component @Input()
### Component resue
- just add multiple times your component tag
  ```bash
  <app-users></app-users>
  <app-users></app-users>
  <app-users></app-users>
  ```
- Hm chahte hai ki, jo data hum app-users tag ko de wo reflect ho, dynamic banana chahte hai
- To phle tag property leta ho
- Aur wo property tag ki ts file mey bhi ho
- app.component.html (Parent)
  ```
  <app-users myname="Parnika"></app-users>
  <app-users></app-users>
  <app-users></app-users>
  ```
- user.ts
  ```
  import { Component, Input } from '@angular/core';

  @Component({
    selector: 'app-users',
    templateUrl: './users.component.html',
    styleUrls: ['./users.component.css']
  })
  export class UsersComponent  {
    @Input() myname!:string;
  }
  ```
- Import input and use input decorator inside class.
- Lets define some more properties
- app.ts
  ```
  <app-users myname="Parnika" hobby="Travelling" profession="Teacher"></app-users>
  <app-users myname="Somi" hobby="Travelling" profession="Singer"></app-users>
  ```
- users.html
  `<h1>{{myname}} and my hobby is {{hobby}} and my profession is {{profession}}</h1>`
- users.ts
  ```
  import { Component, Input } from '@angular/core';

  @Component({
    selector: 'app-users',
    templateUrl: './users.component.html',
    styleUrls: ['./users.component.css']
  })
  export class UsersComponent  {
    @Input() myname!:string;
    @Input() hobby !: string;
    @Input() profession !: string;
  }
  ```
- Make data also dynamic
- app.ts
  ```
   users = [
    {name : 'Ashwani', hobby : 'Watching Movies', profession : 'Engineer'},
    {name : 'Parnika', hobby : 'Travelling', profession : 'Teacher'},
  ]
  ```
- Now, lets add images also
- I add images to assets folder
- app.ts
  ```
  users = [
    {name : 'Ashwani', hobby : 'Watching Movies', profession : 'Engineer', imgPath : 'assets/ashwani.png'},
    {name : 'Parnika', hobby : 'Travelling', profession : 'Teacher', imgPath: 'assets/parnika.png'},
  ]
  ```
- app.html
  ```
    <app-users [myname]="users[0].name" [hobby]="users[0].hobby" [profession]="users[0].profession" [img]="users[0].imgPath"></app-users>
    <app-users [myname]="users[1].name" [hobby]="users[1].hobby" [profession]="users[1].profession" [img]="users[1].imgPath"></app-users>
  ```
- users.html
  ```
    <img src="{{img}}" alt="" width="200px" />
    <h1>{{myname}} and my hobby is {{hobby}} and my profession is {{profession}}</h1>
  ```
- users.ts
  ```
    import { Component, Input } from '@angular/core';

    @Component({
      selector: 'app-users',
      templateUrl: './users.component.html',
      styleUrls: ['./users.component.css']
    })
    export class UsersComponent  {
      @Input() myname!:string;
      @Input() hobby !: string;
      @Input() profession !: string;
      @Input() img !:string;
    }
  ```

- As you saw, we use same code many times in app.html, we can use `ngFor 
  <app-users *ngFor="let user of users" [myname]="user.name" [hobby]="user.hobby" [profession]="user.profession" [img]="user.imgPath"></app-users>`

## Child to parent communication
- Sbse phle 2 cheeze import krni pdengi, Output and EventEmitter (child mey)
- aur variable bnana pdega Outuput decorator aur eventEmitter k saath
- aur ek function jo data send krega
  ```
    @Output() myevent = new EventEmitter<string>();

    passData(){
      this.myevent.emit("Ashwani will be the richest man in the world");
    }
  ```
- ab iss function ko dena hai parent ko 
  `<button class="bg-indigo-500" (click)="passData()">pass data to parent</button>`

- Ab hume Parent ko event dena hai
  ```
    <app-users *ngFor="let user of users" [myname]="user.name" [hobby]="user.hobby" [profession]="user.profession"
      [img]="user.imgPath" (myevent)="recieveData($event)"></app-users>
  ```

- app.ts
  ```
    recieveData(e:any){
      console.log(e);

    }
  ```

## User Model
- hum users ke andar jo mnn chahe daal de rhe hai, but ye recommended nhi hai
  ```
      users = [
      {name : 'Ashwani', hobby : 'Watching Movies', profession : 'Engineer', imgPath : 'assets/ashwani.png'},
      {name : 'Parnika', hobby : 'Travelling', profession : 'Teacher', imgPath: 'assets/parnika.png'},
    ];
  ```
- hume phle apna khud ka data type banana chahiye users ke liye
- src folder mey ek nya folder models ke naam se bna lenge aur uske andr ek file user.ts
  ```
      export interface User{
        name:string;
        hobby:string;
        profession:string;
        imgPath:string;
    }
  ```

- Ab app.ts 
  ```
    users: Array<User> = [
      {name : 'Ashwani', hobby : 'Watching Movies', profession : 'Engineer', imgPath : 'assets/ashwani.png'},
      {name : 'Parnika', hobby : 'Travelling', profession : 'Teacher', imgPath: 'assets/parnika.png'},
    ];
  ```

- Ab hum inn 4 property k alwa kuch nhi de skte

## Content Projection
- When we pass data from parent to child its raw data (user.hobby etc)
- now, i want to pass html code
- Add your html code in b/w tag `<app-users>Here</app-users>`
  ```
    <app-users *ngFor="let user of users" [myname]="user.name" [hobby]="user.hobby" [profession]="user.profession"
      [img]="user.imgPath" (myevent)="recieveData($event)">
      <h2>Hello buddy</h2>
    </app-users>
  ```

- In user.html add
  `<ng-content></ng-content>`

- Suppose we have to pass more elements than...
  ```
  <app-users *ngFor="let user of users" [myname]="user.name" [hobby]="user.hobby" [profession]="user.profession"
    [img]="user.imgPath" (myevent)="recieveData($event)">
    <h2>Hello buddy</h2>
    <h3>Bye buddy</h3>
  </app-users>
  ```

- user.html
  ```
  <ng-content select="h2"></ng-content>
  <img src="{{img}}" alt="" width="200px" />
  <h1>{{myname}} and my hobby is {{hobby}} and my profession is {{profession}}</h1>
  <button class="bg-indigo-500" (click)="passData()">pass data to parent</button>
  <ng-content select="h3"></ng-content>
  ```
   - hum classes, id bhi select mey de skte hai

- Hum two way data binding bhi use kr skte hai
  ```
    <app-users *ngFor="let user of users" [myname]="user.name" [hobby]="user.hobby" [profession]="user.profession"
      [img]="user.imgPath" (myevent)="recieveData($event)">
      <h2>Hello buddy</h2>
      <br><br>
      <input type="text" [(ngModel)] = "title">
      {{title}}
      <br><br>
      <h3>Bye buddy</h3>
    </app-users>
  ```
  - Error, input field aa hi nhi rha

## Lifecycle hooks
- Jo bhi Lifecycles method hote hai unko hum call nhi karte Angular call krta hai
- Sbse phle hmme interface import krna hota hai lifecycle method ka aur phir implement krna hota h
### ngOnInit
- We use ngOnInit to initialize
- Whats the diff b/w constructor and ngoninit ?
- both methods call only once (constructor and ngoninit)
- Jab class ka instance banta hai tb constructor call hota hai
- Jab component banne wala hota hai tb ngonint call hota h
- app.ts
  ```ts
    constructor(){
      console.log('constructor', this.myname);  // op undefined
      // we can define properties here
    }
    
    ngOnInit(): void {
      console.log('ngOnInit', this.myname); // op shows name
      // we can define
      // properties
      // event listner register
      // initial data fetch 
      
    }
  ```
- Ek aur method hota hai jo constructor aur ngoninit ke bech mey aata hai
- Agr hum implement na bhi kre tb bhi koi issue nhi aata, but ye good practice nhi hai
### ngOnChanges
- ye method constructor ke baad aur ngoninit se phle call hota hai
- iske pass @Input ka access hota hai or jab bhi input change hota hai ye dubara se call hota hai
```ts
 ngOnChanges(changes: SimpleChanges): void {
    console.log(changes)
  }
```
### ngOnDestroy
- jab component delete hone wala hota hai, to hum iss method ki help se memory ko free kar skte hai
  
## Custom Directive
- ng g d <directives/highlight>
- In highlight.dir.ts file  `selector: '[appHighlight]'`
- You know why we use [ ] 
- Now main chahta hu ki background color change ho appHighlight directive se
- Sbse phle hum uss element ko access krenge jisko directive diya hai with help of ElementRef type
- users.html
  ```
  <div class="mx-40 my-20 border-spacing-4" appHighlight>
  ```
- highlight.directive.ts
  ```
  import { Directive, ElementRef } from '@angular/core';

  @Directive({
    selector: '[appHighlight]'
  })
  export class HighlightDirective {

    constructor(el:ElementRef) { 
      el.nativeElement.style.backgroundColor = "pink";
    }

  }
  ```
  - el ko hum abhi sirf constructor k andr use kr pa rhe
  - sirf private likhne se hum usko puri class mey use kar skte hai
  ```ts
        export class HighlightDirective {

          constructor(private el:ElementRef) { 
          }
          
          ngOnInit(){
            this.el.nativeElement.style.backgroundColor = "pink";

          }

        }

  ```
  - this is recommended approach (Make constructor simple)
  - We can also use @HostBinding
    ```ts
      @HostBinding('style.backgroundColor') bgColor: any;
      ngOnInit(){
          // this.el.nativeElement.style.backgroundColor = "pink";
          this.bgColor = 'pink';

        }
    ```
    - Now, I want to change bgColor on hover and remove color when mouse leave
  
## Custom Pipes
- Hum pipes ka use content ko format krne ke liye karte hai
- Hmare pass mobile number hai, us ke samne country code lgana hai
  ```ts
  import { Pipe, PipeTransform } from '@angular/core';

  @Pipe({
    name: 'countrycode'
  })
  export class CountrycodePipe implements PipeTransform {
    // iss value ke andr hmara phoneNo receive ho rha hai
    transform(value: unknown, ...args: unknown[]): unknown {
      return "+91" + value;
    }

  }

  ```
  - ab main country ka naam dena chahta hoon like USA
   ```ts
     // iss value ke andr hmara phoneNo receive ho rha hai
      transform(value: unknown, ...args: unknown[]): unknown {
        if(args[0]==="USA") return '+1' + value;
        else return "+91" + value;
      }
   ```

## HttpClient
- lets learn about how we call network in our Angular App
- Import HttpClientModule in module.ts
  ```ts
  constructor(private http:HttpClient) { }
  ```
  - This is called Dependency Injection
- Create a function to fetch the data
  ```ts
   fetchData(){
    this.http.get('https://jsonplaceholder.typicode.com/users').subscribe(data=>{
    //  console.log(data);

    });
    //above line return an observable before subscribe
  }
  ```
  ```html
  <button class="bg-purple-600 mx-20 my-20 px-10 py-10 text-white text-lg" (click)="fetchData()">Fetch Data</button>

  ```
  - updated ts
  ```ts
    export class HttpClientComponent implements OnInit {
    userName:string = 'user';

    constructor(private http:HttpClient) { }

    ngOnInit(): void {
      this.fetchData()
    }

    fetchData(){
      this.http.get('https://jsonplaceholder.typicode.com/users').subscribe((data:any)=>{
        //console.log(data);
        this.userName = data.value;
      });
      //above line return an observable before subscribe
    }

    }
  ```

- The code we write is not the recommended approach
- Jab bhi app mey data(network) se related kaam krte hai to hmme services ka use krna chahiye
  
## Services
- ng g s services/joke
  ```ts
  import { Injectable } from '@angular/core';

    @Injectable({
      providedIn: 'root'
      // iska mtlb ki hum iss service ko puri application mey khin bhi use kar skte hai
    })
    export class JokeService {

      constructor(private http:HttpClient) { }

      getJoke(){
        return this.http.get('https://api.chucknorris.io/jokes/random?category=dev');
      }
    }

  ```
  - Now, our service is ready

- Lets inject this service in our component
- http-client.ts component
  ```ts
  import { Component, OnInit } from '@angular/core';
  import { JokeService } from '../services/joke.service';

  @Component({
    selector: 'app-http-client',
    templateUrl: './http-client.component.html',
    styleUrls: ['./http-client.component.css']
  })
  export class HttpClientComponent implements OnInit {
    joke:string = 'joke';

    constructor(private jokeService:JokeService) { }

    ngOnInit(): void {
      // this.fetchData()
      this.fetchJoke();
    }

    fetchJoke(){
      this.jokeService.getJoke().subscribe((data:any)=>{
        this.joke = data.value;
      })

    }

    // fetchData(){
    //   this.http.get('https://api.chucknorris.io/jokes/random?category=dev').subscribe((data:any)=>{
    //     console.log(data);
    //     this.joke = data.value;
    //   });
    //   //above line return an observable before subscribe
    // }

  }

  ```
## State management using services
- So lets create some components comp-a,b,b2
- Lets create a service called counter
- counter.service.ts
  ```ts
  import { Injectable } from '@angular/core';

  @Injectable({
    providedIn: 'root'
  })
  export class CounterService {
    private counter:number = 0;

    constructor() { }

    getCounter(){
      return this.counter;
    }

    updateCounter(){
      this.counter = this.counter + 1;
    }
  }

  ```
- Both component A and B have same code
  ```ts
  import { Component, OnInit } from '@angular/core';
  import { CounterService } from '../services/counter.service';

  @Component({
    selector: 'app-comp-a',
    templateUrl: './comp-a.component.html',
    styleUrls: ['./comp-a.component.css']
  })
  export class CompAComponent implements OnInit {

    constructor(private counterService:CounterService) { }

    ngOnInit(): void {

    }

    showCounter(){
      this.counterService.getCounter();
    }

    updateCounter(){
      this.counterService.updateCounter();
    }

  }

  ```
  ```html
  <p>Component A - Counter {{showCounter()}} </p>
  <h1>{{showCounter()}}</h1>
  <button class="bg-indigo-500" (click)="updateCounter()">Update Counter</button>

  ```
  -Error, Don't know why {{showCounter()}} not showing, but console works fine
  - We have same code and same service in both component, so when you update any component's button changes reflect in another component also. 


## Reactive(Model Driven) Forms
- In reactive form, most of the code write in ts file and in template driven form most of the code in template(html)
- we create two new components login and register
- First import the ReactiveFormsModule in app.module.ts from @angular/forms for reactive forms and formsModule for template forms.
- Now, import formGroup, formControl and Validators in login.ts from @angular/forms
  ```ts
  // email is property
  // formControl takes two values, 1 is intial value and 2 is array of validators
     email = new FormControl("",[
      Validators.required,
      Validators.email
    ])
    password = new FormControl("",[
      Validators.required,
      Validators.minLength(6)
    ])

    login(){
      console.log(this.email.value, this.password.value)
    }

  ```
  ```html
  <h1>Login Reactive Form</h1>
  <form class="mx-12 my-12">
    <input type="email" [formControl]="email" />
    <!-- we use hidden not ngif because ngif rebuild dom while hidden just show or not -->
    <h2 class="text-red-500" [hidden]="email.valid || email.untouched">Enter correct email</h2>
    <br><br>
    <input type="password" [formControl]="password" />
    <h2 class="text-red-500" [hidden]="password.valid || password.untouched">Enter correct password min length 6</h2>
    <br><br>
    <button class="px-8 py-3 text-white bg-blue-600 rounded " (click)="login()">login</button>
  


  </form>
  <h1>email {{email.value}}</h1>
  <h1>email valid {{email.valid}}</h1>
  <h1>email untouched {{email.untouched}}</h1>
  ```
- We can able to submit emial and password when they showing error
- So, to overcome this issue we can disable the button till all conditions satisfied
  ```ts
   loginForm = new FormGroup({
    email : this.email,
    password : this.password
    })

    login(){
      console.log(this.loginForm.value)
    }

  ```
  ```html
  <h1>Login Reactive Form</h1>
  <form class="mx-12 my-12" [formGroup]="loginForm">
    <input type="email" [formControl]="email" />
    <!-- we use hidden not ngif because ngif rebuild dom while hidden just show or not -->
    <h2 class="text-red-500" [hidden]="email.valid || email.untouched">Enter correct email</h2>
    <br><br>
    <input type="password" [formControl]="password" />
    <h2 class="text-red-500" [hidden]="password.valid || password.untouched">Enter correct password min length 6</h2>
    <br><br>
    <button class="px-8 py-3 text-white bg-blue-600 rounded " [disabled]="loginForm.invalid" (click)="login()">login</button>
  </form>

  ```


## Routing and Navigation
- When you build app code there you can selecting routing to yes
- Than add AppRotingModule in app.module.ts
- And insure this tag  <base href="/"> is present in your index.html
- We can't show hardcoded login form in our body, we have to use router-outlet tag
- Add your components jinka navigation krna hai
  ```ts
    const routes: Routes = [
    {path: 'login', component: LoginComponent},
    {path: 'register', component: RegisterComponent},
    {path: 'user', component: UsersComponent},
    {path: 'profile', component: ProfileComponent}
  ]; 

  ```
- Hum url mey /login, /user kr k ja to rhe hai, but hmme navbar se jana hai
- replace href with routerLink
  ```html
    <a routerLink="login">Login</a>
    <a routerLink="register">Register</a>
    <a routerLink="user">User</a>
    <a routerLink="profile">Profile</a>
  ```
- for default path
    {path: '', redirectTo: '/login', pathMatch:"full"},
- for unknown page, isko hmeesha end mey rkhna (Most important)
    {path: '**', component: NotfoundComponent},

- When a user register, i want to automatically navigate to home page
- first Inject router in constructor as private from Router
- In the function of that button
  this.router.navigate(['/login'])

  
## Route Params