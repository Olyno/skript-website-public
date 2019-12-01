# Functions

## <a href="#construct_function">#</a> Constructing Your Function

There are two important things to consider when constructing your function, that you should know 
when you make the first line. What are going to be the inputs of the function (the data it receives), 
and what the return (if any) of the function will be (the outputs). So let's make our first function.

<pre class="skript-code">
function myFunction(i: number) :: number:
	set {_i} to {_i} + 1
return {_i}
</pre>

So let's break this down so you know what is happening. First, what does this function do?
This function will take a number and add 1 to it. Yes, you might not need a function to do
this, but let's make it as simple as we can.

<pre class="skript-code">
# First you declare your function name, this can be anything. In this case 'myFunction'
# You will then need to determine your inputs. I want this function to take in a single number
# In the that, I also declare what will be the reference name of the variable, in this case 'i' which can be reference by {_i}
# I then determine my return, in this case a single number. The format is as follows:
#    function %function name%(%variable name%: %variable type%) :: %return type%:
function myFunction(i: number) :: number:
 
	#you simply indent the appropriate amount, spaces or tabs whatever you prefer and put in your code.
	set {_i} to {_i} + 1
 
#if you have a return, you simply return the value, it must match the value type you have specified
return {_i}
</pre>

So, that is probably the most basic function you can do. However, a function is not 
required to make a return (have an output). In most programming languages this is 
called a 'void' which means the executing code will not be looking for a return, 
but instead calls on the function to DO something.

Let's say we want a function that gives players a set of gear.

<pre class="skript-code">
function leathSet(p: player):
	set helmet of {_p} to leather helmet
	set chestplate of {_p} to leather chestplate
	set leggings of {_p} to leather leggings
	set boots of {_p} to leather boots
</pre>

This would give the reference player a full set of leather armor. Modifying 
this makes it easier to give kits and such for instances like KitPVP. You 
could also make a neat little function that lets you dye a full set of armor 
with a simple function.

<pre class="skript-code">
function leatherDye(c: color , p: player):
	#note the comma, this allows us to input multiple values
	dye {_p}'s helmet {_c}
	dye {_p}'s leggings {_c}
	dye {_p}'s chestplate {_c}
	dye {_p}'s boots {_c}
</pre>

## <a href="#calling_your_function">#</a> Calling Your Function

So now that we have covered a few simple ways to construct your function. 
Lets see how we can call them.

Shown is a demonstration of using the functions we have created in the same order as before.

<pre class="skript-code">
set {this.number} to 1
#{this.number} will equal 1 here
set {this.number} to myFunction({this.number})
#{this.number} will equal 2 here
</pre>
The above will call our function that simply adds 1 to our inputted value.

<pre class="skript-code">
command /leatherset:
	trigger:
		leatherSet(player)
</pre>

The above will give the executing player a full set of leather armor.

<pre class="skript-code">
command /leatherset &#60;color>:
	trigger:
		leatherSet(player)
		leatherDye(argument 1 , player)
</pre>

Using the above, and our two leather set functions, we give the player a 
full set of leather armor, and then let them dye it whatever color they inputted.

## <a href="#built_in_functions">#</a> Built in functions

Skript 2.2 has a few simple built in functions. View them <a href="/documentation/functions">here</a>

## <a href="#extra_notes">#</a> Extra notes

That's really all there is to it. Word of advice though, if you can do what you need to do with 
a simple command like the examples, I would personally just use a command. Functions are more 
useful if you are going to be executing the same code over and over from different areas.

Giving the ability for multiple scripts to start a game or use a math function that is unique to 
your server, these are things that functions are great for. I personally use them a lot for 
logging, as my server has many scripters who contribute. By using functions, I ensure that the 
all of the logs look the same with the same data and Formatting provided, without having the 
scripters waste their time writing different log formats over and over.

Functions have the unique ability of being able to be called from any other script regardless 
of location. They do not have to be in the same file as what is calling them.

When a function is changed and it's change is no longer valid for something that is calling it 
(like changing a return from a number to a text), then the caller will use the old version of 
the function until either it is reloaded, or the server is reset.

Skript will not allow to input the wrong values in the wrong slots. This allows you to avoid 
having to check if the parameters are the correct type or not (something you had to do in the 
skQuery Counterparts).