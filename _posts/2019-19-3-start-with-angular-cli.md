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