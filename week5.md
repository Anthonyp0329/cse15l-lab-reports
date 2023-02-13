# Week 5 Lab Report
Today's topic: The **grep** command!   
We will be exploring the **grep** command and its possible options!

## 1. The -i option
Here's an example of this option and what it does: 
```
anthony@Anthonys-MacBook-Air-2 written_2 % grep -i "resTAUraNT" travel_guides/berlitz1/WhereToItaly.txt 

wonders when entering or leaving a shop or restaurant. In a land where
restaurant Da Pancrazio, whose cellar shelters ruins of Pompeii’s
restaurants and boutiques, a vibrant local pride nurtured by economic
people-watcher’s delight lined with smart cafés and fine restaurants,
paths lead to farmhouses and rustic mountain-restaurants where you can
prestigious museums, excellent restaurants and shopping, and
restaurants, bookshops, and boutiques are showcased in its unabashed
attractive, modern town full of shops, hotels, and restaurants known
to spend hours in the restaurants. Naples is where pizza began (the
Santa Lucia is now lined with elegant hotels and restaurants, many
cafés and restaurants until the cool wee hours, and restore some of the
restaurants that stay open until all hours. In the little church of
```
As you can see, this command does a case insensitive grep search! Clearly these lines don't contain "resTAUraNT"
spelled like that, but the command still returns all the lines with "restaurant" in it!

```
anthony@Anthonys-MacBook-Air-2 written_2 % grep -i "genoese" travel_guides/berlitz1/WhereToItaly.txt

Genoese pasta dishes.
Genoese painters: Cambiaso, Strozzi, and Magnasco, as well as works by
```
Here's a better example of when this command can be useful. Let's say I wanted to look for where Genoese things were mentioned, but wasn't sure if the author capitalized it or not. Instead of trying two different commands, I can just use the -i instance to find everytime "Genoese" is used without having to try both commands.

     
## 2. The -r option
Here's an example of a grep command using -r:

```
anthony@Anthonys-MacBook-Air-2 written_2 % grep -r "pasta" travel_guides/berlitz1/          
travel_guides/berlitz1//WhereToItaly.txt:        Genoese pasta dishes.
travel_guides/berlitz1//WhereToItaly.txt:        change from pasta.
travel_guides/berlitz1//WhereToItaly.txt:        risotto, pasta, and polenta.
travel_guides/berlitz1//WhatToDublin.txt:        Bistro for pizza and pasta in Castle Market, Fitzer’s cafés, and the
travel_guides/berlitz1//HandRIsrael.txt:        Tel. (02) 671 0632. A vegetarian restaurant serving great pasta,
travel_guides/berlitz1//HandRIsrael.txt:         — good pizzas, interesting pasta dishes. Eat out on the tree-shaded
```
This commmand searches through every file in the directory for the search string! If I wanted to look for all the places I could eat pasta, instead of searching through each file individually, I can search through each file in a directory. So useful!

```
anthony@Anthonys-MacBook-Air-2 written_2 % grep -r "excellent cuisine" travel_guides/berlitz1/
travel_guides/berlitz1//WhereToMalaysia.txt:        character and a location for excellent cuisine. A boat can be hired
```
Here's another example of this commands usefulness. With one command, I was able to find the country with excellent cuisine! Guess I'm really hungry while doing this lab report, I keep searching stuff related to food. Maybe I should eat. I like food.

   
## 3. The -l option
The -l option complements the -r option perfectly, here's some examples of it:

```
anthony@Anthonys-MacBook-Air-2 written_2 % grep -r -l "awesome" travel_guides/berlitz1/
travel_guides/berlitz1//WhereToItaly.txt
travel_guides/berlitz1//WhereToIsrael.txt
travel_guides/berlitz1//WhereToFrance.txt
travel_guides/berlitz1//WhereToMallorca.txt
travel_guides/berlitz1//WhereToLosAngeles.txt
```
This command, instead of outputting the lines in which the search string is contained, simply outputs the files it matches for. So here, all it returned was the txt files containing "awesome", rather than the files along with the lines.

```
anthony@Anthonys-MacBook-Air-2 written_2 % grep -r -l "trampoline" travel_guides/berlitz1/ 
travel_guides/berlitz1//HandRJamaica.txt
travel_guides/berlitz1//WhereToIsrael.txt
```
Let's say I wanted to see which countries I could explore that have "trampoline", rather than seeing the lines in which "trampoline" is contained. The -l command solves this conundrum for me!

   
## 4. The -w option
The -w option is great for seraches, here's why: 
   
```
anthony@Anthonys-MacBook-Air-2 written_2 % grep -r -w "awe" travel_guides/berlitz1/
travel_guides/berlitz1//WhereToLakeDistrict.txt:        awe-inspiring view north over the diminutive Brothers Water, so called
travel_guides/berlitz1//WhereToLakeDistrict.txt:        Bassenthwaite Lake in the distance. It’s an awe-inspiring sight, but
travel_guides/berlitz1//HistoryDublin.txt:        the poet was held in awe. Law and religion were important in Celtic
travel_guides/berlitz1//WhereToIndia.txt:        you may have already seen it from a distance, is still an awe-inspiring
travel_guides/berlitz1//WhereToItaly.txt:        by every stone of St. Peter’s Basilica and in the almost physical awe
travel_guides/berlitz1//WhereToItaly.txt:        centuries. Most rushed visitors see the square, stand in awe of the
travel_guides/berlitz1//WhereToEgypt.txt:        truly awe-inspiring find which still dazzles the eye even after over
travel_guides/berlitz1//WhereToFrance.txt:        Grünewald’s awe-inspiring Isenheim altarpiece. Created for the
travel_guides/berlitz1//WhereToFrance.txt:        atmospheric changes for 17,000 years, these awe-inspiring frescoes and
travel_guides/berlitz1//IntroGreek.txt:        of Mykonos and the awe-inspiring caldera of Santorini.
travel_guides/berlitz1//IntroItaly.txt:        The world also stands in awe of Italian cuisine. In the
travel_guides/berlitz1//WhereToIstanbul.txt:        Süleyman, in awe of his architect’s achievement, handed the keys to
```
This command searches for a word rather than just a substring. So, when I used the -w option along with "awe", it didn't return any lines with the word "awesome", but only lines with "awe" on its own.

```
anthony@Anthonys-MacBook-Air-2 written_2 % grep -r -w "th" travel_guides/berlitz1/
travel_guides/berlitz1//WhereToItaly.txt:        This is where th e thousand-year-old Repubblica Serena
travel_guides/berlitz1//WhereToJerusalem.txt:        page 82). John D. Rockefeller Jr. provided th e money to build this
```
Here's an example of a useful use case of this option. Here, I was able to find when the word "the" was typoed, as I was able to look for "th" on its own. Without the -w option, this would return a large amount of lines and I wouldn't be able to gain any useful information from it.


Well, there's this weeks lab report. Thanks for reading!

-Anthony :)


Source: https://www.geeksforgeeks.org/grep-command-in-unixlinux/ 

