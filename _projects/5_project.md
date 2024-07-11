---
layout: page
title: ePortfolio with Custom Spider Background
description: Creating a personalized ePortfolio using Jekyll and al-folio template, featuring an interactive spider web background
img:
importance: 5
category: fun
giscus_comments: false
---

## Project Overview

This project showcases the creation of my personal ePortfolio using the al-folio template in Jekyll, with a particular focus on the customization of an interactive spider web background. The goal was to create a unique and engaging online presence that reflects both my professional skills and creative interests.

## Key Features

1. **Jekyll-based Portfolio**: Leveraged the power of Jekyll static site generator for efficient content management.
2. **al-folio Template**: Utilized the al-folio template as a foundation, providing a clean and academic-oriented design.
3. **Custom Spider Web Background**: Implemented an interactive JavaScript animation to create a distinctive visual element.
4. **Responsive Design**: Ensured the portfolio and background animation are fully responsive across various devices.

## The Spider Web Background

The centerpiece of this project is the custom spider web background, created using JavaScript and HTML5 Canvas. This interactive element adds depth and interest to the portfolio, creating a unique user experience.

### Key Aspects of the Spider Web Animation:

- **Dynamic Point Generation**: Creates a set of points that move organically across the canvas.
- **Inter-point Connections**: Draws lines between points when they come within a certain distance of each other.
- **Edge Fading**: Implements a fading effect near the edges of the screen for a polished look.
- **Responsive Behavior**: Adapts to different screen sizes and resolutions.

Here's a simplified version of the core animation logic:

```javascript
function animate() {
  for (let i = 0; i < points.length; i++) {
    movePoint(points[i]);
  }
  drawPoints();
  requestAnimationFrame(animate);
}

function drawPoints() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  drawLines();
  for (let i = 0; i < points.length; i++) {
    const opacity = getOpacity(points[i].x, points[i].y);
    points[i].circle.pos.x = points[i].x;
    points[i].circle.pos.y = points[i].y;
    points[i].circle.draw(opacity);
  }
}
```

## Challenges and Learning

1. **Jekyll Learning Curve**: Familiarizing myself with Jekyll's structure and Liquid templating language.
2. **JavaScript Animation Optimization**: Ensuring smooth performance of the spider web animation across different devices.
3. **CSS Customization**: Adapting the al-folio template to incorporate the custom background seamlessly.

## Reflections

Creating this ePortfolio was both challenging and rewarding. The project allowed me to showcase my web development skills while also expressing my creativity through the custom animation. The spider web background, in particular, became a talking point and added a memorable aspect to my online presence.

## Future Improvements

- Implement color themes for the spider web animation
- Add interactive elements that respond to user input
- Optimize the animation further for improved performance on mobile devices

## References and Resources

1. [Jekyll Documentation](https://jekyllrb.com/docs/)
2. [al-folio Template](https://github.com/alshedivat/al-folio)
3. [HTML5 Canvas Tutorial](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial)
4. [JavaScript Animation Techniques](https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame)

This project exemplifies the intersection of technical skill and creative design, resulting in a unique and engaging online portfolio.
