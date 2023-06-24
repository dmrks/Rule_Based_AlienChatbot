# Rule_Based_AlienChatbot

# Alienbot
The 1950s ushered in a slew of UFO sightings and excitement about outer space. Incidentally, the decade also brought about a new idea of artificial intelligence. 
The computer scientist Alan Turing proposed that if a computer was able to fool a human into believing it was human, the computer would be considered “intelligent.”

While your bot may not pass a true Turing test, perhaps it could pass an “E.T.uring” test if you can successfully fool a human into believing that your chatbot is, in fact, an alien.

We’ve added a class called AlienBot to get you started; you’ll be digging into the main chatbot functionality. Take a look at what you have in script.py:

the regex and random libraries are imported
a tuple of negative responses (you can add more!)
a tuple of commands for a user to exit the program
a tuple of random starter questions an alien might ask (feel free to add more)
a tuple of dictionaries called alienbabble with the chatbot’s main intent-utterance matching pairs — you’ll add to this later!
several methods for core chatbot functionality:
.greet() will greet the user
.make_exit() will check if a user has used an exit command
.chat() will run the program allowing users to chat with the alien you created
.match_reply() will match the response pairs in alienbabble for you
several methods associated with user intents
.describe_planet_intent() will include responses about the alien’s planet
.answer_why_intent() will include responses for why the alien is visiting
.cubed_intent() is a method that returns the cube of a number, because these aliens are very good at math
.no_match_intent() will respond with something general when none of the other intents are matched
As you add to the chatbot, you can check the functionality by:



# Greeting the user
1.
The first step in any chatbot program is to greet the user. Over the next few steps, you will call the .greet() method and program the chatbot to welcome a user.

Inside .greet(), ask the user for their name with an input method and assign it to a self.name variable.


2.
Below the previous input, create a will_help variable and assign it the user’s response to the following string:

"Hi NAME, I'm Etcetera. I'm not from this planet. Will you help me learn about your planet? "
In this example, NAME is the value saved to self.name.

3.
Next, we want to see if the user even wants to chat. Create a conditional that checks if the will_help response is in self.negative_responses. If it is, then we need to:

Print a goodbye statement to the terminal (we suggest “Ok, have a nice Earth day!”)
Return from the function


4.
If the user didn’t respond in the negative, we know the user is interested in chatting.
Outside the if statement, call self.chat(). The .chat() method will be responsible for handling the conversation.

6.
Let’s test .greet() out!

At the bottom of script.py, outside of the AlienBot class, create an instance of the AlienBot class. Then call the .greet() method.

In the terminal enter python3 script.py. See if you can have the following two conversations:

Yes, you do want to have a conversation:

Hello there, what's your name? Codecademy 
Hi Codecademy, I'm Etcetera. I'm not from thisplanet. Will you help me learn about your planet? yes
No, you do not want to have a conversation:

Hello there, what's your name? Codecademy 
Hi Codecademy, I'm Etcetera. I'm not from this planet. Will you help me learn about your planet? no
Ok, have a nice Earth day!


# Handle the conversation
6.
In the next few tasks, you will create a loop that continues the conversation until the user replies with an exit command.

Let’s start by asking the user a random question in the .chat() method. You can do this with the following line of code:

reply = input(random.choice(self.random_questions)).lower()
This code will randomly select a question from random_questions, ask it to the user, then save the user’s response.

7.
Before setting up the loop in .chat(), let’s set up a stop condition for the loop.

Inside of the .make_exit() method, you will check if the user wants to stop talking to the chatbot.

First, use a for loop to iterate over the words in self.exit_commands.



8.
Inside the for loop, create an if statement to check if the current exit command is in reply.

Inside the if statement, print “Ok, have a nice Earth day!” and then return True.



9.
Jump back inside the .chat() method.

Below where you set reply, create a while loop that continues for as long as the .make_exit() method returns False. Include the following features in this loop:

The .make_exit() method should accept the user’s response, saved to the reply variable.
Inside the loop, create an input() function that asks the user “How are you?” and saves the response to reply (we’ll change this later).


10.
Now, let’s try testing your code. Press the Save button, then type python3 script.py.

At this point, you should be able to recreate the following conversation:

Hello there, what's your name? Codecademy
Hi Codecademy, I'm Etcetera. I'm not from this planet. Will you help me learn about your planet? yes
Why are you here? To talk with you
How are you? I'm okay
How are you? I'm okay
How are you? exit
Ok, have a nice Earth day!

# Matching the user's response

11.
Now, we need to setup the functionality to match a user’s response to an intent. Over the next few steps, you will:

Call the self.match_reply() method inside of .chat().
Loop over the intent-regular expression pairs in the alienbabble dictionary.
Check if the user’s response matches a regular expression in the alienbabble dictionary.
Let’s get started. Inside .chat(), replace “How are you? “ with a call to self.match_reply(). (This is still inside input().)

Pass the reply variable into the method.

12.
Inside of .match_reply(), loop over all the items in self.alienbabble. For each item, save the key to a variable called intent and the value to a variable called regex_pattern.



13.
Inside of the for loop, use the regular expression .match() method to check the user’s reply for the regex_pattern. Save the result to a variable called found_match.

At this point, there are no regular expressions in the alienbabble variable. You will add them in a few steps.



# The describe_planet_intent

14.
Over the next several steps, you are going to create a long if-elif-else conditional block to select the corresponding intent when a match is found.

After the line with re.match(), write a conditional statement that checks if a match was found and if the current intent is 'describe_planet_intent'.

Inside the if block, return self.describe_planet_intent().

15.
Next, locate the AlienBot constructor method and add a regular expression to self.alienbabble that matches the 'describle_planet_intent' key.

Write a regular expression that matches the following two statements:

“Can you tell me about your planet?”
“I am interested in your planet.”
The regular expression should not match:

“Why are you here?”
“I think I am the only human who has met you.”
“Can you cube the number 3?”
“Why are you asking me so many questions?”

Stuck? Get a hint
16.
At this point, you can check if your regular expression worked. Run python3 script.py and see if you can get the chatbot to respond with, “Inside .describe_planet_intent()”.

One example may look like:

Hello there, what's your name? Codecademy
Hi Codecademy, I'm Etcetera. I'm not from this planet. Will you help me learn about your planet? yes
What do you consume for sustenance? tell me about your planet
Inside describe_planet_intent

17.
Inside .describe_planet_intent(), we want to answer with a response about the alien’s planet. Delete the current return statement.

In place, create a tuple called responses with the following two strings:

"My planet is a utopia of diverse organisms and species. "
"I am from Opidipus, the capital of the Wayward Galaxies. "

18.
Next, return one of the strings in the responses tuple. You can randomly select a response using the following syntax:

random.choice(responses)

# The answer_why_intent

19.
Under the if block, add an elif that checks if a match was found and if the current intent is 'answer_why_intent'.

Inside the elif block return self.answer_why_intent().

20.
Next, you need to add a regular expression to self.alienbabble that matches the 'answer_why_intent' key.

Write a regular expression that matches the following two statements:

“Why are you here?”
“Why are you asking me so many questions?”
The regular expression should not match:

“Can you cube the number 3?”
“Can you tell me about your planet?”
“I think I am the only human who has met you.”
“I am interested in your planet.”

21.
At this point, you can check if your regular expression worked. Run python3 script.py and see if you can get the chatbot to respond with, “Inside .answer_why_intent()”.

One example may look like:

Hello there, what's your name? Codecademy
Hi Codecademy, I'm Etcetera. I'm not from this planet. Will you help me learn about your planet? yes
What do you consume for sustenance? why are you here?
Inside answer_why_intent

22.
Inside .answer_why_intent(), we want to answer with a response about why the alien is visiting. Create a tuple called responses with the following strings:

“I come in peace. “
“I am here to collect data on your planet and its inhabitants. “
“I heard the coffee is good. “

23.
Next, return one of the strings in the responses tuple. You can randomly select a response using the following syntax:

random.choice(responses)

# The cubed_intent

24.
This alien chatbot is also capable of doing some math. Over the next few steps, you will create an intent that takes a user’s input, with a number, and cubes it.

Under the last elif block, add an elif that checks if a match was found and if the current intent is 'cubed_intent'.

Time for some entity recognition.

Inside the elif block return the output from self.cubed_intent(), and pass the first group from found_match as an argument. (This group should have the number the user wants cubed — our entity!)

25.
Next, you need to add a regular expression to self.alienbabble that matches the 'cubed_intent' key.

Write a regular expression that matches the following two statement:

“Can you cube the number 3?”
The regular expression should not match:

“Why are you here?”
“Why are you asking me so many questions?”
“Can you tell me about your planet?”
“I think I am the only human who has met you.”
“I am interested in your planet.”

26.
Let’s check if your regular expression worked. Run python3 script.py and see if you can get the chatbot to respond with, “Inside .answer_why_intent()”.

One example may look like:

Hello there, what's your name? Codecademy
Hi Codecademy, I'm Etcetera. I'm not from this planet. Will you help me learn about your planet? yes
What do you consume for sustenance? can you cube the number 5?
Inside cubed_intent


27.
Inside .cubed_intent(), we need to return the following:

The cube of NUMBER is CUBED_NUMBER. Isn't that cool? "
Follow these steps to set up the above string:

On the first line of the method, use the int function to change the value saved to number to an integer (right now it’s a string).
On the second line, multiply number by itself three times, then save the response to cubed_number.
On the third line return an f-string to respond to the user with the string above.


# Handling responses that don't match an intent

28.
Finally, we need to handle the situation when none of the intents are matched. Under the last elif statement in .match_reply(), add an else.

Inside the else block, return self.no_match_intent().



29.
Inside the method, we want to answer with a response that is applicable to many statements. In this way, we simulate that the chatbot understands what the user is saying despite it not matching any intent.

Create a tuple with the following strings and save it to responses:

“Please tell me more. “
“Tell me more! “
“Why do you say that? “
“I see. Can you elaborate? “
“Interesting. Can you tell me more? “
“I see. How do you think? “
“Why? “
“How do you think I feel when you say that? “

30.
Next, return the response to one of the strings in the responses tuple. You can randomly select a response using the following syntax:

random.choice(responses)
Now try out your AlienBot and see how it does!

# Adding to this chatbot

31.
Great work!

You built a chatbot that simulates a real conversation. 
It’s unlikely that a human would be fooled by the chatbot. 
However, it’s worth mentioning that it can be easily extended by adding conditions and intents to the if-elif-else block.

At this point, you’ve proven that you understand the basic architecture and features of a rule-based chatbot. 
You can build upon these skills with more sophisticated regular matching and response generation. Good luck as you continue developing these skills to create increasingly human-like bots!
