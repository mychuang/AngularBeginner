# Create the HeroService

- generate service

  ```
  ng generate service hero
  ```

- Get hero data: hero.service.ts

  ```typescript
  import { Hero } from './hero';
  import { HEROES } from './mock-heroes';

  getHeroes(): Hero[] {
    return HEROES;
  }
  ```

# Use service in HeroesComponent
Update heroes.component.ts

  ```typescript
  // Delete the HEROES import
  import { HeroService } from '../hero.service';

  export class HeroesComponent implements OnInit {
    heroes: Hero[] = [];

    //Inject the HeroService
    constructor(private heroService: HeroService) { }


    //Create a method to retrieve the heroes from the service. 
    getHeroes(): void {
      this.heroes = this.heroService.getHeroes();
    }

    //Call it in ngOnInit()
    ngOnInit(): void {
      this.getHeroes();
    }
  }
  ```

# Observable data: 異步(非同步) 流程

Quick to see the pure javascript sample to undersatnd why need asynchronous.<p>

從伺服器抓取一張影像，以下程式碼是沒有辦法馬上獲得結果的

```javascript
let response = fetch('myImage.png'); // fetch is asynchronous
let blob = response.blob();
// display your image blob in the UI somehow
```
那是因為不知道下載影像需要花上多少時間，所以當執行第二行時它將拋出一段錯誤（也許間歇性的發生，也許每一次都發生）這是因為 response 尚未取得結果還不能使用。因此在它嘗試做接下來的任何事之前，你需要讓你的程式碼先等到 response 回傳結果。<p>
在 Javascript 有兩種主要類型的非同步程式碼風格，舊式的回呼風格（callback）以及新式的 promise 風格<p>

Angular Observables 類似 javascript 的 Promises, 卻更加強大, 以下圖微比較

<img src=001.png width=500px>

## Observable HeroService

- 加入 Observables: hero.service.ts

  ```typescript
  //Observable is one of the key classes in the RxJS library.
  import { Observable, of } from 'rxjs';

  //Replace the getHeroes() method with the following:
  getHeroes(): Observable<Hero[]> {
    const heroes = of(HEROES);
    return heroes;
  }
    // of(HEROES) returns an Observable<Hero[]> that emits a single value, the array of mock heroes.
  ```

- 訂閱 Observables: heroes.component.ts

  ```typescript
  /*
  getHeroes(): void {
    this.heroes = this.heroService.getHeroes();
  }
  */
  
  getHeroes(): void {
    this.heroService.getHeroes()
      .subscribe(heroes => this.heroes = heroes);
  }
  ```
