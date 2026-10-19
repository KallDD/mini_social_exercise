What features did you implement, and how does each implemented feature function? (with enough detail)

Recommendation function:
I implemented content filtering to my recommendation function, it querries 10 latest posts that the user has reacted to and 
10 latest posts that the user has commented to. The function goes through all max 20 posts and makes
a ranking of all words used in those posts giving them relevance score. A word gains +1 score each time the algorithm comes a cross it.
After all that top 3 of those words are selected and the posts table is querried for posts that contain one or
more of the seleceted relevant words. Newst posts are shown first and the amount of recommendations is limited to 5 posts.

Chapter 5, Design claim 3 "Recruiting new members from the social networks of current members increases the number of new members more than impersonal methods":
I implemented a feature that makes a custom invitation link for each user that they can use to invite
their firends to the platform. If the person signs up through the invitation link the action is saved
to database by adding a invitor id to the users table invitor column.

The feature works by taking url parameter in the signup path /signup?u=<user_id>. If this parameter is empty
the invitor id will be set as None/Null else the preson ID who sent the link will be added upon the user creation
to the new users invitor column.

To gain an invitation link user can copy it from the front page when they are logged in. The link is generated
in the feed.html.j2 template when the page is loaded. User can click copy button placed next to the link to easily copy it.

The deature fulfils the design claim by allowing exsisting users to easily personally invite their friends 
to join the community. In the future this feature could be tied to a reward system.

Chapter 5, Design claim 4 "Making it easy for users to share content from a community site with their friends (eg., via easy email, Twitter, Facebook, and similar links) will increase the visibility of the community among the users friends and thereby increase the likelihood of them joining":
In this feature I implemented a share button that allows users to easily share content throug links.
The feature is missing integration to suggest applications where the user could share the link.

The feature works similary to the "Invite friends" feature. This time the link is bit more complex /posts/3046?l=de2d7f38-8a84-482d-a6cf-0571d3bfef68. The link is 
generated when user presses the share button. The button calls /posts/<int:post_id>/share endpoint where the app 
checks if the user has already generated a link for this post. If a link had been generated earlier the same link 
will be given to the user. If no previous link exists for the user a new link will be generated that the user can share.

The links are stored in Share table that has three important columns UUIDv4 id, user_id and post_id. With this
information I can display how many confimed users have shared a post. This data could also be used to see which
users have opened certain links and these could also be taken into account as contributions.

This feature fulfils the desing claim by allowing allows users to share posts to other members or to users
that do not have account, increasing the visibility of the community.

What did you learn during the coding assignment?

I learned about recommendation functions and how they work and again I gained more knowledge about how this
application specific architechture works together with the templates and python code.

What was difficult, if anything?

I did not find anything to be difficult, I could utilize ideas/functions that I was already familiar with.
The task was interesting and the desing claims did not feel as arbitary as in the assaingment 1 so it felt 
easier to make the features.

Usage of AI:
In the recommendation algorithm I ideated and wrote the word relevance score system, I did use line autocompletion.
 I used AI to make the dynamic querries for fetching posts and list sorting. I reviewed the AI generated code and tested that it
works like I wanted to.

In the features AI made the HTML and script(function) for the share button onClick event following my instructions.
Again I reviewed all the code. I integrated the changes since I told the AI not write it directly in to the code base.
I wanted to have control over where the functions would be implemented and it also helped me understad and review each function better.

Repo: https://github.com/KallDD/mini_social_exercise

