---
name: 'Memory Game'
description: 'Create your own memory game using JavaScript'
author: '@giridhar7632'
---

# Memory Game

Memory Game, also known as Matching Game, is a simple card game where you need to match pairs by turn over 2 cards at a time. In this workshops we are going to build a simple memory game using JavaScript. Take a peek at the final project and the code.

![Final Project](https://cloud-lrj071vrh.vercel.app/0memory_game.gif)

[Live Demo](https://memory-game.giridharhackclu.repl.co/) and [Source Code](https://repl.it/@Giridharhackclu/Memory-Game#index.html).

## How to play...

Memory Game has long been a favorite game for all generations. It is easy to play, in fact it is so simple that really young children can play with ease.
It requires observation, concentration and a good memory to win.

### Rules

* You will start by flipping over one card
* If the next card you flip matches, you get +1 to your score
* These cards then disappear
* If the next card you flip does not match, the cards flip back
* The game continues until you match all the cards on the board

## Prerequisites

![prerequisites](https://cloud-h9glprsfs.vercel.app/0prerequisites.png)
Basic knowledge of HTML5, CSS3, and JavaScrip. We are going to use some of the in-built functions of JavaScript. Also the styling will be as simple as possible.

## Setup

[Repl.it](https://repl.it) is an online code editor. There is no need to install anything which makes coding simpler.

Create a new [HTML,CSS,JS](https://repl.it/languages/html) project or you can just fork this repl [here](https://repl.it/@Giridharhackclu/Memory-game-starter#index.html). Your development environment will be ready in few seconds!

![Repl](https://cloud-oyhes1lns.vercel.app/0memory-game-starter.png)

It contains an empty `index.html` file linked with `style.css` and `script.js` files.

We will create a simple 3x4 card game in this workshop. We use images for the cards. I will provide the public links for the images along the code. If you prefer to download, you can download them [here](https://drive.google.com/drive/folders/128S-rB27-86ciSyJvjkfK2NhJeoOmsB3?usp=sharing). You can also add your own images. Make sure they are 100 x 100 px to avoid further styling.

After setting up let's get going.

## The HTML

Let's create the markup of our game. Change the title and create a heading. Now put a `p` tag of Score with a `span` of `id = "score"` for displaying the live score. Create a `div` element with `class = "board"`. We will create the game board using JavaScript. Your final `index.html` will look something like this.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>Memory Game</title>
    <link href="style.css" rel="stylesheet" type="text/css" />
  </head>
  <body>
    <h1> ~ Memory Game ~ </h1>
    <p>Score:<span id="score"></span></p>
    <div class="board">
    </div>
    <script src="script.js"></script>
  </body>
</html>
```

Click the Run button to check your output, whether all the tags are working.

![HTML output](https://cloud-6a90k3fzb.vercel.app/0htmlop.png)

## Styling

Now hop on to `stlye.css` file. Let's add some universal styles and styles for our game board. As mentioned before we are going to use images of 100 x 100 px, 
