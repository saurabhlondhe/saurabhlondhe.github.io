---
layout: post
title:  "Angular and Its CLI"
date:   2019-03-19
desc: ""
keywords: "angular,agular-cli,master,gh-pages,website,blog"
categories: [HTML,Project]
tags: [angular]
icon: icon-angular
---
# Angular and angular-cli
*Angular* is a platform that makes it easy to build applications with the web. Angular combines declarative templates, dependency injection, end to end tooling, and integrated best practices to solve development challenges. Angular empowers developers to build applications that live on the web, mobile, or the desktop.

```angular-cli``` stands for *Angular Command Line Interface*, Angular having a structure and little configurations that can be done by using ```angular-cli``` is no time. 

Angular architecture includes:
-   Modules
-   Components
-   Routing
-   Services

Let's have a brief look to each one

-   [x] Modules
    
    - The basic building blocks of an Angular application are NgModules, which provide a compilation context for components. NgModules collect related code into functional sets; an Angular app is defined by a set of NgModules. An app always has at least a root module that enables bootstrapping, and typically has many more feature modules.

-   [x] Components
    - Every Angular application has at least one component, the root component that connects a component hierarchy with the page document object model (DOM). Each component defines a class that contains application data and logic, and is associated with an HTML template that defines a view to be displayed in a target environment.
    - The ```@Component()``` decorator identifies the class immediately below it as a component, and provides the template and related component-specific metadata.
    - ```@Component``` Basically includes selector name, the definition for HTML and CSS/SCSS (or any styling file ) templates, or just a template code.

        ```typescript
        @Component({
        selector: 'app-root',
        templateUrl: './app.component.html',
        styleUrls: ['./app.component.scss']
        })
        ```


-   [x] Services
    -   For data or logic that isn't associated with a specific view, and that you want to share across components, you create a service class. A service class definition is immediately preceded by the ```@Injectable()``` decorator. The decorator provides the metadata that allows other providers to be injected as dependencies into your class.


-   [x] Routing
    -   The Angular Router NgModule provides a service that lets you define a navigation path among the different application states and view hierarchies in your app. It is modeled on the familiar browser navigation conventions:

        -   Enter a URL in the address bar and the browser navigates to a corresponding page.

        -   Click links on the page and the browser navigates to a new page.

        -   Click the browser's back and forward buttons and the browser navigates backward and forward through the history of pages you've seen.

    ```typescript
    import { NgModule } from '@angular/core';
    import { Routes, RouterModule } from '@angular/router';
    import { HomeComponent } from './home.component.ts'
    const routes: Routes = [
        {
            path:"home",
            componet:"HomeComponent"
        }
    ];

    @NgModule({
    imports: [RouterModule.forRoot(routes)],
    exports: [RouterModule]
    })
    export class AppRoutingModule { }

    ```

The theory might make you sleepy try some hands-on

---

Now, for installing angular cli, follows the steps given below:
-   Install node.js first if not already install (which I think you probably would have downloaded)
Open the node.js command prompt and issue the command:

    ```sh
    npm install -g @angular/cli
    ```

> Note: The -g flag in the above command signifies the fact that the ng-cli is being installed in a global scope.

-   If you want to check out the latest version of angular cli, modify the above-stated command as:
    
    ```sh
    npm install @angular/cli@latest
    ```

> Now, let me list out a few commands for you, which will come handy while creating angular projects:

1.  Creating a new project

    - ```ng new``` will help you with that. Creates a new project structure installs npm packages, creates configurations and many more. . .

2.  Run the project
    - ```ng serve``` allows you to run your angular app on the node server. The default port is localhost:4200. Let's try some tricks with ```ng serve```

    ```sh
    ng serve    #serves project at http://localhost:4200

    ng serve --port 8888    #serves project at port :8888

    ng serve --host 0.0.0.0 #hosts project in LAN can access with local IP address

    ng serve -o #opens project in the default browser

    ```

    > Commands needs to run under the project directory.

3.  Create Components
    - ng generate (or just ng g) command to generate Angular components:
    
    ```sh
    ng generate component component-name

    #or

    ng g c component-name
    ```

Similarly, you can create all other building blocks listed in the table below:

|   | Commands |
| ----------- | ----------- |
| Components | ```ng g c component-name``` |
| Modules | ```ng g module module-name``` |
| Services | ```ng g s service-name``` |
| Class | ```ng g class class-name``` |
| Gaurd | ```ng g gaurd gaurd-name``` |
| Pipe | ```ng g pipe pipe-name``` |

4.  Deploy project

    -  After build Angular project is converted into a JS code.
    -  ```ng build``` is used for dev build and ```ng build --prod``` is used for prod ( production ) build.
    -  This creats a ```./dist/project-name/``` folder with all HTML/CSS and assets which can be deployed on any IIS, Apache servers.