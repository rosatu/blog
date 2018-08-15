---
layout: post
title:  "Rosa Tu's CU Desi(g)n: A new mnemonic/acronym for Roy Fielding’s seven routes"
date:   2018-08-14 21:18:27 -0400
---
This post begins as an angry post. Because I am angry. At Roy Fielding.

Who is Roy Fielding? A computer scientist from 2002, a time when:
- Web apps were starting to communicate more with each other.
- The internet was a Wild West of inconsistent names for the same set of common actions (aka routes) websites performed.

So during these wild times, Roy decided we should standardize. He said “Hey guys, we should use the same names for these seven things that all our websites do! And we should use the same URLs for each of these actions! Here, I'll write my dissertation on this.” This was cool, cause it saved developers time and helped them communicate better.
>Very cool, Roy. -Rosa Tu

Then, tragically, Roy did something extremely UNcool; something that 18 years later came to haunt me in my sleep. Roy named his design convention “RESTful routing.”

>Not cool, Roy. Not cool. -Rosa Tu

There’s nothing restful about “RESTful routing". “Representational State Transfer” probably makes sense at it's core, but doesn't do anything for people who are trying to remember these seven routes. This is infuriating because something I love so much about learning Programming is the care with which things are named, and this name seems so needlessly academic. Also, it's hypocritical not to name this convention something intuitive. The point of creating a standard is to make things more efficient, and it's inefficient to have a name that doesn't actually represent the content of whatever that name is supposed to stand for.

---------------------------end of angriness---------------------------
---------------------------end of angriness---------------------------
---------------------------end of angriness---------------------------
---------------------------end of angriness---------------------------
---------------------------beginning of inspiration


So this is my proposal. I say that from now on we stop using the term RESTful routing for these seven standard routes. Instead, let's use this mnemonic that I've come up with:

                       CU Desi(g)n

Do you like it? Do you see what’s going on here? These letters (minus the g, which is just there because this is GENIUS) represent the seven routes. Create, Update, Destroy, edit, show, index, and new.

A big problem I had understanding restful routing was the difference between update and edit, or new vs create. The names seemed interchangeable to me.

After much unnecessary weeping, it became clear that “new” renders a form for the user to input new information, but “create” saves that information in the database. In the same vein, “edit” shows a form, while “update” modifies the database.

#### CU Desi(g)n

So notice how I’ve capitalized the first three letters of this nemonic. These letters stand for routes that actually make changes to the database. Create, Update, and Destroy. If you want to match them with HTTP verbs, these three are all the routes that don’t require a “GET” request. Does that make sense?

 Route Name  | HTTP request
------------ | -------------
Create | you “POST” the users input to the database
Update| you “PUT/PATCH” (aka replace/modify) the info on the database
Destroy | you “DELETE” info from the database
the other four routes (edit, show, index, new) | you “GET” a view (ie a form, or list) to display to the user


  As for the actual URLs (for some reason called "actions" here) that you send along with your HTTP requests, these are just convention. But when you remember what each route is actually doing, the names seem more logical (except for create, that's still weird).


  Route Name  | "action" (the URL you're sending along with the HTTP request (broswer--->server) )
  ------------| -------------
  Create | /m (This "m" stands for the model name pluralized. So if your site has a model named "Whale", you replace "m" with "whales") (in the Create route, you create a whale instance and save it to the database)
UPDATE | /m/:id (in this route, you modify an existing whale instance and save it to the database)
DESTROY | /m/:id (in this route, you delete a whale instance from the database)
edit | /m/:id/edit (in this route, you render an "edit" form for the user--they will modify the details of an existing whale instance)
show | /m/:id (in this route, you display the details of a specific whale instance)
index | /m (in this route, you list all whale instances)
new | /m/new (in this route, you render a "new" form for the user --they will input details for a new whale instance)

So, if you must use these routes (ie with Sinatra, or Rails which encodes this convention in its secret magic), I hope this mnemonic makes it easier for you. And I hope from this day forward no one ever loses sleep because they were trying to struggle through their own confused misunderstanding of RESTful routing.

---

p.s. in Rails you can type `rails routes` to see all these routes. Still, I think the nemonic will help you remember 1: That these routes are just a design convention 2: What kind of HTTP request you should make to the server 3: Which function each route is actually trying to perform.
