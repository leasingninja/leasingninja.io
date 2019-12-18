# LeasingNinja

WARNING: The LeasingNinja is currently in a state of early alpha. 
I still hope it can already be of some help.

The LeasingNinja is an example how to use Domain-Driven Design --footnote:[We assume that you are familiar with the DDD nomenclature. If not, you may consider reading XXXX first.]--. The idea is to have one domain that is small enough to be grasped easily and big enough to show the different concepts in a real world end-to-end example. There will be different _incarnations_ (i.e. implementations) of the LeasingNinja to show the pros and cons of different styles and solutions. By always using the same domain the details of the various incarnations can be compared easily. Each incarnation is a combination of styles.

We use different styles in: strategic design, implementation of the domain “layer”, programming language and other properties of programming.
Strategic stuff contains big ball of mud versus bounded contexts vs CQRS.
Domain layer: domain model vs anemic domain model vs polluted domain model vs event sourced domain model.
For programming languages the Java version is developed the farthest.
There are also beginning implementations in PHP, Swift, Python.
Other languages will follow eventually.

All incarnations are accessible for everyone under MIT license on GitHub. Some of the better incarnations are meant to serve as blueprint for new projects. The worse incarnations are examples of “how to _not_ do it”. Be warned to use them as blueprints...

## Ok, show me the code!
Not so fast young padawan! The first D in DDD stands for Domain and one important rule is that we have to at least some understanding of the domain before we start coding. (If you want to ignore this warning you can easily jump forward to the incarnations [here](https://www.github.com/leasingninja)).

## So, what is the domain in our example?
Imagine Bob wants to reduce his carbon footprint. He likes to change his dirty gas-powered car for a clean new electric car. Unfortunately he doesn’t have a lot of money. But the salesperson at the car dealer says: “No problem: we buy the car for you and rent it to you for a monthly rate (installment).” This is called _leasing_. “Great” says Bob: “How much will it cost me per month?” The salesperson calculates the monthly rate. Bob signs the contract and the salesperson gives the contract into the risk department. There a risk manager looks at Bob’s credit rating and decides that it is good enough. So he votes the contract with “yes”. Only now the contract becomes legally valid. He informs the salesperson and she gives the keys to Bob.

Phew, this is a lot of text!
Let's model it in a more graphical way – a Domain Story.

<video width="640" height="480" preload autoplay loop>
  <source src="domainstory-leasingninja.mp4" type="video/mp4">
<p>Your browser does not support the video tag and cannot show the domain story.</p>
</video>

In this coarse grained domain story we get an overview about what is happening in our domain.
Also we can see a lot of words of the domain language.
Verbs like _to sign_ and _to vote_, nouns like _contract_, _monthly rate_ and _credit rating_.
All of them will become parts of our ubiquitous language.

Now that we gained some understanding of the domain, let's see if we can find some context boundaries!
Looking at our domain story we can see interaction between the customer and the salesperson in the left part.
And there is work the risk manager is doing on her own.
Considering this we find two bounded contexts:

![The leasing domain with contexts](/domainstory-leasingninja-with-contexts.png)

There is the _Sales_ context and the _Risk Management_ context.
Putting the domain story now away we can paint the context map:

![Context map](/contextmap-leasingninja.png)



## Going deeper into the details
The next step is to drill deeper into the single bounded contexts.
Lets start with "Sales":

xxx

In this finer grained domain story we can find elements for our domain model.
As rule of thumb we take:
* the work objects and make classes out of them
* the activities and turn them into methods/commands
This leads us to the following domain model:
...

## Finally let's write some code
The bounded contexts and domain models we have found can be implemented in different ways.

Currently there are the following implementations:

| Language | Architecture                                        | Technology | Sources |
| -------- | --------------------------------------------------- | ---------- | ------- |
| Java     | Strategic: Bounded Contexts, Tactical: Domain Model | UI: Spring WebMVC, Persistence: Hibernate | <https://github.com/leasingninja/leasingninja-java-boundedcontexts-domainmodel> | 
| PHP      | Strategic: Bounded Contexts, Tactical: Domain Model | | <https://github.com/leasingninja/leasingninja-php-boundedcontexts-domainmodel> |
| Python   | Strategic: Bounded Contexts, Tactical: Domain Model | | <https://github.com/leasingninja/leasingninja-python-boundedcontexts-domainmodel> |
| Swift    | Strategic: Bounded Contexts, Tactical: Domain Model | | <https://github.com/leasingninja/leasingninja-swift-boundedcontexts-domainmodel> |
