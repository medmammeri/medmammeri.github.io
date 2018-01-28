---
layout: post
title:  "First Jekyll!"
date:   2018-01-27 22:13:07 +0100
categories: jekyll update
---
Ok You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.


{% highlight python %}
# -*- coding: utf8 -*-
import json
import random

# Give a Json file and return a List
def read_values_from_json(path, key):
    values = []
    with open(path) as f:
        data = json.load(f)
        for entry in data:
            values.append(entry[key])
        return values

# Give a json and return a list
def clean_strings(sentences):
    cleaned = []
    # Store quotes on a list. Create an empty list and add each sentence one by one.
    for sentence in sentences:
        # Clean quotes from whitespace and so on
        clean_sentence = sentence.strip()
        # don't use extend as it adds each letter one by one!
        cleaned.append(clean_sentence)
    return cleaned

# Return a random item in a list
def random_item_in(object_list):
    rand_numb = random.randint(0, len(object_list) - 1)
    return object_list[rand_numb]

# Return a random value from a json file
def random_value(source_path, key):
    all_values = read_values_from_json(source_path, key)
    clean_values = clean_strings(all_values)
    return random_item_in(clean_values)


#####################
###### QUOTES #######
#####################

# Gather quotes from San Antonio

def random_quote():
    return random_value('quotes.json', 'quote')

######################
#### CHARACTERS ######
######################

# Gather characters from Wikipedia

def random_character():
    return random_value('characters.json', 'character')


######################
#### INTERACTION ######
######################

# Print a random sentence.

def print_random_sentence():
    rand_quote = random_quote()
    rand_character = random_character()
    print(">>>> {} a dit : {}".format(rand_character, rand_quote))

def main_loop():
    while True:
        print_random_sentence()
        message = ('Voulez-vous voir une autre citation ?'
                   'Pour sortir du programme, tapez [B].')
        choice = input(message).upper()
        if choice == 'B':
            break
            # This will stop the loop!

if __name__ == '__main__':
    main_loop()
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
