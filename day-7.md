# Day 6: COMPONENT - PASS DATA FROM PARENT TO CHILD WITH INPUT BINDING

We have generated a new component in a previous [6th tutorial](day-1.md). Let's add it to our main application.      

We need only selector name which is inside `bar.component.ts`:
```typescript
import { Component, OnInit } from '@angular/core';

@Component({
    selector: 'challengular-bar',
    templateUrl: './bar.component.html',
    styleUrls: ['./bar.component.scss'],
})
export class BarComponent implements OnInit {
constructor() {}

ngOnInit(): void {}
}
```

Adding **ClientModule** to `app.module.ts ` to have a possibility reading components from **Client library**:   
```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';
import { NxWelcomeComponent } from './nx-welcome.component';
import {FormsModule} from "@angular/forms";
import {ClientModule} from "@challengular/client";

@NgModule({
    declarations: [AppComponent, NxWelcomeComponent],
    imports: [
        BrowserModule,
        FormsModule,
        ClientModule //<---- here
    ],
    providers: [],
    bootstrap: [AppComponent],
})
export class AppModule {}
```

Add **Bar selector** to `app.component.html`
```html
<challengular-bar></challengular-bar>
```

You should get a new string in your application **bar works!** if everything was set up correctly.

## CONSTRUCTOR() VS NGONINIT()
- **Constructor** is the constructor of a class, it is a special function that when you instantiate an instance of the class, it will be automatically run, and only run once.    
- **ngOninit** is a life-cycle method that will be automatically called by Angular when the component is initialized, after the constructor runs, and after the inputs have been bound.   
> So if you bind to a property in the parent component's template, your child component's constructor won't get the value you've bound, but in ngOnInit you will be able to.      

>In fact, **Angular** recommends limiting the code to the constructor, the constructor does as few tasks as possible, let ngOnInit take care of the rest.

✅ Awesome! You have learned about **generating Angular components** and 7th tutorial is done!   
👋 See you in the 8th one.

## SOURCES
- [Angular Component Interaction[Angular Official page]](https://angular.io/guide/component-interaction)
- [Angular Lifecycle Hooks[Angular Official page]](https://angular.io/guide/lifecycle-hooks)

## HASHTAGS
`angular` `nx` `nx workspace` `frontend` `challenge` `guide` `tutorial`

# AUTHOR
`Serhii Nahornyi`