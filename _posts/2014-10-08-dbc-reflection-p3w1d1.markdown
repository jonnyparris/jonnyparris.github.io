---
layout: post
title:  "DBC Phase 3 - Days 1-3 Reflection"
date:   2014-10-08 22:13:46
categories: notes DBC-reflections
---
### Memorable
* "Data is like water"

### Learned
* Day1 - Intro to phase 3 and Rails auto-magics
* Day2 - Rails auto-magics part II
* Day3 - TDD in Rails and beyond
* Other flavours of coding Kool-Aid

#### Phase 3
At this stage, we're supposed to know enough to take on the rest of the DBC curriculum in the role of 'junior devs' as opposed to regular civilians. Similarly, the learning goals seem centred around honing the habits that distinguish *good developers* from *hackers*. Some examples:

* writing clean code
* extensive github use (regular commits, sharing code, sharing feedback)
* immaculate github workflow
* test driven development (TDD)
* extensive use of the unix terminal
* challenging opinions and forming our own about the plethora of tools available to get the job done
* a more independent team project workflow using full stack feature slices of an app
* *making sure that we weed out any "this is the only way I know how to do this" knowledge gaps*
* encouraging exploration of other coding fields that interest us (there's no excuse to be bored in phase 3!)

There's more along that theme, and it's pretty exciting to feel more comfortable with the definition of *good programming* and some solid steps required to get there.

#### Rails & Sorcery
The brief is to learn how to comfortably make apps with rails so that we can identify its limitations, leverage its advantages and know what questions to ask of competing frameworks/building options.
So far, the amount of gizmos that rails provides via its conventions has been intimidating. It's the first time since phase 0 that I've seen lines of code where I simply have no clue how to begin interpreting what they might represent and how they will behave. There's a whole new set of reserved words to watch out for and "shortcuts solutions" that have been implemented for problems that I'm yet to fully understand, let alone be bothered by.

This will be an ongoing struggle for at least the next few days as I try to recreate apps from Sinatra and attempt to digest the mercifully thorough rails guides documentation.
The confusion is very encouraging, but also very exhausting.

#### TDD in Rails and Beyond
Myles Byrne & Anne Spalding gave very illuminating lectures today on the topic of test driven development along with some insight into good git practice.

##### TDD in Rails
* Feature tests should assess a full stack of unit tests contributing to the successful implementation of that feature. E.g. "Input a set of numbers on page A, outputs the sum of those numbers on page B"
* Unit tests, such as model tests, controller tests, view tests (uncommon) should all operate as independently as possible from each other. E.g. don't rely on a route to serve up the method that you want to test. Instead, test that method directly, bypassing whether route serves that or not.
* BDD is basically capybara (cucumber is not strictly necessary)
* Capybara's core function is to emulate a web browser. It does so using Nokogiri with some added code on top. This just happens to be super handy for feature testing, but it's capable of more.
* Try to extract out your core *business logic* for tests independent from the rest of how your app fits together.
* Outside-in is one approach to TDD: write a feature test, write the subsequent unit tests as the feature test fails for different reasons. It's like using TDD to write tests instead of code!

##### Git + Github flow    
* You can make comparisons between a particular commit and the current final commit in github that's useful for tracking the story of the code.
* Why not make your github aliases one-letter long in the terminal? Idea: turn them on/off with another alias that lives in the bash profile so it's not always a potential conflict threat.
* 2 main things to check for when you're reviewing a commit - *console logs* and *commented out code*
* Use git clean to remove unwanted files from the git tracking.
* Commit your readme for the project before anything else.
* ...then commit any boilerplate (e.g. rails files) and include the version number of any boilerplate you're using.
* You can "spike" on a topic to investigate something, but never commit the new crappy code that results from it to your production.

#### Other Flavours of Coding Kool-aid
Part of forming an opinion on what I like or don't like about the plethora of options available to get the job done is asking other people what they think about certain topics. Some views that have stuck out so far:

* rspec vs minitest - why bother with rspec when minitest is quicker and is not a domain specific language (DSL)?
* "If the candidate is savvy in their unix command line, then that shows that they've been using it a lot, which shows that they know how to debug, and that might make up for a lack of prowess in other areas of the interview"
* "Companies should have location independent pay scales, if their engineers are location independent"
*  "Your code should have as few dependencies as possible"

### Feels
* Fatigued!
* Proud to have independently invested in TDD ahead of the time when it's shoved down our throats by phase 3 and future employers
* Happy to be getting so much more attention from instructors - Brandon is awesome.
* Much closer to the cohort, and really moved to receive their support in moments of pure confusion.
* Glad to be keeping up with yoga twice a week.
* Excited to get to know another cohort.