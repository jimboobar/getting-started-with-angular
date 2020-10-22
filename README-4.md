# Getting Started With Angular (Step 4)
Now that we navigate and display varios components, the user experience can be improved:
- Create Navbar using Angular Materials

## Create Navbar using Angular Materials
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

## Next step
A next step could be to create another Angular Component of choice, add routing for the component in `src/app/app-routing.module.ts`, and add the corresponding `routerLink` in the navigarion bar.

For additional styling with Angular Material, have a look at:
- https://material.angular.io/components/categories

For a final solution, checkout `step-5`:
```bash
git checkout step-5
```
