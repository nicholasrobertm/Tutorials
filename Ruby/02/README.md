Using your first script
-----------------------

Welcome to the second tutorial! In the first tutorial we learned how to install Ruby, in this tutorial we'll learn the basics of your first script.

rbenv
-----

If you've got rbenv installed correctly, it's super simple to use.

To see what versions of ruby you have you can use:

``rbenv versions``

This will tell you about what ruby versions you have, as well as where they live! But what if you don't have the version you want? How do you know what versions can be installed? To view these you can use:
``rbenv install --list``

This gives you a list of all available versions to install. You then can use the below to install ruby 2.4.0 for example:
``rbenv install 2.4.0``

When you've installed a new version, you want to run `rbenv rehash` as well. What this does is a bit involved, but the main point is running this ensures everything using ruby sees that ruby exists where rbenv installs it.

Once you've installed and re-hashed, you have two ways to start using your new version. You can either set it to be the globally used version, or locally used version.

For setting your global version you use `rbenv global 2.4.0`

For setting your local version you use `rbenv local 2.4.0` This will create a file `.ruby-version` which will contain this version. On my system I have `2.3.1` as my global ruby so running `rbenv versions` from anywhere but this directory on my system outputs:

``* 2.3.1 (set by /home/rob/.rbenv/version)
    2.4.0``
    
Note: the * shows the current version.

Where as doing this from this directory outputs:

  ``2.3.1``\
``* 2.4.0 (set by /home/rob/Devopsdog/Tutorials/Ruby/02/.ruby-version)``

And that's it! If you've made it this far you can skip down to the section 'First Script'

RVM
---

I won't go as deeply into explaining how to use RVM, they have a great basics guide on there website [here](https://rvm.io/rvm/basics)

The main use is similar, however they handle the switch between versions differently.

To install a new ruby version the syntax is much the same. To list ruby versions you can install you use:

``rvm list known``

To list only those installed you use `rvm list rubies`

To install a ruby you use ``rvm install 2.4.0`` where 2.4.0 is the version found from ``rvm list known``

To globally set your ruby version you use ``rvm --default use 2.4.0`` - this sets your default ruby version

To use a different version (without setting your default) you can simply use `rvm use 2.4.0`

Once you've set to use a ruby version just use `ruby -v` and you should see the version you've used, you can now go down to the 'First Script' section.

First Script
------------

Learning a new programming language can often be daunting, however learning the language is often easier than learning other parts of development (Such as best practices, agile or waterfall workflows, what tools to use when, multithreading best practices, etc)

With that said, learning the process to write a program is the difficult task, where as learning the language to write a program is an easy(or easier) task. Given all this learning a programming language to write a program is something anyone can do following the proper guide.

Open up `first_script.rb` in your preferred editor. In my case I'm using RubyMine (A ruby development environment) but any text editor will do (Notepad++, vim, emacs, etc)

Inside this file you'll see the following content:

```
   #!/usr/bin/env ruby
   puts 'This is your first ruby script!'
   puts "Your ruby version is #{%x(ruby -v)}"
```

This may look daunting at first but this is actually a very simple script. Lets break it down line by line.

The first line is something actually not unique to ruby, but something unique to UNIX. 

`#!/usr/bin/env ruby`

This is what's known as a 'shebang' line. This tells the operating system when you execute this script with the interpreter you specify on this line. Examples of interpreters are ruby, python, or even bash! Lets break this down into pieces.

The `#!` is a unique syntax which tells UNIX that there is a shebang line here!

This: `/usr/bin/env` is the _path_ for UNIX to look for the interpreter (in this case ruby).  In this case the path is `/usr/bin/env`. This location is a bit special, it's a non-environment dependent place where interpreters are (usually) included! This means that if you have ruby installed on a UNIX system, no matter where it is including it from here will allow the OS find it at the right place.

The final bit `ruby` is the interpreter. This could be replaced with any interpreter (such as bash, or python) but since we're writing ruby scripts, we use it!

Onto the next line

```puts 'This is your first ruby script!```

Going onto the second line we run into our first method. A method, in this case, is a piece of code used to achieve an end result. 

The name of this method is `puts`. 

What this method does is prints whatever is passed to the method, and adds a new line character `\n` to the end.
In this case we 'pass' the string 'This is your first ruby script' to the `puts` method, which then when executed outputs it to the terminal.

Building Blocks of Ruby
-----------------------

Before we move on to the next line, lets take a second to talk about how this method, and others like it work. `puts` is what is known as a __Kernal__ method.

To explain what the __Kernal__ module is, lets start with explaining what an the building blocks of Ruby. You first start out with what's called an 'Object'. Think of an Object as the most basic level in Ruby (There is something smaller called a 'Basic Object' but we'll not get into that here).

Everything in ruby is comprised of an object, even Modules themselves are an object. An Object itself is a way of grouping methods / functions with data.

Going above the level of Object, you have what's called a __Module__. A module in ruby is a grouping of functions for a specific purpose.

Getting back to where we were, __Kernel__ in ruby is a module. __Kernal__ methods specifically are ones that you likely will need to use everywhere in ruby, they deal with the basic data structures (Think Strings, Integers, or Arrays) and allow you to manipulate them.

A better example of a higher level Module might be a 'Math' module. What if you wanted to create a math method/function that squared a number? This is where you'd make a Module to do just this, include it where you need to use it and then there you go, you have a common way to complete a problem you might need to use in more than one place!

Above a Module is what's known as a __Class__. Classes are much like Modules, however they also have data attached to them. Think of a everyday things, lets say a Dog. Dog's have breeds, or fur color, or eye color, these are things you'd model in a Class!

There is one final level to the hierarchy, but it still is actually just a __Class__. This is known as a __Child Class__, or also a __Subclass__.

Going back to the Dog example, what if you wanted to get more specific? What if you wanted to make a __Smart Dog__ with methods that do things like fetch a paper, or get a soda from the fridge? It wouldn't make sense to add these methods to the basic 'Dog' class - it's not something they would do. Enter the __Subclass__.

When creating a __Subclass__ you're creating a class that __Inherits__ from another class, also known as it's __Superclass__ or __Parent Class__. All of the __data__ and __methods__ of the __Parent__ class are available to the __Subclass__. This means if you had a Bark method in the __Dog__ class, you could call this function from the __SmartDog__ class.

From this you can see it's clear that you use a __Class__ when you want to associate data with the functions you're making where as you use a __Module__ when you just want to execute a specific task.

Understanding these relationships are important, they help you understand questions like 'Why would I use a module instead of a class', or how to best Implement something you're trying to.

Now that you understand that everything is an object, it makes sense you can call `puts` from anywhere. When we're talking about passing objects to methods, in ruby it might look a bit different if you came from other languages. The important thing to know is:

```
puts('my string')
puts 'mystring'
```

Are both actually the same! You actually can do this with multiple arguments as well, for example:

`puts('string1', 'string2')`

`puts 'string1', 'string2'`

Both of these would output:

```
string1
string2
```

To your console!

The final bit to discuss is the last line:

`puts "Your ruby version is #{%x(ruby -v)}"`

We already know what `puts` does however there are two new things to explore here. The first we'll cover is what the `%x(ruby -v) is doing.

When you're making a script, there may be a time when you want to ask the system you're running it on for something. In this case it's a bit self explanatory, we're asking the system to run the `ruby -v` command. the `%x()` part here is saying to ruby 'Run this system command and return me the output, so when we run this ruby script, it should output your ruby Version! There are actually more ways to do this than just using the %x() but they work differently in some ways, we'll save this for another tutorial, for now just understand you within ruby have a way to tell the system to run a command and give you back the output.

The final thing here is the use of double-quotes. When you use single quotes in ruby, it treats what's in those quotes directly as a string.

If we did `puts 'Your ruby version is #{%x(ruby -v)}'` it would return this:

```Your ruby version is #{%x(ruby -v)}```

Which isn't what we want! Single quotes however are useful (and recommended to use) when you don't have anything inside the quotes to be executed.

The fancy part of double quotes is the `#{}`. Think of this as a way to say `Execute what's inside this from ruby`. In our case we used this to 'Shell out'(another way of saying make a call to the system's environment) and call that system command.

However you could also use this in different ways. What if you have a variable called `numberOfDogs` which is set to `5`, how would you output that in a string?

Here you are wanting to 'Combine' the strings, and essentially that's what the `#{}` does. If you had:

```puts "I have #{numberOfDogs} dogs!```

You'd get back:

```I have 5 dogs!```

Another way you could do this is something like:

```puts "I have " + numberOfDogs + " dogs!"```

But the first way is much cleaner! We've gone through a lot in this tutorial, if you've made it this far on to lesson 3!