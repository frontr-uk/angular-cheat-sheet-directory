# angular cheat sheet directory
I always head issue with the current documentation so I created this is a list of references, ideas, architecture suggestion and code snippets. 

The content is linked to videos incase you need some visual explanation and mostly reference to naming 'Bananas' as based on the channel name. Feel free to contribute.


**1. Computer Setup**

| Command  | Description |
| ------------- | ------------- |
| npm install -g @angular/cli  | Install Angular CLI globally |

**2. Architecture and Structure**

```
App
-projects
--Custom Features
-src
--app
--app.route.ts
--app.module.ts
--assets
--eviorments
package.json
tsconfig.json
tslint.json
```

| **Related videos** | 
| ------------- |
|[Angular Architecture video](https://www.youtube.com/watch?v=Zq4vrEPbnj8&t=1223s)|
|[Dumb vs Smart Components structure](https://www.youtube.com/watch?v=Zq4vrEPbnj8)|
|[How to create project libs](https://www.youtube.com/watch?v=wMZ1QYlNHvM)|

**4. Creating a new application**

| Command  | Description |
| ------------- | ------------- |
| ng new bananas --dry-run  | simulate ng new  |
| ng new bananas --skip-install  | create app without installing node_modules  |
| ng new bananas --prefix ban  | set prefix to `ban`  |
| ng new --help	| Available command list  |


| **Related videos** | 
| ------------- |
|[React vs Angular Setup](https://www.youtube.com/watch?v=4S0DLZKNDAk)|




**5. Components vs Directives**
Component Basic structure

```ts
import { Component } from '@angular/core';

@Component({
	selector: 'app-root',
	templateUrl: './app.component.html',
	styleUrls: ['./app.component.less']
})

export class AppComponent {
	title = 'Bananas';
    hero = {
        name: 'Chris',
        imageUrl: `https://yt3.ggpht.com/-pAxGtnKc69U/AAAAAAAAAAI/AAAAAAAAAAA/Rl5zaJUa6QE/s108-c-k-no-mo-rj-c0xffffff/photo.jpg`,

    }
    doSomething(){
        console.log('You clicked')
    }
}
```

## How to bind data to HTML
***Interpolation*** 

Render from Hero object the name property 

`{{hero.name}}`

---
***Property binding***

Bind image url for user to src attribute

`<img [src] = "hero.imageUrl">`

---
***Event*** 

Assign function to click event

`<button (click)="doSomething()" ... />`


Show button when user.showSth is true  
<button *ngIf="user.showSth" ... />

---
***Looping through items***

Iterate through heors list 

`*ngFor="let item of heros"`

---
Dynamic class based on a condition

`<div [ngClass]="{ active: isTrue() }"/> `

---
Dynamic inline css

`<div [ngStyle]="{'color': isTrue() ? '#000' : '#dedede'}"/>`

----------------
Dynamic class assignment via host

```ts
export class Component implements OnInit {
    @HostBinding('class.active')
    public AddstyleAsActive: boolean = false;
}
```


| **Related videos** | 
| ------------- |
|[Binding data](https://www.youtube.com/watch?v=d6RX-iQVorQ&t=441s)|
|[Dumb vs Smart Components structure](https://www.youtube.com/watch?v=Zq4vrEPbnj8)|
|[Components vs Directives](https://www.youtube.com/watch?v=r2PdotX3bkw&t=9s)|



## Component life cycles

| Life cycle  | Description |
| ------------- | ------------- |
| ngOnChanges  | Called before ngOnInit() and whenever one or more data-bound input properties change.  |
| ngOnInit  | Called once, after the first ngOnChanges()   |
| ngDoCheck  | Called during every change detection run  |
| ngAfterContentInit  | Called once after the first ngDoCheck().  |
| ngAfterContentChecked  | Called after the ngAfterContentInit() and every subsequent ngDoCheck()  |
| ngAfterViewInit  | Called once after the first ngAfterContentChecked().   |
| ngAfterViewChecked  | Called after the ngAfterViewInit() and every subsequent ngAfterContentChecked().|
| ngOnDestroy  | Called just before Angular destroys the directive/component  |

[Angular website for lifecycles](https://angular.io/guide/lifecycle-hooks)

**6. Services**

| **Related videos** | 
| ------------- |
|[Creating services in angular](https://www.youtube.com/watch?v=Z5Q_IQMNrPg&t=616s)|


**7. Lint**

| Command  | Description |
| ------------- | ------------- |
| ng lint bananas  | Display in terminal the lint errors  |
| ng lint bananas --format stylish  | format code  |
| ng lint bananas --help  | Available command list  |
| ng lint bananas --fix   | fix code errors based on your lint config  |


