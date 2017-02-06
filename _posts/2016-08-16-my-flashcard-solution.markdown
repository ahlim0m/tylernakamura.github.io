---
layout: post
title: "My Flashcard Solution - Anki"
date: 2016-08-16 15:03
comments: false
categories: flashcards anki flashcard memory memorization
---

Memory can be beneficial to any education or career.
Over the last few years, I have found flashcards use to be the most effective memory method.
Initially I used index cards to reinforce information, but I found that there were scaling issues when my physical deck exceeded 200 cards.

I then found an open source project that was a perfect solution for me: Anki.
Anki is digital flashcard software that enforces assists in remembering large amounts of data.
After digging and playing with the software, I have found that Anki provides a tremendous amount of robustness. You can learn more about Anki at [the official website/](https://apps.ankiweb.net/)

Here are some my favorite features of Anki:

### 1. Reinforce Difficult Cards
This is my favorite feature that Anki offers that I haven't been able to find with any other flashcard solutions.
As your deck continues to grow (100+ cards), it doesn't make sense to go through the entire deck every single study session.
It is a pretty big waste of time to go through cards that you know really well.
The power of flashcards comes from the fact that you can test yourself on the cards that you need the most help with.

Anki is designed to test you on the flashcards that you struggle with the most.
Depending on how well you know the card, Anki won't present you that flashcard until it's time for you to see it again.

For example, when I know a card really well, I can press the "easy" key and Anki will keep track of how easy the card has been for you in a database.
You can indicate how well you know the card with the following interface:

<img src="/images/anki-card-options.png"/>

If you continue to successfully recall the flashcard, Anki will increase the interval before it asks you to recall the flashcard again.
This is a scalable solution as your decks and knowledge continue to grow.
I have flashcards that aren't due for 2-3 years because I know them so well!

### 2. FOSS
Anki is completely open source and written in Python.
The project is licensed under the AGPL3.
The source code can be found here [github.com/dae/anki](https://github.com/dae/anki)

### 3. Nested Decks
Decks can be nested within one another.
This is awesome if you have a ton of decks that sometimes have overlapping cards.
This functionality allows users to create grand hierarchies.
Here is what my decks currently look like:

<img src="/images/nested-anki-decks.png"/>

You can see that I have a variety of topics that are important to me.
Nested decks allow me to keep everything organized and track my progress for each category.

### 4. Cloze Deletion

Cloze deletion makes it easy to create many flashcards from sample texts.
The cloze feature allows you to take a sample text and remove certain words or phrases from it and turn them into flashcards.
Creating these types of flashcards is extremely quick and enables you to pinpoint which parts of the text you want to truly memorize.
Take a look at the example from the [Anki documentation](http://ankisrs.net/docs/manual.html#cloze-deletion):

<img src="/images/2016-12-08-anki-cloze-example.PNG"/>

Note that in this example, there could be another flashcard where the word "Canberra" is blanked out and and 1913 is visible.

### 5. Charts and Stats
During your studies, all of your answers and decks are being tracked.
You can view your performance in a lot of different ways. Here are my current stats:

<img src="/images/anki-stats.png"/>

The statistics are far more robust than what I need, but it is neat to look at performance.

### 6. Media in Flashcards
Sometimes pictures or audio are neccesary for flashcards.
Depending on what topic you are studying, it might be useful to insert media in your flashcards.
With Anki, this can be done with both audio and picture media.
Here is what a picture flashcard could look like:

<img src="/images/anki-picture-card.png"/>

With the audio feature, you can memorize chord sounds, or foreign language word pronunciations.

### 7. Other Features

- Plugins
- Web syncing
- LaTex support
- Card templates

---

### Quizlet
There are other flashcard solutions available. [Quizlet](https://quizlet.com) is the probably the biggest competitor to Anki.
However, Quizlet isn't open source and doesn't have the same weak card reinforcing capabilities that Anki has.
I still use Quizlet as a search engine to find decks and just import them into my personal Anki decks.

---

Give Anki a try.
Incorporate flashcard studies both for recreational learning and schoolwork.
If you do this on a daily basis, I think you would be surprised at how much you can memorize.
It only gets easier the more you do it.

### Noteworthy Links
- [Effective Learning: Twenty Rules of Formulating Knowledge](https://www.supermemo.com/en/articles/20rules)
- [Offical Anki Tutorials on Youtube](https://www.youtube.com/channel/UCFt1oYUNiwkMaJTSZiFEodQ)
