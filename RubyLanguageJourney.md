Ruby on Rails Language Journey

## Prerequisites

The majority of the work we do at Radial in Ruby benefits from having the following installed:
[Readline](https://ftp.gnu.org/gnu/readline/) - Readline gives you a set of commands for manipulating text as you type it in so if you miskey you don’t have to retype the whole line. 
[wiki](https://en.wikipedia.org/wiki/GNU_Readline) [documentation](https://www.gnu.org/software/bash/manual/bash.html#Readline-Interaction)
[xCode](http://docs.railsbridge.org/installfest/install_xcode_command_line_tools) – Additional command line tools but only available for mac. If using Ubuntu you can install the [build-essential](https://packages.ubuntu.com/xenial/build-essential) package which will give you compilers, debuggers, linkers, etc
You also need to agree to the EULA if using OS X.

## History of Ruby/Rails

Ruby on Rails, or Rails, is a server-side web application framework written in Ruby. The distinction between Ruby and Rails is important, however our use of Ruby at Radial at the time of this writing is entirely in the context of Rails. As such this document is not only not comprehensive, it is not comprehensive in a limited scope.

Yukihiro “Matz” Matsumoto is credited as the creator of Ruby. His demeanor has brought about a motto in the Ruby community: “Matz is nice and so we are nice,” abbreviated as MINASWAN. He made the reference implementation of Ruby, Matz’s Ruby Interpreter (MRI), for which he is still leads development.

Another one of the key figures in the Ruby community is known by the pseudonym “why the lucky stiff,” often abbreviated as “_why”. Before deleting his Twitter and GitHub accounts, _why tweeted the self-fulfilling prophecy, “programming is rather thankless. u see your works become replaced by superior ones in a year. unable to run at all in a few more.” However _why strove to make make programming accessible and appealing to adolescents and to solve [The Little Coder’s Predicament](https://github.com/hacketyhack/hacketyhack/wiki/The-Little-Coder's-Predicament).

The third key figure in Ruby is David Heinemeier Hansson (DHH). Hansson is credited with the creation of Ruby on Rails. DHH made a [Ruby on Rails demo](https://www.youtube.com/watch?v=Gzj723LkRJY) in 2005 where he premiered Rails to the world and gave us the wonderful catch phrase, “Whoops! It worked”.

## Key features

Ruby is a pattern language, which makes comprehensively learning Ruby akin to learning a spoken language. However many common problems have elegant expressions and solutions incorporated into the language itself, and are described in terms with meaningful names. The compiler is also forgiving in that punctuation identifiers can be omitted (most of the time) so long as they can be inferred from the context.

# Functions
There are three kinds of function objects that exist in Ruby: blocks, procs, and lambdas. Blocks are functions that can be passed into methods. Procs are a way to define a block within the context of a method, so if you’re writing functions within a method you would use procs. A lambda is a way to define a block and its parameters.

# Variables
There are five different types of variables in Ruby: global, local, class, instance, and constant. They each have a unique prefix to identify their type. They also will behave differently if referenced before being initialized. You can access the value of any variable or constant by putting a hash (#) character in front of its name.


There are also pseudo-variables which have the appearance of local variables but behave like constants: self, true, false, nil, _FILE_, and _LINE_. You cannot assign any values to these pseudo-variables.

# Case statements
Ruby has a case evaluator that reduces much of the repetitive typing of other languages. You give the case statement which variable it should evaluate, and follow it with one or more when statements to define the response. When statements can use ranges, regex, procs, type, and other comparisons. It also doesn’t fall through; once a condition is found it breaks automatically.

More information can be found [here](https://www.rubyguides.com/2015/10/ruby-case/)

## Meta-programming
One of the strengths of Ruby is the ability to meta-program, to write code that writes code. Everything in Ruby is an object, even classes, which means the fundamental components of the language can be manipulated. This can greatly reduce the amount of repetition in your code and simplify it, or it can turn your code into something cryptic and unintelligible. Some of the tools of metaprogramming are as follows:

# method_missing
Defining method_missing allows Ruby to take an alternative action if a method called is missing. Instead of just throwing an exception Ruby will attempt to execute the method_missing method.

# class_eval and instance_eval
In Ruby an object can be instantiated into multiple instances of the same object. Class_eval allows you to define an instance method that applies to all instances of a class object. Instance_eval allows the definition of a class method that is associated with the class object but not visible to the instances.

# Introspection
Because Ruby is an interpreted language rather than a compiled language, programs are able to see themselves and answer questions about their components. For example the “class” method can be used on an object to return a string that represents its class. The “instance_of?” method can be used on an object to determine if it is an instance of a specific class. And the “methods” method can be used to return an array of the methods available to an object instance. There is also an “inspect” method which lets you see an object in a human-readable way, “respond_to?” which checks if an object has a particular method, and “instance_variables” which shows what variables are defined for an object.

# Mutable Class Instances
Through a combination of the _eval methods and introspection methods the states of objects can be changed. The vast majority of Ruby is made up of mutable objects. I fear this has been understated.

The exceptions generally are numbers, true, false, nil, range objects, and classes without methods that can alter its state. However by calling the “freeze” method an object that might otherwise be mutable can also be made immutable.

# Eiganclasses

Introspection and mutability allow for classes to be manipulated, but sometimes you might want a class to be private. Well it turns out these private classes already exist for everything and they are called eiganclasses. An eiganclass is accessed using the method “class << self”. 

## Comparison to other languages

# Testing

When testing Ruby it’s advisable to use the gem “pry” to allow inserting “binding.pry” into your test cases. When binding.pry is hit it will allow you to step through the code using “next”, but meanwhile you’ll be able to use console commands to check the state of your program.

## Further Reading

Getting Started with Ruby on Rails tutorial
[Heroku’s Getting Started Repository](https://devcenter.heroku.com/articles/getting-started-with-ruby)
Railsguides.org’s Advantage of Getting Started on Ruby on Rails
[Ruby on Rails Style Guide](https://github.com/rubocop-hq/rails-style-guide)
Rails Casts from Ryan Bates
[APIdock](https://apidock.com/ruby)
[Ruby-doc.org](https://ruby-doc.org/)
Programming Ruby the Pragmatic Programmers’ Guide
Metaprogramming Ruby the Pragmatic Programmers’ Guide
[API Documentation Guidelines](https://guides.rubyonrails.org/api_documentation_guidelines.html)

## Tools and Workflow

You’re going to need RBENV, RVM, or Trueby. It’s advised to install them directly from github. If you use RBENV you will also need ruby build as an extension.

Packages in Ruby are called gems. We don’t use gemsets, but it is a thing that is supported. Instead we use bundler to manage package sets ($ gem install bundler). Typically we use ‘gem’ to install global ruby packages, and bundler to install sets of packages.

There are also some common commands you should know:
The _rails server_ command launches a web server named Puma which comes bundled with Rails. You'll use this any time you want to access your application through a web browser.
The _rails console_ command lets you interact with your Rails application from the command line. Basically it’s _irb_ with the benefit of including your application environment so you don’t need to _require_ your gems manually.

## Common Libraries and Framework

The standard library of Ruby is extensive. Consider checking API dock to see if there is already a method for doing what you want to do.
[sidekiq](https://github.com/mperham/sidekiq) helps handle background processing in a simple and efficient way, useful for job scheduling and works with resque
[resque](https://github.com/resque/resque) is a redis-backed Ruby library for creating background jobs
[carrierwave](https://github.com/carrierwaveuploader/carrierwave) provides a way to upload files. This requires installing image magic which most people do through brew, although there is a standalone package available for mac.
[pundit](https://github.com/varvet/pundit)/[devise](https://github.com/plataformatec/devise)/[doorkeeper](https://github.com/doorkeeper-gem/doorkeeper) are useful for managing authorizations and authentications
[slim](https://github.com/slim-template/slim) is a template language for Ruby
[rabble](https://github.com/ewiener/rabble) is a Ruby implementation of Scrabble, which attempts to maximize word score rather than optimizing for all potential letters it might draw. I thought this was supposed to be a templating language…
[Enumberable](https://ruby-doc.org/core-2.5.3/Enumerable.html) provides collection classes with several traversal and searching methods, and with the ability to sort.
