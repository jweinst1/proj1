# Q0: Why is this error being thrown?
An uninitialized constant is throwing the error because the Pokemon model does not yet exist as a model.

# Q1: How are the random Pokemon appearing? What is the common factor between all the possible Pokemon that appear? *
The Pokemons do appear because first, we've seeded the database with around four Pokemon, second, in the `home_controller`, we have picked out a variable `@pokemon` to represent a Pokemon in the database that is still currently without a trainer, and (3) in `views>home>index.html.erb`, we have Ruby code that prints the wild `@pokemon` is happening to appear, so long as both the wild `@pokemon` exists (there is a Pokemon without a trainer in the database) and there is a current trainer (a user is logged in). If `@pokemon` is deinitialized, than trainer will be deleted.

# Question 2a: What does the following line do "<%= button_to "Throw a Pokeball!", capture_path(id: @pokemon), :class => "button medium", :method => :patch %>"? Be specific about what "capture_path(id: @pokemon)" is doing. If you're having trouble, look at the Help section in the README.
It creates a button that, once clicked, will call the patch route prefixed with `capture`. The `@pokemon` parameter (the current wild pokemon) is sent as the input parameter along the `capture_path`, which calls on the `#capture` action in the `pokemons_controller`. The capture method runs, and redirects back to the homepage via the `root_path`.

# Question 3: What would you name your own Pokemon?
Kodasaur

# Question 4: What did you pass into the redirect_to? If it is a path, what did that path need? If it is not a path, why is it okay not to have a path here?
I redirected to `:back`, which takes me back to the last page I came from (in this case, the Pokemon's trainer's page). This is not a defined path in the routes and it does not need anything else; it's okay to not have a path from the `routes.rb` because I'm just going back to the page I came from. I could have also defined a variable `@trainer = @pokemon.trainer_id` and used `redirect_to trainer_path(@trainer)`. This path needs the Pokemon's trainer's id because if we look at the routes, the URI pattern to show the trainer's profile page is `/trainers/:id(.:format)`, which requires the `:id` parameter to be passed in.

# Question 5: Explain how putting this line "flash[:error] = @pokemon.errors.full_messages.to_sentence" shows error messages on your form.
Values stored in the flash will only be available in the next request, as it is cleared out with each request. (Source: `http://guides.rubyonrails.org/action_controller_overview.html#the-flash`) Therefore, the flash feature stores the last input the user put in as the new Pokemon's name for potential flashes. If it was an empty input, the flash knows it was empty and flashes the appropriate error requesting that the user input a name; if it was a duplicate name, the flash knows that the name is already in the database and lets the user know that the name is not unique. Side note: error throwing can also be done in the `simple_form_for`; however, the error message throwing is not as tailored to each specific error because only one error message is preset into the code.

# Give us feedback on the project and decal below!
This project was pretty enjoyable to work on, and I think I've also learned the most from this assignment of all the ones we've had in the class thus far. Although we haven't done the final project yet, I imagine this project is a nice bridge between the homeworks (which are very guided) and the final project (which is much more open-ended).
I think lectures cover good walkthroughs of how everything works/what we're expected to know how to do. Some suggestions: it would be helpful to have more words/information on the slides, and maybe even have a version/snippets of the code from the live demos available post-lecture (I know they sometimes follow the homeworks pretty closely, so maybe just snippets?). I do learn a lot from having to look elsewhere and Google/read docs, but sometimes there are specific things that happened in lecture that I want to remember or small things I didn't catch the first time around, and it's hard to go back and look for these details without having to search through the entire videos again. The live coding demos are really helpful, though!

# Extra credit: Link your Heroku deployed app
http://pokeportalproject.herokuapp.com/
