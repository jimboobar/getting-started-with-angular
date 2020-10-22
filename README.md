# Getting Started With Angular (Step 2)
Now that we have created **my-app**, the next steps are:
- Install Angular Material
- Create Material Module

## Install Angular Material
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

## Create Material Module
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

## Import Material Module
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

## Proceed to next step
To proceed to next step check out branch `step-3`, see command below:

```bash
git checkout step-3
```
