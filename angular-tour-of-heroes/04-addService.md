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

