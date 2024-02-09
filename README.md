# Angular Resize Event

## Important
Forked from: https://github.com/vdolek/angular-resize-event. The last original version is not supported by angular 17. 
We forked and merged a pull request which contains angular 17 support.

Thanks to: https://github.com/vdolek, https://github.com/dereekb, and all contributors.

---
## Description
Angular 17 directive for detecting changes of an element size.

It is as simple as:

```html
<div (resized)="onResized($event)"></div>
```

It internally uses browser native [`ResizeObserver`](https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserver). Therefore it is not supported in IE.

For Angular 11 you can use version 2.1.0 which internally uses uses `ResizeSensor` from [CSS Element Queries](https://github.com/marcj/css-element-queries) that is supported in IE.

## Playground

[StackBlitz playground](https://stackblitz.com/edit/angular-resize-event-playground?file=src/app/app.component.html)

## Using the library

Import the library in any Angular application by running:

```bash
$ npm i angular-resize-event@npm:@sonrisa-dev/angular-resize-event-sonfork
```

and then from your Angular `AppModule`:

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';

// Import the library module
import { AngularResizeEventModule } from 'angular-resize-event';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,

    // Specify AngularResizeEventModule library as an import
    AngularResizeEventModule
  ],
  providers: [],
  bootstrap: [ AppComponent ]
})
export class AppModule { }
```

Once your library is imported, you can use its `resized` directive in your Angular application:

```html
<div (resized)="onResized($event)"></div>
```

```typescript
import { Component } from '@angular/core';

// Import the resized event model
import { ResizedEvent } from 'angular-resize-event';

@Component({...})
class MyComponent {
  width: number;
  height: number;

  onResized(event: ResizedEvent) {
    this.width = event.newRect.width;
    this.height = event.newRect.height;
  }
}
```

## License

MIT © [Martin Volek](mailto:martin@vdolek.cz)
