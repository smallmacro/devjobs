# Frontend Mentor - Devjobs web app solution

This is a solution to the [Devjobs web app challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/devjobs-web-app-HuvC_LP4l). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)
- [Acknowledgments](#acknowledgments)

## Overview

### The challenge

Users should be able to:

- View the optimal layout for each page depending on their device's screen size
- See hover states for all interactive elements throughout the site
- Be able to filter jobs on the index page by title, location, and whether a job is for a full-time position
- Be able to click a job from the index page so that they can read more information and apply for the job
- **Bonus**: Have the correct color scheme chosen for them based on their computer preferences. _Hint_: Research `prefers-color-scheme` in CSS.

### Screenshot

![mobile](./mobile.gif)
![tablet](./tablet.gif)
![desktop](./desktop.gif)

### Links

- Solution URL: [github url](https://github.com/smallmacro/smallmacro.github.io/tree/main/challenge6)
- Live Site URL: [Devjobs](https://devjobs.fly.dev/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Mobile-first workflow
- [React](https://reactjs.org/) - JS library
- [Vite](https://vitejs.dev/) - React Tooling
- [React Router](https://reactrouter.com/en/main) - React Router
- [Tailwind Css](https://tailwindcss.com/) - For styling component
- Express
- React Query

### What I learned

1. Flexbox or Grid: When aligning items along the main axis, auto margins are the way to go.
2. In tailwind-css `prefers-color-scheme` can be automatically triggered by setting the classname `dark:` or triggered by manually.`window.matchMedia('(prefers-color-scheme: dark)').matches` is true in Chrome while is false in Firefox.

   ```javascript
   const [checked, setChecked] = useState(false);
   useEffect(() => {
     if (
       checked ||
       localStorage.theme === "dark" ||
       (!("theme" in localStorage) &&
         window.matchMedia("(prefers-color-scheme: dark)").matches)
     ) {
       document.documentElement.classList.add("dark");
     } else {
       document.documentElement.classList.remove("dark");
     }

     return () => {};
   }, [localStorage, checked]);
   ```

3. React Router enable to define the `loader` function to load data before loading the component
4. Stop Propagation from children elemement to parent element by using `event.stopPropagation()`
5. Setting Dynamic color tailwind css, such as `bg-[${themeColor}]` , is not working as it against the constraint of Tailwind css. The solution is to set inline-style within the element.
6. [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) is a great tools for testing backend api functions. Can't figure out how to post a Array data .
7. `nodemon` will watch the files in the directory in which nodemon was started, and if any files change, nodemon will automatically restart your node application.
8. Deleting remote branches.To delete a remote branch, you can’t use the git branch command. Instead, use the git push command with --delete flag, followed by the name of the branch you want to delete. You also need to specify the remote name (origin in this case) after git push.

```
git push origin --delete test
```

9. deploy to fly.io. `fly launch` `fly deploy`
10. Github Pages does not support dynamic route.
11. React router loader function only suggest a timing to preload the data needed to render components, but it does not serve as a cache.
12. Streaming deploying of the frontend

```json
{
  "scripts": {
    // ...
    "build:ui": "rm -rf dist && cd ../frontend && npm run build && cp -r dist/ ../server",
    "dev": "nodemon index.js",
    "deploy": "fly deploy",
    "deploy:full": "npm run build:ui && npm run deploy"
  }
}
```

13. redirect the `Express` get requests to `/dist/index.html` to prevent the `can not get /jobs/:id error` when refreshing the path.

14. In Test-Driven Development, we write the test function bedore the actual implementation of functions.

15. `Mongoose` do the similar join operation like relational database by usinbg `populate`.The functionality of the `populate` method of Mongoose is based on the fact that we have defined "types" to the references in the Mongoose schema with the ref option:

```javascript
const users = await User.find({}).populate("jobs", { comapny: 1, postion: 1 });
//{company: 1,postion:1} means choosing the fields we want to include, like the Mongo syntax

response.json(users);
```

16. Problems of Token-based authentication

- If a token without limited time, the server cannot revoke the access right of token holder
- If a token with limited time, the shorter the expiration time, the more safe the solution is, but the user must login to the system more frequently
  - (server side session,regular database is complicated and slower)save the info about each token to backend database and check each API request if the access right corresponding to the token is still valid.
  - (key-value database such as Redis) save the session corresponding to a token to a key-value-database.
  - token is quite often just a random string, not including any information about the user.
  - For each API request, the server fectched the relevant information about the identity of the user from the database.
  - Instead of using authorization-header, cookies are used for transfering the token between the client and th server.
  - Usernames, passwords and applications using token authentication must always be used over HTTPS.

### Continued development

- ~~Load json data from backend~~
- ~~configure the base url in react router.~~
- ~~search and filter the jobs~~
- ~~deploy it with a docker.~~(Automatically done while delpoy to flyio)
- Use `React Query` ~~in the loader function~~ as a cache.(done)
- ~~Extract communicaiton with the backend into a seperate module~~
- ~~deploy the whole app to fly.io~~
- ~~connect the backend to Database(mongoDb)~~
- ~~Implement the CRUD operations in the backend.~~
- ~~Fix the `jobs/:id` path;~~
- ~~Use `mongoose` as mongodb modeling,validation for node.js~~
- ~~Add Unit test for job related api function.~~
- ~~Add User model~~
- Add utils functions.(User can register,login, reset password, update profile, email verificaiton)
- Add role authentication and authorization
- Session and Cache managment.
- `Load More` or pagination

### Useful resources

- [React - Prevent Event Trigger on Parent From Child](https://stackoverflow.com/questions/37568550/react-prevent-event-trigger-on-parent-from-child)
- [Toggling dark mode manually](https://v2.tailwindcss.com/docs/dark-mode)
- [fullstack open course](https://fullstackopen.com/en/)
- [Pagination vs. Infinite Scroll vs. Load More Explained](https://crocoblock.com/blog/pagination-vs-infinite-scroll/)
- [Node.js User Authentication Guide](https://blog.loginradius.com/engineering/guest-post/nodejs-authentication-guide/)

## Author

## Acknowledgments
