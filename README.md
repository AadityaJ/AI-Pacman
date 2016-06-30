Smart-Pacman
===============
### Intro
A Python based AI capable of playing various versions of the classic game of Pacman . The AI uses **Q-Learning and value iteration** to obtain the heuristical best policy for a given **Markov Decision Process** . The AI is first tested on an easier layout of **Gridworld (from class)** and then applied on simulated bot controller **(Crawler)** and **Pacman** . It was done in the summers of 2016 to understand reinforcement learning.
### Layouts
The software consists of 4 layouts :
* smallGrid (simple layout with 2 pac-dots and 1 ghost)
* smallClassic (complex layout with many pac-dots and 2 ghosts)
* mediumGrid  (large simple layout with 3 pac-dots and 1 ghosts)
* mediumClassic (large complex layout with many pac-dots and 2 ghosts)

An example for MediumClassic grid is :
![Animated gif pacman game](http://ai.berkeley.edu/images/pacman_game.gif)

### Results and Troubleshooting
The default parameters are __epsilon=0.1,alpha=0.3,gamma=0.7__ . Initial understanding of the AI was that *the MDP state is the exact board configuration facing Pacman, with the now complex transitions describing an entire ply of change to that state. The intermediate game configurations in which Pacman has moved but the ghosts have not replied are not MDP states, but are bundled in to the transitions.* This configuration worked well for smallGrid where the accuracy after 2000 training games became about 100% but did not succeed for larger layouts. This was because *each board configuration is a separate state with separate Q-values. It has no way to generalize that running into a ghost is bad for all positions. Obviously, this approach will not scale.* This was removed by implementing __approximate Q-Learning__ which learns weights for features of states, where many states might share the same features. This improved the performance on larger layouts from about 0% on previously to about 90% .  

### Downloading and Running 
To download the code :
```
$git clone https://github.com/AadityaJ/Smart-Pacman
```
Then to run :
```
$cd Smart-Pacman
$python pacman.py -p PacmanQAgent -x 2000 -n 2010 -l smallGrid
```
This will run a smallGrid layout with first 2000 training sets and the show 10 test sets . To alter parameter use __-a__ option like 

```-a epsilon=0.1,alpha=0.3,gamma=0.7```

To run Higher layouts 
```
$python pacman.py -p ApproximateQAgent -a extractor=SimpleExtractor -x 50 -n 60 -l mediumClassic 
```
This will train on a dataset of 50 using SimpleExtractor class and then show & run 10 test sets .

### Contribute

To Contribute feel free to Fork the code . To create your own branch do :
```
$ git checkout -b [name_of_your_new_branch]
```
Anyone who wishes to send a pull request please contact :
* Aaditya Jamuar ([@AadityaJ](https://github.com/AadityaJ))





