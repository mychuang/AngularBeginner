# Create mock heroes

新建一個列表清單, 基於 Interface 模組

```
cd src/app
vi mock-heroes.ts
```

```typescript
import { Hero } from './hero';

export const HEROES: Hero[] = [
  { id: 12, name: 'Dr. Nice' },
  { id: 13, name: 'Bombasto' },
  { id: 14, name: 'Celeritas' },
  { id: 15, name: 'Magneta' },
  { id: 16, name: 'RubberMan' },
  { id: 17, name: 'Dynama' },
  { id: 18, name: 'Dr. IQ' },
  { id: 19, name: 'Magma' },
  { id: 20, name: 'Tornado' }
];
```

# Displaying heroes

- 引入與使用 列表清單 模組: heroes.component.ts

  ```typescript
  import { HEROES } from '../mock-heroes';

  export class HeroesComponent implements OnInit {
    heroes = HEROES;
  }
  ```

- List heroes with ***ngFor**: heroes.component.html

  ```html
  <h2>My Heroes</h2>
  <ul class="heroes">
    <li *ngFor="let hero of heroes">
      <button type="button">
        <span class="badge">{{hero.id}}</span>
        <span class="name">{{hero.name}}</span>
      </button>
    </li>
  </ul>
  ```

# Add a click event binding

- heroes.component.html

  ```html
  <li *ngFor="let hero of heroes">
    <button type="button" (click)="onSelect(hero)">
    <!-- ... -->
  ```

- heroes.component.ts

  ```typescript
  selectedHero?: Hero;
  onSelect(hero: Hero): void {
    this.selectedHero = hero;
  }
  ```

# Add a details section

heroes.component.html

```html
<div *ngIf="selectedHero">
  <h2>{{selectedHero.name | uppercase}} Details</h2>
  <div>id: {{selectedHero.id}}</div>
  <div>
    <label for="hero-name">Hero name: </label>
    <input id="hero-name" [(ngModel)]="selectedHero.name" placeholder="name">
  </div>
</div>
```

# Style the selected hero

heroes.component.html

```html
<li *ngFor="let hero of heroes">
  <button [class.selected]="hero === selectedHero" type="button" (click)="onSelect(hero)">
    <span class="badge">{{hero.id}}</span>
    <span class="name">{{hero.name}}</span>
  </button>
</li>
```
