# Getting Started With Angular (Step 3)
Now that we have created **my-app** and have Materials setup, the next steps is to:
- Create a Dashboard Component
- Setup routing for Dashboard Component
- Setup navigation to Dashboard

## Creating a Dashboard component
To create a component we type the following in the terminal window:
```bash
ng generate component component/dashboard
```
This creates an an Angular component under `src/app/component/dashboard`. And the component is also automatically added as a declaration in `src/app/app.module.ts`.

## Setup Routing for Dashboard Component
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

## Setup navigation to Dashboard
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

## Proceed to next step
To proceed to next step check out branch `step-4`, see command below:

```bash
git checkout step-4
```
