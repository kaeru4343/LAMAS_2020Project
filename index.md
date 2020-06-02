---
layout: default
---

```Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](./another-page.html).

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.


###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.


The final element.
```
# Introduction

Battleships is a strategy type guessing game for two players that originally came out as pen and paper game in the 1930s and, later, in 1973, as a plastic board game.

The game created a multitude of spin-offs in various formats, including electronic versions, video games and even phone apps. Every version generally respects the core idea of the game, but will sometimes deviate in execution or rules. For the sake of simplicity, we will be using the game's default rules and a abridged version of its components in our attempt to model the game in an epistemic logic system.

## Rules and Components

As stated before, this is a game for two players. Each player has a grid of 10x10 that only they can see, pegs to mark an opponent's hits and misses and a number of ships of varying lengths and witdh 1. Various versions of the game have a different numbers of ships, but the default version has: 1 Carrier, which has length 5, 1 Battleship, which has length 4, 1 Cruiser, which has length 3, 1 Submarine, which has length 3 and 1 Destroyer, which has length 2. For our abridged version, we will be using a 6x6 grid, 1 Battleship, 1 Cruiser and 1 Destroyer.

The game is played as follows: At the start, each party places down their ships without the knowledge of the oponent. They can place their ships whereever they want on their grid as long as the ships are either vertical or horizontal and they do not intersect other ships. Afterwards, the first round starts. During a round, the players each take a turn to attack a slot on the opponent's board. During an attack, they specify the coordinates they want to check, for example A5(first row, fifth collumn), and after this announcement, the opposing player has to announce if the attempt was a hit or a miss and mark it on their grid accordingly. Then the other player does the same. The round ends and the next round begins. If all of the slots that a ship spans are hit, then the ship is considered to have "sunk" and the player to whom that ship belonged must announce that that particular kind of ship has been sunk. The rounds keep repeating until the ships of either one of the players, or of both (as the round ends after both players have taken a shot, this is possiible), have been sunk. This concludes the rules the rules of the game.

### Epistemic Logic Conversion

#### Example of an Epistemic Logic Playthrough

##### Discussion





