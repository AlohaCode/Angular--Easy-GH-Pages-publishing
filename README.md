# NgCalc
This is a simple Angular project that demonstrates use of the npm angular-cli-ghpages package to quickly and easily publish an Angular project to Github Pages.
The app itself is a simple calculator.  The point of this repo is to demonstrate how to use npm's angular-cli-ghpages package to publish the project.  

## A project built with **CodeAnywhere.com**
Sign up for a free account @ https://codeAnywhere.com.  
Then, create a new project and a new connection with the "Node.js on Ubuntu" connection wizard.

## Set Up for Angular
This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.7.4.
To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).

Within the IDE's newly created "connection" (think: sub-project), the IDE defaults to a terminal view at the connection root. In this terminal, 
use the following commands to set up for Angular:

1. $ nvm install node (installs latest node version, needed by angular-cli)
2. $ nvm ls (see which version was installed, use that version in next command)
3. $ nvm alias default <new version> (makes version the workspace default, i.e.: "9.1")
4. $ npm i -g npm (updates npm version to match new node version)
5. $ npm install -g @angular/cli  (installs angular-cli in global context)
6. $ ng new <my-app-name>  (substitute the name of your angular project, i.e. "ng-calc")
7. $ Change package.json “scripts.start” entry to :
           "start": "ng serve --host 0.0.0.0 --port 3000 --public $<connectionName>-<userName>.codeanyapp.com",
8. By default the IDE should have also opened an info tab which contains the https URL to view the application.  
   Use this URL to formulate the "connectionName" and "userName" values in the previous step. Also use this URL
   to view the running application when the ng has been started.
   
## Create the App
1. In this app we will be using the Forms Module's ngModule class, so Angular's Forms Module needs to be added to the app.module.ts file
      - Be sure to include the forms module in the app.module.ts imports at the top of the file:
            import { FormsModule } from '@angular/forms';
      - Add the FormsModule to the @NgModule decorator's "import" node:
            imports: [
                BrowserModule,
                FormsModule
            ],      
2. Within the app.component.ts file, replace the class declaration with the following:

   

>      export class AppComponent {
>             title = 'Calculator App';
>             num1: number;
>             num2: number;
>             result: number;
>             add() {
>                 this.result = this.num1 + this.num2;
>             }
>             substract() {
>                 this.result = this.num1 - this.num2;
>             }
>             multiply() {
>                 this.result = this.num1 * this.num2;
>             }
>             divide() {
>                 this.result = this.num1 % this.num2;
>             }
>         }

    
3. Change the app.component.html file so it contains the following (swipe it):

>     <div style="text-align:center">
>       <h1>
>         Welcome to {{ title }}!
>       </h1>
>       <img width="300" alt="Angular Logo" src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNTAgMjUwIj4KICAgIDxwYXRoIGZpbGw9IiNERDAwMzEiIGQ9Ik0xMjUgMzBMMzEuOSA2My4ybDE0LjIgMTIzLjFMMTI1IDIzMGw3OC45LTQzLjcgMTQuMi0xMjMuMXoiIC8+CiAgICA8cGF0aCBmaWxsPSIjQzMwMDJGIiBkPSJNMTI1IDMwdjIyLjItLjFWMjMwbDc4LjktNDMuNyAxNC4yLTEyMy4xTDEyNSAzMHoiIC8+CiAgICA8cGF0aCAgZmlsbD0iI0ZGRkZGRiIgZD0iTTEyNSA1Mi4xTDY2LjggMTgyLjZoMjEuN2wxMS43LTI5LjJoNDkuNGwxMS43IDI5LjJIMTgzTDEyNSA1Mi4xem0xNyA4My4zaC0zNGwxNy00MC45IDE3IDQwLjl6IiAvPgogIDwvc3ZnPg==">
>     </div>
>     <div class="container">
>         <br />
>         <div class="row">
>             <div class="col-md-6">
>                 <input type="number" [(ngModel)]="num1" placeholder="Enter Number 1" class="form-control" />
>             </div>
>             <div class="col-md-6">
>                 <input type="number" [(ngModel)]="num2" placeholder="Enter Number 2" class="form-control" />
>             </div>
>         </div>
>         <br />
>         <div class="row text-center">
>             <div class="col-md-3">
>                 <button class="btn btn-info" (click)='add()'>Add</button>
>             </div>
>             <div class="col-md-3">
>                 <button class="btn btn-info" (click)='substract()'>Substract</button>
>             </div>
>             <div class="col-md-3">
>                 <button class="btn btn-info" (click)='multiply()'>Multiply</button>
>             </div>
>             <div class="col-md-3">
>                 <button class="btn btn-info" (click)='divide()'>Divide</button>
>             </div>
>         </div>
>         <br />
>         <div class="row">
>             <div class="col-md-5 col-md-offset-4">
>                 <h2>Result = {{result}} </h2>
>             </div>
>         </div>
>     </div>

    
4. Save off each of these files.  Back in the terminal change to the Angular project's directory (i.e. $ cd ng-calc)    

5. Use the npm start command to build the project and start the server: $ npm start

6. Use the https URL in the IDE's info tab to load and view the app.  
   If the info tab is not open in the editor, right-click the connection node in the left-hand side tree view of the IDE and select "Info".

7. Debug anything necessary to get the app running correctly.7

8. In your github account, create a new repo for this project with a descriptive name (i.e. "ng-calculator").8

9. In the terminal, in the project's context, use the following command to add your new github repo as a 
   remote file to the local project (be sure to change the username and project name to match your Github properties):
   $ git remote add origin https://github.com/USERNAME/PROJECT_NAME.git
   
10. Verify that the repo was properly added with the following command:
   $ git remote -v  (you should see a fetch and a push line in the output)
   
11. The angular-cli-ghpages package can now be installed with the following command:
   $ npm i -g angular-cli-ghpages
   
12. With the package installed, use Angular CLI to build the project 
   with the following command (be sure to use your Github username and repo name)   
   $ ng build --prod --base-href https://alohacode.github.io/ng-calculator/
   
13. Finally, use the following command to publish the project on Github Pages:
   $ ngh -no-silent
   
14. Navigate to **https://[username].github.io/[reponame]/** to see it on GitHub 
   (be sure to use our Github username and repo name).    
   

    
    



