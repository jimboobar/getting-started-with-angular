# Getting Started With Angular (Step 5)
Here you find all the combined steps
- Step-0
- Step-1
- Step-2
- Step-3
- Step-4

## Step-0
This is a simple web project to get started with Angular. First we must:
- Install required software
- Checkout this repository

### Required Software
TODO

### Checkout this repository
To checkout, do the following command:
```bash
prompt$ git clone git@github.com:jimboobar/getting-started-with-angular.git
```

### Proceed to next step
To proceed to next step check out branch `step-1`, see command below:

```bash
prompt$ git checkout step-1
```

## Step-1
Now that we have all required software installed we can move to the followin:
- Install Angular CLI
- Create Angular project

### Install Angular CLI
Follow the official install instructions, available here:
- https://angular.io/guide/setup-local

### Proceed to next step
To proceed to next step check out branch `step-2`, see command below:

```bash
git checkout step-2
```

## Step-2
Now that we have created **my-app**, the next steps are:
- Install Angular Material
- Create Material Module

### Install Angular Material
Follow the official documentation available here:
- https://material.angular.io/guide/getting-started

Go to **my-app**-folder, type `cd my-app` in terminal.

Then type the following to add Angular Material:
```bash
ng add @angular/material
```
When adding:
- Choose a prebuilt theme for simplicity
- Select **Yes** to setup typography styles
- Select **Yes** to setup browser animations
- Then wait for packages to be installed

### Create Material Module
To create our first module we type the following in the terminal window:
```bash
ng generate module modules/material
```
This creates an an Angular module under `src/app/modules/material`.

Then open `src/app/modules/material/material.module.ts` to look like:
```typescript
import { NgModule } from '@angular/core';

const materialModules = [
  // Material modules will be added here as we need them
];

@NgModule({
  imports: materialModules,
  exports: materialModules
})
export class MaterialModule { }
```

### Import Material Module
Now that we have created a module we need to import it to `src/app/app.module.ts`. When done, the result should look like:
```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { BrowserAnimationsModule } from '@angular/platform-browser/animations';
// This is where our module is imported from
import { MaterialModule } from './modules/material/material.module';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    BrowserAnimationsModule,
    MaterialModule // <-- Our module is added here
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

### Proceed to next step
To proceed to next step check out branch `step-3`, see command below:

```bash
git checkout step-3
```

## Step-3
Now that we have created **my-app** and have Materials setup, the next steps is to:
- Create a Dashboard Component
- Setup routing for Dashboard Component
- Setup navigation to Dashboard

### Creating a Dashboard component
To create a component we type the following in the terminal window:
```bash
ng generate component component/dashboard
```
This creates an an Angular component under `src/app/component/dashboard`. And the component is also automatically added as a declaration in `src/app/app.module.ts`.

### Setup Routing for Dashboard Component
To enable routing to Dashboard we must update `src/app/app-routing.module.ts`.
```typescript
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { AppComponent } from './app.component';
import { DashboardComponent } from './components/dashboard/dashboard.component';

const routes: Routes = [
  // Mapping AppComponent to root path
  { path: '', component: AppComponent },
  // Mapping AppComponent to path '/dashboard'
  { path: 'dashboard', component: DashboardComponent },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```
By doing this we can now open `http://localhost:4200/dashboard` in a browser.

### Setup navigation to Dashboard
The HTML tag `<router-outlet></router-outlet>` controls what routed content to be diplsayed.

So lets update `src/app/app.component.html` with some links for navigation:
```html
<ul>
  <li><a href="#" routerLink="/">Home</a></li>
  <li><a href="#" routerLink="/dashboard">Dashboard</a></li>
</ul>
<router-outlet></router-outlet>
```

Now we should be able to verify the changes by starting the development server in terminal:
```bash
ng serve
```

Then open the following URL in a browser `http://localhost:4200`.

### Proceed to next step
To proceed to next step check out branch `step-4`, see command below:

```bash
git checkout step-4
```

## Step-4
Now that we navigate and display varios components, the user experience can be improved:
- Create Navbar using Angular Materials

### Create Navbar using Angular Materials
For this we will start by adding the `MatToolbarModule` to `src/app/modules/material/material.module.ts`.
```typescript
import { NgModule } from '@angular/core';
// Import module here
import { MatToolbarModule } from '@angular/material/toolbar';

const materialModules = [
  MatToolbarModule // Add module to list of modules
];

@NgModule({
  imports: materialModules,
  exports: materialModules
})
export class MaterialModule { }
```

Next we update `src/app/app.component.html` to look like:
```html
<mat-toolbar class="navbar" color="primary">
  <div>My-App</div>
  <div>
    <span routerLink="/dashboard">Dashboard</span>
  </div>
</mat-toolbar>
<router-outlet></router-outlet>
```

Then update `src/app/app-routing.module.ts` to add a redirect on root, the result should look like:
```typescript
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { AppComponent } from './app.component';
import { DashboardComponent } from './components/dashboard/dashboard.component';

const routes: Routes = [
  // Redirect root to '/dashboard'
  { path: '', redirectTo: '/dashboard', pathMatch: 'full' },
  { path: 'dashboard', component: DashboardComponent },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

And finally adding some minor styling in `src/app/app.component.css` like this:
```css
.navbar {
    justify-content: space-between;
}

span {
    padding: 0 1rem;
}
```

Now when we run `ng serve` in the terminal we should see a navigation bar when loading `http://localhost:4200` in a browser!

### Next step
A next step could be to create another Angular Component of choice, add routing for the component in `src/app/app-routing.module.ts`, and add the corresponding `routerLink` in the navigarion bar.

For additional styling with Angular Material, have a look at:
- https://material.angular.io/components/categories

For a final solution, checkout `step-5`:
```bash
git checkout step-5
```
