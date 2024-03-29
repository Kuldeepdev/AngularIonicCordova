#Angular
##-------------------------------------GETTING STARTED------------------------------------------

###ANGULAR CLI:
The Angular CLI is a command line interface tool that can create a project, add files, and perform a variety of ongoing development tasks
such as testing, bundling, and deployment.

####Step 1. Set up the Development Environment 
      Install Node.js® and npm
      Install the Angular CLI  :   npm install -g @angular/cli

####Step 2. Create a new project 
        ng new my-app

####Step 3: Serve the application 
        ng serve --open



##------------------------------------FILE STRUCTURE--------------------------------------------
###ROOT FOLDER
e2e/            :- Inside e2e/ live the end-to-end tests.
node_modules/   :- Node.js creates this folder and puts all third party modules listed in package.json inside of it.
.editorconfig   :- Simple configuration for your editor to make sure everyone that uses your project has the same basic configuration. Most editors support an .editorconfig file. See http://editorconfig.org for more information.
.gitignore      :- Git configuration to make sure autogenerated files are not committed to source control.
angular.json    :- Configuration for Angular CLI. In this file you can set several defaults and also configure what files are included when your project is built.
package.json    :- npm configuration listing the third party packages your project uses.
tsconfig.json   :- TypeScript compiler configuration for your IDE to pick up and give you helpful tooling.
tslint.json     :- Linting configuration for TSLint together with Codelyzer, used when running ng lint

###SRC FOLDER

main.ts            :- The main entry point for your app. Compiles the application with the JIT compiler and bootstraps the application's root module (AppModule) to run in the browser. You can also use the AOT compiler without changing any code by appending the--aot flag to the ng build and ng serve commands.
polyfills.ts       :- Different browsers have different levels of support of the web standards. Polyfills help normalize those differences. You should be pretty safe with core-js and zone.js
environments/*     :- This folder contains one file for each of your destination environments, each exporting simple configuration variables to use in your application. The files are replaced on-the-fly when you build your app. You might use a different API endpoint for development than you do for production or maybe different analytics tokens. You might even use some mock services. Either way, the CLI has you covered.
tslint.json        :- Additional Linting configuration for TSLint
tsconfig           :- TypeScript compiler configuration for the Angular app
test.ts            :- This is the main entry point for your unit tests.
app/app.component  :- It is the root component 
app/app.module.ts  :- Defines AppModule, the root module that tells Angular how to assemble the application. 
assets/*           :- A folder where you can put images and anything else to be copied wholesale when you build your application.

##-------------------------------------BADIC CONSEPT---------------------------------------------




##ANGULAR:
Angular is a platform and framework for building client applications in HTML and TypeScript. Angular is written in TypeScript.


##MODULES:
Modules allow to manage code into distinct functional modules, that allow managing complex appliction & reusability.

Organizing your code into distinct functional modules helps in managing development of complex applications, and in designing for reusability.
In addition, this technique lets you take advantage of lazy-loading—that is, loading modules on demand—to minimize the amount of code that needs to be loaded at startup.
They can import functionality that is exported from other NgModules, and export selected functionality for use by other NgModules.

@NgModule Defines a module that contains components, directives, pipes, and providers.
@NgModule({ declarations: ..., imports: ...,
exports: ..., providers: ..., bootstrap: ...})
class MyModule {}
declarations :  List of components, directives, and pipes that belong to this module.
imports      :  List of modules to import into this module. Everything from the imported modules is available to declarations of this module.
exports      :  List of components, directives, and pipes visible to modules that import this module.
providers    :  List of dependency injection providers visible both to the contents of this module and to importers of this module.
bootstrap    :  The main application view, called the root component, which hosts all other app views. Only the root NgModule should set the bootstrap property.

NgModules and JavaScript modules
The NgModule system is different from and unrelated to the JavaScript (ES2015) module system for managing collections of JavaScript objects.
In JavaScript each file is a module and all objects defined in the file belong to that module. The module declares some objects to be public by marking them with the export key word. Other JavaScript modules use import statements to access public objects from other modules.

At a high level, NgModules are a way to organize Angular apps and they accomplish this through the metadata in the @NgModule decorator. The metadata falls into three categories:
Static: Compiler configuration which tells the compiler about directive selectors and where in templates the directives should be applied through selector matching. This is configured via the declarations array.
Runtime: Injector configuration via the providers array.
Composability/Grouping: Bringing NgModules together and making them available via the imports and exports arrays.
content_copy
@NgModule({
  // Static, that is compiler configuration
  declarations: [], // Configure the selectors
  entryComponents: [], // Generate the host factory
 
  // Runtime, or injector configuration
  providers: [], // Runtime injector configuration
 
  // Composability / Grouping
  imports: [], // composing NgModules together
  exports: [] // making NgModules available to other parts of the app
})

REFERENCE: https://angular.io/guide/architecture-modules


##DIRECTIVE:
Angular templates are dynamic. When Angular renders them, it transforms the DOM according to the instructions given by directives. A directive is a class with a @Directive() decorator.
A component is technically a directive. However, components are so distinctive and central to Angular applications that Angular defines the @Component() decorator, which extends the @Directive() decorator with template-oriented features.

A great way to do this is with directives. I think the difference between a directive and a component is pretty hard to understand conceptually. The best way I’ve heard it explained is that you would use a directive when you want to modify the behaviour of an existing DOM (Document Object Model) element, and you would create a component when you want a completely new DOM element. Otherwise, a component and a directive are pretty much the same thing, a component is just a directive with its own template.

   TYPE: 
   1 structural : Structural directives alter layout by adding, removing, and replacing elements in the DOM. 
                  *ngFor, *ngIf
   2 attribute  : Attribute directives alter the appearance or behavior of an existing element.
                  ngStyle, ngClass
Custome Directive:
<p appHighlight>Highlight me!</p>

import { Directive, ElementRef } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
    constructor(el: ElementRef) {
       el.nativeElement.style.backgroundColor = 'yellow';
    }
}

COMPONENTS:
A component controls a patch of screen called a view.
Component is a class that contains data & logic of application, component is associated with view.

Each component defines a class that contains application data and logic,
and is associated with an HTML template that defines a view to be displayed in a target environment.

CUSTOM VIEW COMPONENT:
home.html
<common-action [item]="item" (componentFunction)="pageFunction($event)"></common-action>
home.ts
pageFunction(event){
    console.log(event)
}
common-action.ts
    @Input() item;
    @Output() componentFunction = new EventEmitter();
    anyFunction(){
        this.componentFunction.emit(this.item);
    }
common-action.html
    {{item.name}}

DECORATORS:
Decorators are functions that modify JavaScript classes. Angular defines a number of decorators that attach specific kinds of metadata to classes, so that the system knows what those classes mean and how they should work.
There are four main types:
    Class decorators, e.g. @Component and @NgModule
    Property decorators for properties inside classes, e.g. @Input and @Output
    Method decorators for methods inside classes, e.g. @HostListener
    Parameter decorators for parameters inside class constructors, e.g. @Inject

PIPES:
A pipe takes in data as input and transforms it to a desired output.

Angular pipes let you declare display-value transformations in your template HTML.
Built-in pipes: DatePipe, UpperCasePipe, LowerCasePipe, CurrencyPipe, and PercentPipe
                date, currency
Parameterizing a pipe : To add parameters to a pipe, follow the pipe name with a colon ( : ) and then the parameter value (such as currency:'EUR'). If the pipe accepts multiple parameters, separate the values with colons (such as slice:1:5)

Chaining pipes: You can chain pipes together in potentially useful combinations. {{ birthday | date | uppercase}}

Custom pipes: 
import { Pipe, PipeTransform } from '@angular/core';
@Pipe({
  name: 'limitText'
})
class LimitText implements PipeTransform{
  transforms(text: string, args){
    return text.sub
  }
}

Pure and impure pipes:
Angular executes a pure pipe only when it detects a pure change to the input value. A pure change is either a change to a primitive input value (String, Number, Boolean, Symbol) or a changed object reference (Date, Array, Function, Object).

Angular ignores changes within (composite) objects. It won't call a pure pipe if you change an input month, add to an input array, or update an input object property.
@Pipe({
  name: 'flyingHeroesImpure',
  pure: false
})
REFERENCE :https://angular.io/guide/pipes


SERVICE:
Service allow share data & logic across component. Injectable decorator allow to inject service into client component.

You can inject a service into a component, giving the component access to that service class.

Configure an injector with a service provider:
The class we have created provides a service. The @Injectable() decorator marks it as a service that can be injected.
The injector is responsible for creating service instances and injecting them into classes.

You can configure injectors with providers at different levels of your app, by setting a metadata value in one of three places:
    In the @Injectable() decorator for the service itself. :  providedIn
    In the @NgModule() decorator for an NgModule.
    In the @Component() decorator for a component.
The @Injectable() decorator has the providedIn metadata option, where you can specify the provider of the decorated service class with the root injector, or with the injector for a specific NgModule.
The @NgModule() and @Component() decorators have the providers metadata option, where you can configure providers for NgModule-level or component-level injectors.

For data or logic that you want to share across components, you create a service class.
A service class definition is immediately preceded by the @Injectable() decorator. The decorator provides the metadata that allows your service to be injected into client components as a dependency.

DEPENDENCY INJECTION(DI): 
Dependencies are services or objects that a class needs to perform its function.
DI is a coding pattern in which a class asks for dependencies from external sources rather than creating them itself.

ROUTING: 
The Angular Router enables navigation from one view to the next as users perform application tasks.
        Router outlet : you've placed in the host view's HTML
        Router links  : 

<base href> : Most routing applications should add a <base> element to the index.html as the first child in the <head> tag to tell the router how to compose navigation URLs.
                <base href="/">
Router imports:
    import { RouterModule, Routes } from '@angular/router';

Configuration:
configures the router via the RouterModule.forRoot() method.

Router outlet:
The RouterOutlet is a directive from the router library that is used like a component. It acts as a placeholder that marks the spot in the template where the router should display the components for that outlet.
<router-outlet></router-outlet>

Router links:
The RouterLink directives on the anchor tags give the router control over those elements. 
<a routerLink="/list" routerLinkActive="active">Crisis Center</a>

RouterLinkActive:
The RouterLinkActive directive toggles css classes for active RouterLink bindings based on the current RouterState.
<a routerLink="/list" routerLinkActive="active">Crisis Center</a>

Router Service:
router.navigate(['detail', 33]);
router.navigateByUrl("/team/33/user/11");

Router state:
You can access the current RouterState from anywhere in the application using the Router service and the routerState property.


Activated route:
The route path and parameters are available through an injected router service called the ActivatedRoute. 
--
1 import { ActivatedRoute } from '@angular/router';
2 constructor(private route: ActivatedRoute){}
3A this.route.params.subscribe(params => {
        const id: number = +params['id'];
   });
3B   let id = this.route.snapshot.paramMap.get('id');

Router events:
During each navigation, the Router emits navigation events through the Router.events property.


--Example--
--src/app/app-routing.module.ts--
import { NgModule } from '@angular/core';
import { PreloadAllModules, RouterModule, Routes } from '@angular/router';
import { PageNotFoundComponent } from './page-not-found/page-not-found.component';
const routes: Routes = [
  {
    path: '',
    redirectTo: 'home',
    pathMatch: 'full'
  },
  {
    path: 'home',
    loadChildren: './pages/home/home.module#HomePageModule'
  },
  { path: 'detail/:id', loadChildren: './pages/detail/detail.module#DetailPageModule' },
  { path: '**', component: PageNotFoundComponent }
];

@NgModule({
  imports: [
    RouterModule.forRoot(routes, { preloadingStrategy: PreloadAllModules })
  ],
  exports: [RouterModule]
})
export class AppRoutingModule {}


--src/app/app.module.ts--
import { NgModule }       from '@angular/core';
import { BrowserModule }  from '@angular/platform-browser';
import { FormsModule }    from '@angular/forms';
 
import { AppComponent }     from './app.component';
import { AppRoutingModule } from './app-routing.module';
 
@NgModule({
  imports: [
    BrowserModule,
    FormsModule,
    AppRoutingModule
  ],
  declarations: [
    AppComponent
  ],
  bootstrap: [ AppComponent ]
})
export class AppModule { }

REFERENCE : https://angular.io/guide/router


DATA BINDING:
    TYPE:
    1 Interpolation : You met the double-curly braces of interpolation, {{ and }}, early in your Angular education.
    2 Property binding : from a component to an element.
    lets you interpolate values that are computed from your application data into the HTML.
                         <videoItem [items]="items"></videoItem>
                         <img [src]="heroImageUrl">
    3 Event binding    : from an element to a component.
    lets your app respond to user input in the target environment by updating your application data.
                         <li (click)="go()"></li>
    4 Attribute binding :
        You can set the value of an attribute directly with an attribute binding.
        <tr><td [attr.colspan]="1 + 1">One-Two</td></tr>
    5 Class binding
        You can add and remove CSS class names from an element's class attribute with a class binding.
        [class]="badCurly"
        [class.special]="isSpecial"
    6 Style binding
        You can set inline styles with a style binding.
        [style.color]="isSpecial ? 'red': 'green'"
    7 Two-way data binding
            Two-way data binding: combines property and event binding in a single notation.
                          <input [(ngModel)]="name">
                          <input [ngModel]="currentHero.name"  (ngModelChange)="setUppercaseName($event)">


OBSERVABLES:
Observables provide support for passing messages between publishers and subscribers in your application.
Observables offer significant benefits over other techniques for event handling, asynchronous programming, and handling multiple values.

The subscribe() call returns a Subscription object that has an unsubscribe() method, which you call to stop receiving notifications.

three types of notifications that an observable can send:
next	     Required. A handler for each delivered value. Called zero or more times after execution starts.
error	     Optional. A handler for an error notification. An error halts execution of the observable instance.
complete	 Optional. A handler for the execution-complete notification. Delayed values can continue to be delivered to the next handler after execution is complete.

    let s = new Subject();
    s.subscribe((a)=>{
      console.log(a);
    })
    s.next("Hi");

    let myObservable = Observable.create(observer => {
	    observer.next("hello");
    });

    myObservable.subscribe((data) => {
	    console.log(data);
    });
PROMISE:

promiseFunciton(val): Promise<any>{
   return new Promise((resolve, reject)=>{ 
            if(val ==1){
               setTimeout(()=>{ resolve(1)}, 3000)
            }else{
                reject(2)
            }
    })
}
async asyncFunction(val){
    let i = await this.promiseFunciton(val);
    console.log("async",i)
}
----------------------
this.promiseFunciton(1)
.then((success)=>{
      console.log("success")
}).catch((error)=>{
      console.log("error")
});
this.asyncFunction(1);

LIFECYCLE:
ngOnChanges           : Respond when Angular (re)sets data-bound input properties.
ngOnInit              : Called once, Initialize the directive/component after Angular first displays the data-bound properties
ngDoCheck             : Detect and act upon changes that Angular can't or won't detect on its own.
ngAfterContentInit    : Angular calls after Angular projects external content into the component.
ngAfterContentChecked : After every check of component content.
ngAfterViewInit       : Angular calls after it creates a component's child views.
ngAfterViewChecked    : After every check of a component's views.
ngOnDestroy           : Just before the directive is destroyed.

AHEAD OF TIME AOT:-
The Angular ahead-of-time (AOT) compiler converts Angular HTML and TypeScript code into efficient JavaScript code during the build phase,
before the browser downloads and runs that code.
This is the best compilation mode for production environments,

JUST IN TIME JIT:-
The Angular just-in-time (JIT) compiler converts your Angular HTML and TypeScript code into efficient JavaScript code at run time,
JIT compilation is the default (as opposed to AOT compilation) when you run Angular's ng build and ng serve CLI commands,
and is a good choice during development.

LAZY LOADING:-
A process that speeds up application load time by splitting the application into multiple bundles and loading them on demand. 



FORMs:
Reactive and template-driven forms process and manage form data differently. Each offers different advantages.
Reactive Forms:
Reactive forms are more robust: they're more scalable, reusable, and testable. If forms are a key part of your application, or you're already using reactive patterns for building your application, use reactive forms.
Template-driven Forms:
Template-driven forms are useful for adding a simple form to an app, such as an email list signup form. They're easy to add to an app, but they don't scale as well as reactive forms. If you have very basic form requirements and logic that can be managed solely in the template, use template-driven forms.

--------------------------------------------------------------OTHER CONSEPT--------------------------------------------------------------------------

--------------------------------------------------------------IONIC-------------------------------------------------------------------
Events :-
Events is a publish-subscribe style event system for sending and responding to application-level events across your app.

import { Events } from 'ionic-angular';

// first page (publish an event when a user is created)
constructor(public events: Events) {}
createUser(user) {
  console.log('User created!')
  this.events.publish('user:created', user, Date.now());
}


// second page (listen for the user created event after function is called)
constructor(public events: Events) {
  events.subscribe('user:created', (user, time) => {
    // user and time are the same arguments passed in `events.publish(user, time)`
    console.log('Welcome', user, 'at', time);
  });
}

Ionic Page Life Cycle :

ionViewWillEnter	Fired when the component routing to is about to animate into view.
ionViewDidEnter	    Fired when the component routing to has finished animating.
ionViewWillLeave	Fired when the component routing from is about to animate.
ionViewDidLeave	    Fired when the component routing to has finished animating.




Angular Router: Preloading Modules:
The issue with lazy loading, of course, is that when the user navigates to the lazy-loadable section of the application, the router will have to fetch the required modules from the server, which can take time.
To fix this problem we have added support for preloading. Now the router can preload lazy-loadable modules in the background while the user is interacting with our application.
Enabling Preloading: To enable preloading we need to pass a preloading strategy into forRoot.
imports: [RouterModule.forRoot(ROUTES, {preloadingStrategy: PreloadAllModules})]
The latest version of the router ships with two strategies: preload nothing and preload all modules, but you can provide you own. And it is actually a lot simpler that it may seem.
 Say we don’t want to preload all the modules. Rather, we would like to say explicitly, in the router configuration, what should be preloaded.
[
  {
    path: 'moduleA',
    loadChildren: './moduleA.module',
    data: {preload: true}
  },
  {
    path: 'moduleB',
    loadChildren: './moduleB.module'
  }
]
Custom Preloading Strategy:
export class PreloadSelectedModulesList implements PreloadingStrategy {
  preload(route: Route, load: Function): Observable<any> {
    return route.data && route.data.preload ? load() : of(null);
  }
}
reference : https://vsavkin.com/angular-router-preloading-modules-ba3c75e424cb


Route Guards:
Angular’s route guards are interfaces which can tell the router whether or not it should allow navigation to a requested route.
There are five different types of guards
CanActivate : It guards a link and allow to access conditionally such as in user authentication application.
CanActivateChild : As we learned about guarding routes with CanActivate, we can also protect child routes with the CanActivateChild guard. The CanActivateChild guard works similarly to the CanActivate guard, but the difference is its run before each child route is activated. We protected our admin feature module from unauthorized access, but we could also protect child routes within our feature module.
CanDeactivate : guard which decides if a route can be deactivated. for example, suppose a user is changing form data and before saving, user tries to navigate away. In this scenario we can use CanDeactivate guard which will deactivate the route and open a Dialog Box to take user confirmation.
CanLoad
Resolve
import { Injectable } from '@angular/core';
import { ActivatedRouteSnapshot, RouterStateSnapshot, Router, CanActivate } from '@angular/router';

@Injectable({
  providedIn: 'root'
})
export class IntroGuard implements  CanActivate {
  constructor(public router: Router) {}
  async canActivate(
    next: ActivatedRouteSnapshot,
    state: RouterStateSnapshot
  ): Promise<boolean> {
    let isComplete = true;
    if (localStorage.getItem('isFirstTime') == null) {
      this.router.navigateByUrl('/intro');
      isComplete = false;
     }
    return isComplete;
  }
}

{
    path: '',
    loadChildren: './pages/home/home.module#HomePageModule',
    canActivate: [IntroGuard]
  }
Reference: https://www.concretepage.com/questions/597

------------------JS------------
What is a closure?
A closure is an inner function that has access to the outer (enclosing) function’s variables—scope chain. 

function showName (firstName, lastName) {
var nameIntro = "Your name is ";
    // this inner function has access to the outer function's variables, including the parameter
function makeFullName () {      
return nameIntro + firstName + " " + lastName; 
}

return makeFullName ();
}

showName ("Michael", "Jackson"); // Your name is Michael Jackson



---------------
JavaScript Event Loop: 
Ref: https://flaviocopes.com/javascript-event-loop/

Your JavaScript code runs single threaded. There is just one thing happening at a time.
The call stack: The event loop continuously checks the call stack to see if there’s any function that needs to run.While doing so, it adds any function call it finds to the call stack and executes each one in order.

The event loop on every iteration looks if there’s something in the call stack, and executes it, until the call stack is empty.
The use case of setTimeout(() => {}), 0) is to call a function, but execute it once every other function in the code has executed.

The Message Queue: When setTimeout() is called, the Browser or Node.js start the timer. Once the timer expires, in this case immediately as we put 0 as the timeout, the callback function is put in the Message Queue.
The loop gives priority to the call stack, and it first processes everything it finds in the call stack, and once there’s nothing in there, it goes to pick up things in the message queue.

ES6 Job Queue: 
ECMAScript 2015 introduced the concept of the Job Queue, which is used by Promises (also introduced in ES6/ES2015). It’s a way to execute the result of an async function as soon as possible, rather than being put at the end of the call stack.


-------------------------
JavaScript function as class
  <script>
    function a (){
      windowvar = 100;
      this.i = 10;
      this.setI = (i)=>{
        this.i = i;
      }
      this.getI = ()=>{
        console.log(this.i);
      }
    }
    a.prototype.setGetI = (i)=>{
      this.i = i;
      console.log(i);
    }

    let obj = new a();
    console.log(obj.i, window.windowvar);
    obj.setI(20);
    obj.getI();
    obj.setGetI(30);
    
  </script>