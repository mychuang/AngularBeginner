# Add the AppRoutingModule

```
ng generate module app-routing --flat --module=app
```

- --flat	Puts the file in src/app instead of its own directory.

- --module=app	Tells ng generate to register it in the imports array of the AppModule

Update app-routing.module.ts

```typescript
import { RouterModule, Routes } from '@angular/router';
import { HeroesComponent } from './heroes/heroes.component';

const routes: Routes = [
  { path: 'heroes', component: HeroesComponent }
];
```

# Add a navigation link using routerLink

app.component.html 

```html
<h1>{{title}}</h1>
<nav>
  <a routerLink="/heroes">Heroes</a>
</nav>
<router-outlet></router-outlet>
<app-messages></app-messages>
```
