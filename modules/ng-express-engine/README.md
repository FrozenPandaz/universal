# Angular Express Engine

This is an Express Engine for running Angular Apps on the server for server side rendering.

## Usage

To use it, set the engine and then route requests to it

```ts
import * as express from 'express';
import { ngExpressEngine } from '@universal/ng-express-engine';

// Set the engine
app.engine('html', ngExpressEngine({
  bootstrap: ServerAppModule // Give it a module to bootstrap
}));

app.set('view engine', 'html');

app.get('/**/*', (req: Request, res: Response) => {
  req: req,
  res: res
});
```

## Bootstrap

The engine also calls the ngOnBootstrap lifecycle hook of the module being bootstrapped

```ts
@NgModule({
  bootstrap: [AppModule]
})
export class ServerAppModule {
  // Make sure to define this an arrow function to keep the lexical scope
  ngOnBootstrap = () => {
      console.log('bootstrapped');
    }
}
```
