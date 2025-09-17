<h1>ExpNo 5 : Implement Simple Hill Climbing Algorithm</h1> 
<h3>Name:  Preethi S         </h3>
<h3>Register Number:  212223230157          </h3>
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
<li>Loop until a solution is found or there are no new operators left to be applied in current state:
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


## Program:


```import random
import string

TARGET = "Artificial Intelligence"
CHARS = string.ascii_letters + " .,!?'"  # allowed characters
MAX_ITERATIONS = 100000

def fitness(current):
    return sum(1 for c1, c2 in zip(current, TARGET) if c1 != c2)

def random_string(length):
    return ''.join(random.choice(CHARS) for _ in range(length))

def hill_climbing():
    current = random_string(len(TARGET))
    current_score = fitness(current)
    iterations = 0

    print(f"Score: {current_score} Solution : {current}")

    while current_score > 0 and iterations < MAX_ITERATIONS:
        iterations += 1
        # Generate a neighbor by mutating one character
        i = random.randint(0, len(TARGET) - 1)
        new_char = random.choice(CHARS)
        neighbor = current[:i] + new_char + current[i+1:]
        neighbor_score = fitness(neighbor)

        # If improvement, accept neighbor
        if neighbor_score < current_score:
            current = neighbor
            current_score = neighbor_score
            print(f"Score: {current_score} Solution : {current}")

    return current, current_score, iterations

if __name__ == "__main__":
    result, score, steps = hill_climbing()
    print("\nFinal Result:")
    print(f"Score: {score} Solution : {result} in {steps} iterations")

```

## Output:

<img width="527" height="464" alt="image" src="https://github.com/user-attachments/assets/9a89b23d-a1b0-421b-a73e-91e1a15b5b94" />


## Result : 

Thus the Hill Climbing Algorithm has been verified successfully.
