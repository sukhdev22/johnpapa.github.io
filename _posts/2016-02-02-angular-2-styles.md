---
layout: post
title: Angular 2 Styles and File Structure
date: 2015-11-19 01:11
author: John
comments: true
categories: [angular, angular2, javascript, Uncategorized]
---
> When are you publishing the Angular 2 Style Guide, John?

Soon. Before ngConf is my goal. What will be there by then? I am careful to only release conventions that I feel are vetted and have worked based upon experience. So the underlying problem with releasing an entire style guide right now is that there is not a lot of experience to lean on for many things. But there is enough traction now where we can safely say the foundations can be agreed upon and published. So when I do make the style guide publicly available, it will contain those foundations.

Until then, here is a quick glimpse at a project structure that I have been working with. I've had input that has impacted this from Ward Bell, Dan Wahlin, Igor Minar, Jules Kremer, and others from the Angular team and Angular GDEs.

### Example File Structure and Naming of Components/Services

```
  index.html                      // Starting page
  app/                            // Main app folder
    main.ts                       // bootstrap here
    app.component.css
    app.component.html
    app.component.ts              // Root component for the app (e.g. AppComponent)
    heroes/                       // Feature folder
      heroes.ts                   // Barrel module for the feature
      heroes.component.ts         // Router component (e.g. HeroesComponent)
      hero-list.component.css
      hero-list.component.html
      hero-list.component.ts      // list of heroes (e.g. HeroListComponent)
      hero-detail.component.css
      hero-detail.component.html
      hero-detail.component.ts    // hero details  (e.g. HeroDetailComponent)
      hero.service.ts             // A feature specific service  (e.g. HeroService)
    shared/                       // Shared features across the app
      shared.ts                   // Barrel module for shared features
      logger.service.ts           // Example shared service (e.g. LoggerService)
      spinner.component.ts        // Example shared component  (e.g. SpinnerComponent)
      config.ts                   // Shared configuration
```

Note that the names `list` and `detail` are arbitrary descriptive names for these components. There is no rule that says you have to use those. The convention is to pick a convention on how to name a list of things component such as HeroesListComponent, HeroListComponent, HeroSearchComponent and be consistent. Same with `Details`. It could be HeroDetailComponent, HeroEditorComponent, or anything that is decriptive and consistent in our app.

### Barrel
A barrel is a module whose purpose in life is to aggregate other modules and export them. Why? Because this reduces the number of import statements you need to use the modules. To put it another way, if the Angular 2 team did not use barrels, you might have 100 import statements everywhere :) Thankfully, they use barrels such as `angular2/core`. In the example above, barrels are used to aggregate the heroes feature.

### Want More?
Want more? I'll be blogging more with these ideas til the guide is released.

I'm also working on a Pluralsight course titled `Angular 2 First Look` due out in early March.
