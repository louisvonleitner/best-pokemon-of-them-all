*2 Dec 2025*

*This project was created as a midterm project for Tohoku University's Intercultural Data Storytelling Course. The project's focus was on making nice visualizations and finding a good story to tell from a simple dataset. I found it interesting and so want to share it.*

# Which one is the best Pokemon of them all?

If you have ever played a Pokemon game, or even multiple, it is likely that you have wondered which one, of the many, is the best Pokemon. 
This question is quite obvious, because all the game is about is collecting better and better Pokemon to increase your battle strength, to eventually be so strong that you can defeat the bad guys who want to abuse Pokemon to gain power.

As I am a data scientist, this question is exciting, because it can be answered very precisely just from looking at all the available data.

So let us dive straight into it!

## What is a good Pokemon?
A good Pokemon has many qualities. Among others, there are its Battle Points, divided into different skills. But what can really give a Pokemon a big advantage in a fight, even if it has less Battle Points than the opposing Pokemon is attacking effectively and being attacked ineffectively. Even with a very high attack score of Battle Points, an attacker deals only mediocre damage (0.5x) if it is ineffective against the attacked Pokemon's PokeType. Vice versa, if a Pokemon attacks effectively, even with a low attack score of Battle Points, it can deal a lot more damage (2x).

So, one could say that better Pokemon are more likely to face PokeTypes in a fight that are ineffective against it and which it attacks effectively itself. To measure this "more likely", we give a definition of the PokeType likelihood:

*The likelihood of a Pokemon facing a Pokemon of PokeType $T$ is the sum of catch rates of all Pokemon of that PokeType*. 

In a formula, this is:

$$\textit{PokeType likelihood} = \sum_{p \in T} c_p$$, where $T$ is the set of Pokemon of PokeType $T$ and $p \in T$ signifies that $p$ is a Pokemon of said type. Further, $c_p := $ Catchrate of Pokemon $p$.

We here assume that the probability of encountering a Pokemon is proportional to its catch rate. This assumption is intuitive as more rare Pokemon are usually have lower catch rates. The PokeType likelihood is thus a weighted sum over the set of all Pokemon of this PokeType. The weights being the catch rates.

(We will conduct the following data analysis on a dataset of all Pokemon in the Pokeverse, from Generations 1 to 6)

## What PokeTypes are good at what?
<img width="3560" height="3543" alt="qualities of poketypes" src="https://github.com/user-attachments/assets/9f4a014b-a929-41c5-927b-f2dd7127a803" />
