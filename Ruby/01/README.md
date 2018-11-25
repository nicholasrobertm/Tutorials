Installing Ruby
---------------

How you install ruby can be very varied depending on your operating system, and how you want the environment to be setup.

Ruby supports almost any operating system, and on those it doesn't directly support, it usually can be built from source.

Before installing there are a few concepts you have to understand. When installing ruby there are four main ways you can install it. These are:
* Using your systems package management system (apt, yum, etc)
* Using an installer (RubyInstaller for example is popular for Windows)
* Using a Ruby manager
* Installing from source

The first two are self explanatory, these are installed like you would install any other program on your system. Ruby managers are made specifically to facilitate working with multiple ruby environments. This is useful specifically if you have:
* Multiple ruby versions used in different environments / scripts.
* Want to test against the latest ruby version
* Want to isolate libraries, known as 'gems'

For the most part the reason for it is the first scenario. An example of this is if you're on MacOS and some flavors of linux, it has a system ruby installed. You don't want to mix your system's version of ruby up with your scripts because if you're developing a script, and upgrade the ruby version, it could break other things running on the system.

Finally, building from source will not be covered here, but this is mostly used by people who either want to implement their own features when they can't do so otherwise (there aren't many times this happens) or if the system doesn't have an install method (the more than likely scenario for this)

For your systems specific instructions on how to install ruby see the [Ruby Documentation](https://www.ruby-lang.org/en/documentation/installation/)

I'd recommend either using __rvm or rbenv__, they will make your life much easier going forward, these tutorials specifically will use rbenv.

Once you've got ruby installed, to test that it's working try running the `hello_world.rb` found in this directory. 

You can do this via the below in a terminal window:
``./hello_world.rb``

If you see the message `Your ruby is working!!` you've got everything working! That said you can move on to lesson 02.