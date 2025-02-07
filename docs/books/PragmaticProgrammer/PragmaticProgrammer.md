# The Pragmatic Programmer 
author
year

## Chapter 01: A Pragmatic Philosophy

### Topic 01: It's Your Life
You own it. You run it. You create it. 
You have Agency. If you jobs sucks, try to fix it. If you cannot, or they won't let you, move on. 

### Topic 02: The Cat Ate my Source Code
The greatest weakness of all is fear of appearing weak
- take resposnibility for you action
- your team needs to be able to trusted and rely on you
    - and you on them 
- healthy communication is built on trust

Provide options, not excuses
- instead of saying what cannot be done. say what can be done

### Topic 03: Software Entropy
when disorder increases in software, it is call technical debt

1 broken window, left un-repaired for a length of time instills the sense of abandonment. eventually, it becomes a reality. Don't live with broken windows
- bad designs, wrong decisions, poor code

First, do no harm
- don't cause collateral damage
- if code is bad, do not follow suit

### Topic 04: Stone Soup and Boiled Frogs
Soldiers are the catalyst, bringing the village together to build something none could do alone

Be the catalyst for change
- do what you can, show it to peeps, let them marvel and suggest enhancements

Remember the big picture
- constantly review what is happening around you

### Topic 05: GOod enough Software
Nothing will be perfect
- write software good enough for your users, and future maintainers
- it will make you more productive

Involve your users in the Trade-Off
- how good do they want it to be? 

make quality a requirements issue 

Know when to stop
- don't over embellish or overrefine.
- move on and let code run for a bit

### Topic 06: Your Knowledge Portfolio
KNowledge and experience are your most important assets
- but they are expiring
- knowledge becomes out of date

Keep a knowledge Portfolio
1. invest regularly
2. Diversify is key to long term success
3. Balance between conservative and high risk investments
4. buy low, sell high (learning emerging techs before they are popular)
5. review and rebalance

Goals
- learn a new languages every year
- read a tech book every month
- Read nontech books
- Take classes
- Participate ion local meet ups 
- experiment w/ different envs
- stay current

Critically analyze what you read and hear
- Ask 5 whys (ask why 5 times)
- Who does this benefit? 
- WHat is the context
- WHen and where would this work
- Why is this a problem? 

### Topic 07: Communicate
English is jsut another programming language
- Know your audience
- KNow what you want to say, outline
- CHoose you moment, not friday at 6pm
- Choose a style, just the facts? hand holding?
- Make it look good
- Involve you audience
- Be a listener
- Get back to people

It is both what you say and how you say it

Build Documentation In, Don't Bolt it on

## Chapter 02: A Pragmatic Approach

### Topic 08: The Essence of Good Design
Good design is easier to change than Bad design
- ETC: Easier to chage
    - Decoupling is ETC
    - Single responsibility is ETC

ETC is value not a rule

### Topic 09: DRY - the Evils of Duplication
Don't Repeat Yourself
- every piece of knowledge must have a single unambiguous, authoritative representation within a system
- More than code
    - Docs
    - intent
    - Data

Make it easy to Reuse

### Topic 10: Orthogonality
2 lines are orthogonal if they meet at right angles.
- In computing, it means independence or decoupling
- changes to 1 thing do not impact the changes to another thing
    - DB is orthogonal to the user interface

Eliminate effects between unrelated things
Benefits
- Gain Productivity
- Reduce Risk 

Design things in layers
![alt text](image.png)

Don't rely on the properties of things you cannot control

Be careful to preserve optionality when introducing 3rd party toolkits and libs

Coding
- Write shy code: do not reveal anything unnecessary to other modules
- Avoid Global Data
- Avoid similar functions

Orthogonal systems are easier to test

same for docs; be able to change appearance without changing content.

### Topic 11: Reversibility

Nothing is forever
There are no final decisions, so make things easier to change
- small components instead of monoliths
- hide 3rd party API behind an abstraction layer

Forgo following fads

### Topic 12: Tracer Bullets
In code, we look for something that gets us from a requirement to some aspect of the final system quickly, visibly and repeatably
- Look for important requirements that define the system
- look for areas where you have doubts and the biggest risks

For example, ths system has 5 architecture layers and we have concerns about how they'd integrate, so we look for a simple feature that will exercise them together
![alt text](image-1.png)

Tracer code is not meant to be disposable

Advantages
- Users get to see something early
- Devs build a structure to work in
- You have an integration platform
- You have something to demonstrate
- You have a better feel for the process

Tracers may miss

Tracer code != prototyping
- prototyping you are aiming to explore a specific aspect of the final system. You will kludge to see that aspect, and if it works, throw it away and do it properly
    - disposable, reconn
- tracer shows how the app as a whole hangs together
    - lean but complete

### Topic 13: Prototypes and Post-it Notes


### Topic 14:

### Topic 15:

### Topic 16:

### Topic 17:

### Topic 18:

### Topic 19:

### Topic 20:

### Topic 21:

### Topic 22:

### Topic 23:

### Topic 24:

## Chapter 03: The Basic Tools

## Chapter 04: Pragmatic Paranoia

## Chapter 05: Bend, or Break

## Chapter 06: Concurrency

## Chapter 07: While You are Coding

## Chapter 08: Before the Project

## Chapter 09: Pragmatic Projects

## Chapter 10: 


