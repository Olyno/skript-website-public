# Loops

This tutorial is mostly for those of you who do not do any programming outside of Skript. It explains the concept of loops, as well as examples of how the syntax looks in Skript.

## <a href="#what_loops_are">#</a> What loops are?

A loop is a bit of code that keeps repeating itself (aka looping) until a certain condition is false. See this image For a visual representation of how this works.

The condition isn't very obvious in most of the loops Skript provides.

<pre class="skript-code">
loop 10 times:
	broadcast "Hi"
</pre>

This code simply runs (or loops) 10 times. So where's the condition? There is an expression called loop-number that holds the number of times the loop has run (starts with 1) The condition is: if loop-number is greater than 10. After the loop runs for the tenth time, loop-number becomes 11 and the condition becomes false, and so the code moves on past the loop.

Loops simply repeat the code they are given. However, there can be slight differences each time. For example, the loop-number expression is a different number each iteration (an iteration is one time of running the loop code. The previous example would have 10 iterations). So what would happen if we broadcasted that number?

<pre class="skript-code">
loop 10 times:
	broadcast "%loop-number%"
</pre>
			
The output would be:
1
2
3
4
5
6
7
8
9
10

As you can see, the loop did something slightly different in each of it's iterations. 
Now let's have an example with players:

<pre class="skript-code">
loop all players:
	if {var::%loop-player%} is true:
		send "You are true!" to loop-player
	else:
		send "You are not true!" to loop-player
</pre>

For this example, let's say there are 3 players: player1, player2, and player3. 
The loop starts with player1, checks the variable, and sends a message depending on the outcome. Then it does the same with player2 and player3. Now the loop is out of players, and continues on with any code after the loop. If {var.player1} was true and {var.player2} was false, player1 would get the true message and player2 would get the false message. This is the main advantage of loops. They allow you to handle each object separately instead of all exactly the same.

## <a href="#looping_list_variables">#</a> Looping List Variables

List variables have the capability to hold many values. This means that you can loop through them! This is explained a bit more above in the Variable explanation.

## <a href="#while_loops">#</a> While Loops

While loops look much closer to that diagram I posted above. While other kinds of loops go through a specified amount of objects before running out, a while loop could potentially run on forever. Just like other loops, this will keep iterating until the condition is false. Make sure to add a wait 1 tick into the code or else the server will crash from the constant while loop.

<pre class="skript-code">
while {var} is true:
	strike lightning at player
	chance of 10%:
		set {var} to false
</pre>

In this case the loop will keep running and striking the player with lightning with only a 10% chance of stopping each time. Any condition you can use with an if statement, you can use for a while loop.

Hopefully this clears up some of the confusion around loops in Skript. You can post in the help forum, or send me a PM (LimeGlass) if you have any questions, or need some more explanation about loops.