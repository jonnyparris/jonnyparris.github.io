---
layout: post
title:  "DBC Phase 2 - Day 3 Reflection"
date:   2014-09-17 23:15:46
categories: notes DBC-reflections
---
### Memorable
* Tiny yoga class
* Topher fixed all the things
* Almost(?) overwhelming amount of new data
* Pimped my macbook to true satisfaction

### Learned
Normally I just jam out some bullets here to force me to vaguely remember what information was thrown at me throughout the day. However, today was so dense that many of the bullets deserve a further exploration in their own post at some point in the future. That warrants at least some organisation of the bullets for the time being:

#### Macbook Pimping
* You can set syntax specific preferences in Sublime (useful for the tab spacing in ERB, ruby, rspec)
* Autocompletion of git branches and other git whatnots in the terminal requires just a little bit of magic in your `.bash_profile`


#### General Coding
* *Test Driven Development...is good* - regardless of the specifics, the process of writing tests before you start coding forces you to *think before you code*, which I think can only be a good thing for any substantial projects. You might not ever get around to writing the tests out fully or properly but you do consider your project from the user's perspective.
* *rspec (and testing in general) should follow a logical flow:*
    - `#arrange` - set up any objects or data required for the test to run
    - `#act` - perform the action that you're testing
    - `#assert` - evaluate whether the impact of that action was as intended


#### Syntax/Language Specific Tidbits
* *TDD using rspec to test route controllers* - you can write tests for the http status requests returned when you hit a server with a route. Here's an example of testing to see whether a route exists (200 is a successful "OK" request status.)
```ruby
describe "Post /urls" do
  it "responds with a successful status" do
    post '/urls'
    expect(last_response.status).to eq(200)
  end
end
```

* rack bridges the gap between application servers and ruby code
* *plenty of shortcuts*, but perhaps `shift+command+w` to close a whole window instead of just one tab at a time with `command+w` was a particular highlight.
* you can amend your last commit in git using `git commit --amend`

### Feels
I was sidetracked a wee bit today, hopping down various rabbit holes to get my macbook running smoothly (Postgresql is pain), but also running smoothly with cherries on top.
I'm hoping that it's going to pay off quickly as it means that I'm now extremely comfortable completing challenges on my own machine. That brings the advantages of better mobility, understanding of my tools, and it means that my endless googlings are all being tracked in one browser. I can contribute to the same bank of bookmarks, execute all the numerous shortcuts via the plugins and addons I've already been using for months, and generally feel like I'm owning the experience more.

How about some actual feels then, eh?
Well, I feel super stoked that once again the day has raced by me because I've been way too busy engaging and learning and enjoying myself to both checking the fancyschmancy watch on my wrist (or my phone!).
I feel a bit daunted about the large amount of work that I have to catch up on from today. That's kind of a good feeling though, and I don't think I'm alone in my behindness even if other people are feeling behind for different reasons. That's comforting.

Yoga today was really pleasant - it really feels great to be so *present* in a more physical yet calm way for a chunk of the day.