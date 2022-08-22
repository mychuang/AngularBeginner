# Angular tutorial Note
This tutorial will follow https://angular.io/tutorial 

- [Intro](./Intro.md)

- 創建 Anguar 專案

  ```shell
  ng new angular-tour-of-heroes
  cd angular-tour-of-heroes 
  ng serve --open
  ```

  Check src/app forder as the following:

  - app.component.ts: The component class code.

    ```typescript
    title = 'Tour of Heroes';
    ```

  - app.component.html: The component template.

    ```html
    <h1>{{title}}</h1>
    ```

  - app.component.css: The component's private CSS styles.

    ```css
    h1 {
        color: #369;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 250%;
    }
    
    h2, h3 {
        color: #444;
        font-family: Arial, Helvetica, sans-serif;
        font-weight: lighter;
    }
    body {
        margin: 2em;
    }
    body, input[type="text"], button {
        color: #333;
        font-family: Cambria, Georgia, serif;
    }
    button {
        background-color: #eee;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        color: black;
        font-size: 1.2rem;
        padding: 1rem;
        margin-right: 1rem;
        margin-bottom: 1rem;
        margin-top: 1rem;
    }
    button:hover {
        background-color: black;
        color: white;
    }
    button:disabled {
        background-color: #eee;
        color: #aaa;
        cursor: auto;
    }

    * {
        font-family: Arial, Helvetica, sans-serif;
    }
    ```

- [初探 Angular 專案 與 data binding](./angular-tour-of-heroes/01-hero_editor.md)

- [顯示列表](./angular-tour-of-heroes/02-DisplayList.md): *ngFor & ngIf

- [組件間傳值: @Input](./angular-tour-of-heroes/03-featureComponent.md)