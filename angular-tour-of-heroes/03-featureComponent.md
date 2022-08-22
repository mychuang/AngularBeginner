# Create a feature component
本章節是將前章節的組件, 細拆成兩個組件

- A HeroesComponent that presents the list of heroes.
- A HeroDetailComponent that presents the details of a selected hero.

# Make the HeroDetailComponent

- create detail component

  ```shell
  ng generate component hero-detail
  ```

- 將前章做的 div 細節, 移至 hero-detail.component.html

  ```html
  <div *ngIf="hero">
    <h2>{{hero.name | uppercase}} Details</h2>
      <div><span>id: </span>{{hero.id}}</div>
      <div>
        <label for="hero-name">Hero name: </label>
        <input id="hero-name" [(ngModel)]="hero.name" placeholder="name">
      </div>
  </div>
  ```

- Add the @Input() hero property<p>

  透過 @Input() 可在不同Component 間傳送資料<p>

  修改 hero-detail.component.ts 

  ```typescript
  import { Hero } from '../hero';
  import { Component, OnInit, Input } from '@angular/core';

  export class HeroDetailComponent implements OnInit {
    @Input() hero?: Hero;
  }
  ```

# Show the HeroDetailComponent

HeroesComponent 元件 與 hero details 元件具有父/子關係, 因此須從父級元件傳送資料給子級元件, 將原先的heroes.component.html: div 下的 detail 內容刪除, 替換為下者

```html
<app-hero-detail [hero]="selectedHero"></app-hero-detail>
```


