# Create the heroes component

```
ng generate component heroes
```

-  Add a hero property: heroes.component.ts

   ```typescript
   hero = 'Windstorm';
   ```

- Show the hero: heroes.component.html

  ```html
  <h2>{{hero}}</h2>
  ```

# Show the HeroesComponent view

- app.component.html

  ```html
  <h1>{{title}}</h1>
  <app-heroes></app-heroes>
  ```

# Create a Hero interface

- create an interface module

  ```
  cd src/app
  vim hero.ts
  ```
  
  Add the interface module

  ```typescript
  export interface Hero {
    id: number;
    name: string;
  }
  ```

- 元件引入interface : heroes.component.ts

  ```typescript
  export class HeroesComponent implements OnInit {
  
    hero: Hero = {
      id: 1,
      name: 'Windstorm'
    };
  }
  ```

- 元件顯示interface內容: heroes.component.html

  ```html
  <h2>{{hero.name | uppercase}} Details</h2>
  <div><span>id: </span>{{hero.id}}</div>
  <div><span>name: </span>{{hero.name}}</div>
  ```

# Two-way binding

- 加入 Two-way binding 功能模組: app.module.ts

  ```typescript
  import { FormsModule } from '@angular/forms'; // <-- NgModel lives here

  imports: [
    FormsModule
  ],
  ```

- HTML 新增 Two-way binding 功能: heroes.component.html
 
  ```html
  <div>
    <label for="name">Hero name: </label>
    <input id="name" [(ngModel)]="hero.name" placeholder="name">
  </div>
  ```
