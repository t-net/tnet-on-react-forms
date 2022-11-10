# React Forms and Testing

This project is an example solution for handling form state and queries or mutations in React. This code definitely does not aim for perfection. Neither does it aim to manoeuvre itself into a "Design Patterns" textbook that you tried to digest during tertiary education. Rather it aims to spike curiosity around user-value driven testing and ideally convince you to do the same in your next project.

Within the Volkswagen group, we are often required to use one of two UX systems namely GroupUI and Design 6. These dependencies make use of the shadow dom which causes some unexpected unmet expectations during testing. To put more plainly, it means that doing `input.type` in your test doesn't cause anything to be typed in the input.

I would like to invite you into the deep waters of JavaScript, lean programming, test driven development and the ever evolving world of frontend. Get in touch if you have any suggestions on the code. I love a good React state management discussion!

## Part 1: Scraping the Icing Off

Start with a bootstrapped project from [Create React App](https://github.com/facebook/create-react-app).

`npx create-react-app my-app --template typescript`

Eject if you prefer having full control over your bundler and compiler. If the name webpack already gives you the creeps, better skip this step. Read more about [eject](https://create-react-app.dev/docs/available-scripts#npm-run-eject).

`npm run eject`

Configure your compiler, linting and testing configurations according to your preference. By default, the configurations will be located in your package.json after ejecting. I prefer configuring jest, eslint, webpack and babel in the separate config files. I add these files separately and remove the react-scripts config and scripts files.

### Running Localhost

Run the app in the development mode at [http://localhost:3000](http://localhost:3000) to check it out:

`npm start`

### Testing

Runs all the jest tests:

`npm test`

When it comes to testing, I agree with [Kent C. Dodds](https://twitter.com/kentcdodds/status/977018512689455106): 
```
The more your tests resemble the way your software is used, the more confidence they can give you.
```

And so I use [React Testing Library](https://testing-library.com/) to test each page for the value that it brings to the user. This encourages accessibility and allows you to refactor the code without breaking the tests. Your tests get to do what they were meant to do originally, give you confidence that things work that way it will in the real world and without it being tied down to the implementation details. Read more about the [guiding principles](https://testing-library.com/docs/guiding-principles).

## Part 2: Routing 

Add `react-router-dom` and set up the routes and layout components.

- `app(.test).tsx`: The top level app is responsible to test whether the different routes render the expected pages as well as testing whether layout contexts are propagating to the pages (context consumers). Since each page is responsible for testing itself, the pages are mocked here.
- `pages/**/index(.test).tsx`: Each page tests all the expected functionality and use cases for that page. Only test the expected functionality and expected text that the user should see. It is not needed to test styling details or order of components unless those details carry a lot of weight towards the user value.
- `test/utils.tsx`: Helper function that wraps the rendered element in a memory router.


