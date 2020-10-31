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

## The CSS

Now hop on to `stlye.css` file. Let's add some universal styles and styles for our game board. As mentioned before we are going to use images of 100 x 100 px, set the board width to `300px` and height to `400px` for 3 x 4 card board. Add the styles below to your project.

```css
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: -apple-system, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
body{
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  }
.board {
  display: flex;
  flex-wrap: wrap;
  width: 400px;
  height: 300px;
}
```

Check your output.

![CSS output](https://cloud-mv8zkaxw2.vercel.app/0screenshot_2020-10-31_133838.png)

We completed the markup and styling of our project. Now flip over to `script.js` and let's start creating the game.

## The JavaScript

Create a DOM [event-listener](https://developer.mozilla.org/en-US/docs/Web/API/EventListener) for the event [DOMContentLoaded](https://developer.mozilla.org/en-US/docs/Web/API/Document/DOMContentLoaded_event). All our JavaScript code will be inside the event-listener, which will be excuted after the content loaded.

```javascript
document.addEventListener('DOMContentLoaded', () => {
  // code goes here!
  })
```

Inside the event-listener, create an array for the cards which we use for the game. Add two of each cards for matching the cards. The public links for the images are provided in the code below. If you downloaded the images or using your own images, then add the relative path to the images.

```javascript
document.addEventListener('DOMContentLoaded', () => {
  const cardArray = [
    {
      name: '1',
      img:"https://cloud-5ystxzer7.vercel.app/11.png"
    },
    {
      name: '2',
      img:"https://cloud-5ystxzer7.vercel.app/22.png"
    },
    {
      name: '3',
      img:"https://cloud-5ystxzer7.vercel.app/33.png"
    },
    {
      name: '4',
      img:"https://cloud-5ystxzer7.vercel.app/44.png"
    },
    {
      name: '5',
      img:"https://cloud-5ystxzer7.vercel.app/55.png"
    },
    {
      name: '6',
      img:"https://cloud-5ystxzer7.vercel.app/06.png"
    },
    {
      name: '1',
      img:"https://cloud-5ystxzer7.vercel.app/11.png"
    },
    {
      name: '2',
      img:"https://cloud-5ystxzer7.vercel.app/22.png"
    },
    {
      name: '3',
      img:"https://cloud-5ystxzer7.vercel.app/33.png"
    },
    {
      name: '4',
      img:"https://cloud-5ystxzer7.vercel.app/44.png"
    },
    {
      name: '5',
      img:"https://cloud-5ystxzer7.vercel.app/55.png"
    },
    {
      name: '6',
      img:"https://cloud-5ystxzer7.vercel.app/06.png"
    }
  ]
})
```

Now we are going to creating our game board.

## Game Board

Pick up the `div` element with `class = "board"` using [querySelector](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector) and define it as `board`. Create a function `createBoard()` and loop over through elements in `cardArray` using `for` loop and add cards to our game board.

Create a constant for our placeholder image. We are going to use it many times.

```javascript
const placeholder = "https://cloud-5ystxzer7.vercel.app/7placeholder.png"
```

Create a `img` element using `document.createElement` for the every card. Using `setAttribute()`, add `src` and `data-id` attributes to the image. Let's first set the `src` attribute to the placeholder image (i.e, let's assume the placeholder image as reversed card). The link to the placeholder image is given in the code, otherwise add the relative path to the image.

![place holder image](https://cloud-5ystxzer7.vercel.app/7placeholder.png)

Here, [createElement( )](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement) creates the HTML element specified by tagName, [setAttribute( )](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute) sets the value of an attribute on the specified element and [data attribute](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes) allow us to store extra information on standard in the HTML tag. According to the game, we have to flip the card that is clicked. So add a `click` event-listener for the card. Every time a card get clicked, `flipCard` function will be excuted, which we will define later on the flow. Then add the `card` into the `board` using `appendChild()`. The method [appenChild( )](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild) adds a node to the end of the list of children of a specified parent node.

```javascript
const board = document.querySelector('.board')
const placeholder = "https://cloud-5ystxzer7.vercel.app/7placeholder.png"

// create game board
function createBoard() {
  for (let i = 0; i < cardArray.length; i++) {
    var card = document.createElement('img')
    card.setAttribute('src', placeholder)
    card.setAttribute('data-id', i)
    //card.addEventListener('click', flipCard)
    board.appendChild(card)
  }
}
createBoard()
```

For now, comment the event-listener as `flipCard` haven't yet defined and invoke the `createBoard()` function. Press the run button and see the your game board. It looks like this with all the cards turned down (i.e., placeholder images).

![Temporary output](https://cloud-2vppbtbp1.vercel.app/0jsop.png)

## Flip Card

When a card is clicked, let's flip the card. Create two empty variable arrays `cardsClicked` and `cardsClickedId`. Create a function `flipCard()`. Then inside this function, create a variable `cardId`, which is the `data-id` attribute of the clicked card, using `getAttribute()`. Now add name of this card into `cardsClicked` array based on `cardId` using `push()` method. Also push the id of this card (i.e., `cardId`) into `cardsClickedId` array. Then add the front side of the card, image in `cardArray` corrresponding to `cardId`, using `setAttribute`.After selecting two cards, we have to execute the function `checkForMatch()`. For that, if the length of `cardsClicked` array is equal to `2`, add invoke `checkForMatch()` inside `setTimeout()` so that everything doesn't happen too fast. 

Here, [getAttribute( )](https://developer.mozilla.org/en-US/docs/Web/API/Element/getAttribute) returns the value of a specified attribute on the element, [.push( ) method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) adds one or more elements to the end of an array and returns the new length of the array and [setTimeout( )](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout) sets a timer which executes a function or specified piece of code once the timer expires. 

```javascript
document.addEventListener('DOMContentLoaded', () => {
  const cardArray = [....]
  const board = document.querySelector('.board')
  const placeholder = "https://cloud-5ystxzer7.vercel.app/7placeholder.png"
  var cardsClicked = []
  var cardsClickedId = []

  //creating game board
    function createBoard() {
      for (let i = 0; i < cardArray.length; i++) {
        var card = document.createElement('img')
        card.setAttribute('src', placeholder)
        card.setAttribute('data-id', i)
        card.addEventListener('click', flipCard)
        board.appendChild(card)
      }
    }

  //flip  the card
    function flipCard() {
      var cardId = this.getAttribute('data-id')
      cardsClicked.push(cardArray[cardId].name)
      cardsClickedId.push(cardId)
      this.setAttribute('src', cardArray[cardId].img)
      if (cardsClicked.length ===2) {
        setTimeout(checkForMatch, 500)
      }
    }
  createBoard()
})
```

Don't forget to uncomment the event-listener of the card.
Comment the `if` statement and check weather the images are changing or not. The output works like this.

![Flip card](https://cloud-odqx6kfb8.vercel.app/0flipcard.gif)

Until now, we created a flippable game board.

![Wooo!!](https://cloud-bos4syje4.vercel.app/0woo__.gif)

Now that we have flipping cards, let’s handle the matching logic.

## Match Card

When we click the first card, it needs to wait until another card is flipped. So now, when the user clicks the second card. We will check to see if it’s a match. In order to do that, let’s create a function `checkForMatch()`. Inside the function, select all the images we created using `querySelectorAll()`. Also get the two elements in `cardsClickedId` array into two variables `firstCard` and `secondCard` respectively. If the two cards match you get +1 to your score. These cards then disappear. If you click the same card again, a pop up alert notifies you and the cards flip back. If the next card you flip does not match, the cards flip back. The game continues until you match all the cards on the board.

In place of the empty card, a blank image is displayed. Create a constant `blank` for the blank image.

```javascript
const blank = "https://cloud-5ystxzer7.vercel.app/6blank.png"
```

![blank](https://cloud-5ystxzer7.vercel.app/6blank.png)

Once we have a matched, the blank cards are still "clickable" and that's a flaw as far as user experience goes. 

![clickable](https://cloud-fmitdekvd.vercel.app/0removeevent.gif)

So we have to remove the "click" eventListener of the matched pairs.
```javascript
 cards[firstCard].removeEventListener("click", flipCard) 
 cards[secondcard].removeEventListener("click", flipCard)
 ```

Also create a variable `cardsMatched` array to push the matched cards. The length of `cardsMatched` array is your score. We have to add the live score into the `span` with `id = "score"` using `getElementById()` and `textContent`. After the logic executed, we have to clear both the `cardsClicked` and `cardsClickedId` arrays no matter what. 

```javascript
document.addEventListener('DOMContentLoaded', () => {
  const cardArray = [....]
  
  const board = document.querySelector('.board')
  const result = document.querySelector('#score')
  const placeholder = "https://cloud-5ystxzer7.vercel.app/7placeholder.png"
  const blank = "https://cloud-5ystxzer7.vercel.app/6blank.png"
  var cardsClicked = []
  var cardsClickedId = []
  var cardsMatched = []

  //creating game board
    function createBoard() {....}

  //flip  the card
    function flipCard() {....}

    //check for match
    function checkForMatch() {
      var cards = document.querySelectorAll('img')
      const firstCard = cardsClickedId[0]
      const secondCard = cardsClickedId[1]

      if(firstCard === secondCard) {
        cards[firstCard].setAttribute('src', placeholder)
        cards[secondCard].setAttribute('src', placeholder)
        alert('You have clicked the same image!')
      }
      else if (cardsClicked[0] === cardsClicked[1]) {
        cards[firstCard].setAttribute('src', blank)
        cards[secondCard].setAttribute('src', blank)
        cards[firstCard].removeEventListener('click', flipCard)
        cards[secondCard].removeEventListener('click', flipCard)
        cardsMatched.push(cardsClicked)
      } 
      else {
        cards[firstCard].setAttribute('src', placeholder)
        cards[secondCard].setAttribute('src', placeholder)
      }
      cardsClicked = []
      cardsClickedId = []
      result.textContent = cardsMatched.length
      if  (cardsMatched.length === cardArray.length/2) {
        result.textContent = 'Congratulations! You found them all!'
      }
  }

  createBoard()
})

```

One thing you might notice that the cards are not random. So we have to shuffle them using `sort()` method. The [sort( )](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) method sorts the elements of an array in place and returns the sorted array.

```javascript
cardArray.sort(() => 0.5 - Math.random())
```

Finally, we finished our memory game.

![Hooray!!!](https://cloud-4ddhwjoi2.vercel.app/0hooray.gif)

Check the final code [here](https://repl.it/@Giridharhackclu/Final-Memory-Game#script.js).

![final output](https://cloud-cz47beweb.vercel.app/0final-memory-game.gif)
