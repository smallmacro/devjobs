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

**Note: Delete this note and update the table of contents based on what sections you keep.**

## Overview

### The challenge

Users should be able to:

- View the optimal layout for each page depending on their device's screen size
- See hover states for all interactive elements throughout the site
- Be able to filter jobs on the index page by title, location, and whether a job is for a full-time position
- Be able to click a job from the index page so that they can read more information and apply for the job
- **Bonus**: Have the correct color scheme chosen for them based on their computer preferences. _Hint_: Research `prefers-color-scheme` in CSS.

### Screenshot

![](./screenshot.jpg)

Add a screenshot of your solution. The easiest way to do this is to use Firefox to view your project, right-click the page and select "Take a Screenshot". You can choose either a full-height screenshot or a cropped one based on how long the page is. If it's very long, it might be best to crop it.

Alternatively, you can use a tool like [FireShot](https://getfireshot.com/) to take the screenshot. FireShot has a free option, so you don't need to purchase it.

Then crop/optimize/edit your image however you like, add it to your project, and update the file path in the image above.

**Note: Delete this note and the paragraphs above when you add your screenshot. If you prefer not to add a screenshot, feel free to remove this entire section.**

### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Add live site URL here](https://your-live-site-url.com)

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
- Axios

### What I learned

1. Flexbox or Grid: When aligning items along the main axis, auto margins are the way to go.
2. In tailwind-css `prefers-color-scheme` can be automatically triggered by setting the classname `dark:` or triggered by manually.

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
6. [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) is a great tools for testing backend api functions.
7. `nodemon` will watch the files in the directory in which nodemon was started, and if any files change, nodemon will automatically restart your node application.

### Continued development

- Load json data from backend
- search and filter the jobs
- connect the backend to Database(mongoDb)
- Add Unit test.
- deploy it with a docker.

### Useful resources

- [React - Prevent Event Trigger on Parent From Child](https://stackoverflow.com/questions/37568550/react-prevent-event-trigger-on-parent-from-child)
- [Toggling dark mode manually](https://v2.tailwindcss.com/docs/dark-mode)
-

## Author

## Acknowledgments
