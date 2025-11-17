<h1>ExpNo 5 : Implement Simple Hill Climbing Algorithm</h1> 
<h3>Name:SANJEEV R      </h3>
<h3>Register Number: 212224060235         </h3>
<H3>Aim:</H3>
<p>Implement Simple Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration </p>
<h2> Theory: </h2>
<p>Hill climbing is a variant of Generate and test in which feedback from test procedure is used to help the generator decide which direction to move in search space.
Feedback is provided in terms of heuristic function
</p>

<h2>Algorithm:</h2>
<p>
<ol>
 <li> Evaluate the initial state.If it is a goal state then return it and quit. Otherwise, continue with initial state as current state.</li> 
<li>Loop until a solution is found or there are no new operators left to be applied in curreant state:
<ul><li>Select an operator that has not yet been applied to the current state and apply it to produce a new state</li>
<li>Evaluate the new state:
  <ul>
<li>if it is a goal state, then return it and quit</li>
<li>if it is not a goal state but better than current state then make new state as current state</li>
<li>if it is not better than current state then continue in the loop</li>
    </ul>
</li>
</ul>
</li>
</ol>

</p>
<hr>
<h3> Steps Applied:</h3>
<h3>Step-1</h3>
<p> Generate Random String of the length equal to the given String</p>
<h3>Step-2</h3>
<p>Mutate the randomized string each character at a time</p>
<h3>Step-3</h3>
<p> Evaluate the fitness function or Heuristic Function</p>
<h3>Step-4:</h3>
<p> Lopp Step -2 and Step-3  until we achieve the score to be Zero to achieve Global Minima.</p>

```
import random
import string

# Function to calculate fitness (number of matching characters)
def fitness(current, target):
    matches = sum(1 for c, t in zip(current, target) if c == t)
    return matches

# Function to generate a random string of same length as target
def random_string(length):
    return ''.join(random.choice(string.ascii_uppercase + ' ') for _ in range(length))

# Function to mutate one random character
def mutate(current):
    index = random.randint(0, len(current) - 1)
    new_char = random.choice(string.ascii_uppercase + ' ')
    new_string = list(current)
    new_string[index] = new_char
    return ''.join(new_string)

# Simple Hill Climbing Algorithm
def hill_climb(target):
    current = random_string(len(target))
    current_fitness = fitness(current, target)
    print("Initial State:", current, " | Fitness:", current_fitness)

    while True:
        neighbor = mutate(current)
        neighbor_fitness = fitness(neighbor, target)

        # If new state is better, move to it
        if neighbor_fitness > current_fitness:
            current, current_fitness = neighbor, neighbor_fitness
            print("Better State:", current, " | Fitness:", current_fitness)

        # Goal reached
        if current == target:
            print("\nGoal State Reached:", current)
            break

# Example execution
target_string = "HELLO AI"
hill_climb(target_string)
```
<hr>
<h2>Sample Input and Output</h2>
<h2>Sample String:</h2> Artificial Intelligence
<h2>Output:</h2>
Score: 643  Solution :  8RzF:oG ]%;CPORRMe!zGvk<br>
Score: 609  Solution :  8RzF:oG ]%;CPqRRMe!zGvk<br>
Score: 604  Solution :  8RzF:oG ]%;CPqRRMe!zGqk<br>
Score: 594  Solution :  8RzF:oG ]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
....................................................<br>
..................................................<br>
................................................<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 0  Solution :  Artificial Intelligence<br>

# Result:
Therefore, Simple Hill Climbing Algorithm is implemented and a String by Mutating a Single Character at each iteration is generated.
