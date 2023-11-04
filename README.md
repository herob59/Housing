Angular 14 introduces the standalone component—a component not part of any ngModule that can be used with either other
standalone or module-based components.
What Is a Standalone Component?
A standalone component is a type of component which is not part of any Angular module. Prior to Angular 14, usually when you would create a component, you’d pass it inside the declarations array of a module. If you would not do that, Angular would complain about it and not compile. However, as of Angular 14, you can create a component that is not part of any ngModule, and that component is known as a standalone component.

Besides standalone components, in Angular 14, you can also create:

Standalone directives
Standalone pipes
You can use a standalone component with:

Module-based components
Other standalone components
Loading routes
Lazy loading
 
Angular 14 introduces the standalone component—a component not part of any ngModule that can be used with either other standalone or module-based components.

Standalone: true

Starting with Angular 14, you can create the whole application without making any custom Angular modules, which is possible by using standalone components, which provide simplified ways to create an Angular application.

What Is a Standalone Component?
A standalone component is a type of component which is not part of any Angular module. Prior to Angular 14, usually when you would create a component, you’d pass it inside the declarations array of a module. If you would not do that, Angular would complain about it and not compile. However, as of Angular 14, you can create a component that is not part of any ngModule, and that component is known as a standalone component.

Besides standalone components, in Angular 14, you can also create:

Standalone directives
Standalone pipes
You can use a standalone component with:

Module-based components
Other standalone components
Loading routes
Lazy loading
A standalone pipe looks like the below:

import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'search',
  standalone: true
})
export class SearchPipe implements PipeTransform {

  transform(value: unknown, ...args: unknown[]): unknown {
    return null;
  }
}
-
Creating a Standalone Component
You can create a standalone component, pipe or directive by using the --standalone flag in the ng generate component command:

ng g p search --standalone
ng g d credit-card --standalone
ng g c login --standalone

import { Component, OnInit } from '@angular/core';
import { CommonModule } from '@angular/common';

@Component({
  selector: 'app-login',
  standalone: true,
  imports: [CommonModule],
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css']
})
export class LoginComponent implements OnInit {

  constructor() { }

ngOnInit(): void {
  }

}

You can also convert an existing component into a standalone component by setting its standalone property to true. You must keep these three points in mind while converting a module-based component to a standalone one:

Set the standalone property to true.
Remove it from the declaration array of the module of which it was a part.
Use imports array to add dependencies.

Dependencies in Standalone Component
A standalone component may depend on other members, pipes and directives. These dependencies can be divided into two parts:

Standalone
Part of a module
Both types of dependencies can be added to a standalone component using the imports array of the @Component decorator. For example, ReactiveFormsModule can be added to the LoginComponent by passing it to the imports array as shown in the below code listing:


# Housing

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 16.2.9.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
