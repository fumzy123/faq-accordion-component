# Frontend Mentor - FAQ accordion solution

This is a solution to the [FAQ accordion challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/faq-accordion-wyfFdeBwBz). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The Goal](#the-goal)
  - [Screenshot](#screenshot)
  - [Links](#links-to-project-solution)

- [My process](#my-process)

- [Problems I encountered](#problems-i-encountered)
- [What I learned](#what-i-learned)
- [Useful resources](#useful-resources)
- [Feedback from Mentors](#feedback-from-mentors)
- [Areas of Continued Development](#continued-development)
- [Built with the following tools](#built-with)
- [Acknowledgments](#acknowledgments)
- [Author](#author)


## Overview

### The Goal

Users should be able to:

- Hide/Show the answer to a question when the question is clicked
- Navigate the questions and hide/show answers using keyboard navigation alone
- View the optimal layout for the interface depending on their device's screen size
- See hover and focus states for all interactive elements on the page

### Screenshots


### Links to Project Solution

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Add live site URL here](https://your-live-site-url.com)






## My process

### Understanding the HTML Structure
1. I start with the Mobile View:
  - What I am seeing is an h1 tag and an image in a flexbox. Flexbox has some margin to add space between the flexbox and the list.

  - The list is a list of div elements that are flexboxes because they have an image with the text. 
  
  - How do I make them an accordion thou. How do I add an extra div that only gets revealed when the image is clicked.

2. I am currently working on the Background Image:
  a. How do I make the Image the entire width of the browser window ? I simply set the width of the image to be 100%. This way it takes the full width of the image container that it is in.

  b. How do I make the FAQ container float in front of the image and background ? I need the faq's container out of the html document flow. I want it to float in front of the background image container.

  There are two ways that I am thinking of achieving this
  - Find a way to set the background of the body to both color and image pattern. Then use a flexbox to center the FAQs container in the middle of the page.

  - Use Absolute positioning to place the FAQs container in the middle of the page.



## Problems I encountered
1. Placing the image pattern: I found it difficult to place the image pattern in a way that is responsive because I did not understand the fundamentals of how images worked on the web browser. I discovered that images do not automatically fit their container when you put them in one. You need to tell them to by using the `max-width` property.

```html
<div class="pattern__wrapper">
      <img class="" src="./assets/images/background-pattern-mobile.svg" alt="mobile-background-pattern"/>
</div>
```

To achieve the final mobile design. I decided to use `background-image` property from CSS.
```css
    background-image: url('../../assets/images/background-pattern-mobile.svg');
    background-size: cover;
    background-repeat: no-repeat;
```
The real magic however was using the `background-size` property. This tells CSS how to fit the image inside the background. The cover scales the image
while maintaining its aspect ratio, and so some parts where cropped out.

2. Placing the FAQs container in front of the pattern: For some reason I had a hard time implementing this one. I knew it had something to do with `position` property but I defaulted to using the _absolute_ value when relative was a better choice here. The _relative_ `position` value positions the HTML element relative to itself while preserving its space in the DOM / document flow. So other elements still respect its presence. I set the position to relative and moved the element up a little.

```css
.faqs {
    /** Background **/
    background-color: white;

    /** Box Model **/
    border-radius: 15px;
    padding: 1.5rem 1.5rem;

    /** Position **/
    /* position: absolute;
    top: 60%;
    left: 50%;
    transform: translate(-50%, -50%); */
    position: relative;
    top: -40px;

}
```

3. Adding Margins to the faqs question section beyond the xs view: I typically add in a container utility class directly on my sections but for this project i ran into a situation where I needed to add in a small left and right margin for my `faqs` section when the screen was below the 475px. Unfortunately I couldn't achieve this because I my container utility class was directly on my  section and it was overwriting the margins set in just created in the `faqs.css` class. Two separate classes controlling the same CSS property on the same element is not a good thing. One will overrite. The latest one of course.
```css
/* MOBILE FIRST CONTAINER UTILITY CLASS 
    This utility class wraps each section of our website to provide alignment and 
    responsiveness.
*/
.container {
    /** Box Model for all sections **/
    width: 100%;
    margin-inline: auto;
    border: 2px solid red;
}
```

How do I know this because of the order of my stylesheets. 
```css
/**
    All the Stylesheets will be imported into this one file.
    This file will then be linked in the html document.
**/
@import url('./modern-normalize.css');
@import url('./global.css');
@import url('./components/faqs.css');
@import url('./components/pattern.css');
@import url('./utils.css');

```

I solved this problem by moving the styling class for my container, `faqs_container` and my utility class `container` unto a `div` element that wraps the contents of my `faqs`. This way I can now add a margin to the class on my section. This was super helpful. Perhaps it is not always a good idea to place your container utility class on your section element. What if you want to control the same property. It might be more useful to wrap the contents of your section with the container utility and not the entire section.


## What I learned
1. `list-style`: This is a CSS shorthand property that allows you to set all the list style properties at once. list-style-image | list-style-position | list-style-type.
2. `border-top`: This is a CSS shorthand property that allows you to set the. `border-width` | `border-style`, and | `border-color` for the top border. e.g.

```css
border-top: 2px solid red;
```
3. The difference between event.target and event.currentTarget. Event.target refers to the element that fired the event. Whereas event.currentTarget refers to the element that has the event listener attached to it.

## Useful resources

- [Example resource 1](https://www.example.com) - This helped me for XYZ reason. I really liked this pattern and will use it going forward.
- [Example resource 2](https://www.example.com) - This is an amazing article which helped me finally understand XYZ. I'd recommend it to anyone still learning this concept.


## Feedback from Mentors

## Areas of Continued development

## Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Mobile-first workflow
- [React](https://reactjs.org/) - JS library
- [Next.js](https://nextjs.org/) - React framework
- [Styled Components](https://styled-components.com/) - For styles

## Acknowledgments

This is where you can give a hat tip to anyone who helped you out on this project. Perhaps you worked in a team or got some inspiration from someone else's solution. This is the perfect place to give them some credit.

**Note: Delete this note and edit this section's content as necessary. If you completed this challenge by yourself, feel free to delete this section entirely.**


## Author

- Website - [Add your name here](https://www.your-site.com)
- Frontend Mentor - [@yourusername](https://www.frontendmentor.io/profile/yourusername)
- Twitter - [@yourusername](https://www.twitter.com/yourusername)

**Note: Delete this note and add/remove/edit lines above based on what links you'd like to share.**