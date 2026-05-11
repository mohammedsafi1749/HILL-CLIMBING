<h1>ExpNo 5 : Implement Simple Hill Climbing Algorithm</h1> 
<h3>NAME : MOHAMMED SAFI F            </h3>
<h3>REGISTER NUMBER : 212224060156            </h3>
<H3>AIM</H3>
<p>Implement Simple Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration </p>
<h2> THEORY</h2>
<p>Hill climbing is a variant of Generate and test in which feedback from test procedure is used to help the generator decide which direction to move in search space.
Feedback is provided in terms of heuristic function
</p>

<h2>ALGORITHM</h2>
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
<h3> Steps Applied</h3>
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
<h2>Sample Output</h2>
Score: 643  Solution :  8RzF:oG ]%;CPORRMe!zGvk<br>
Score: 609  Solution :  8RzF:oG ]%;CPqRRMe!zGvk<br>
Score: 604  Solution :  8RzF:oG ]%;CPqRRMe!zGqk<br>
Score: 594  Solution :  8RzF:oG ]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
....................................................<br>
..................................................<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 0  Solution :  Artificial Intelligence<br>

### PROGRAM
```python
import random
import string

def fitness(candidate, target):
    return sum(abs(ord(candidate[i]) - ord(target[i])) for i in range(len(target)))

def mutate(parent):
    idx = random.randrange(len(parent))
    new_char = random.choice(string.printable[:95])
    return parent[:idx] + new_char + parent[idx + 1:]

def hill_climb(target):
    current = ''.join(random.choice(string.printable[:95]) for _ in range(len(target)))
    current_score = fitness(current, target)
    while True:
        neighbor = mutate(current)
        neighbor_score = fitness(neighbor, target)
        if neighbor_score <= current_score:
            current, current_score = neighbor, neighbor_score
            print(f"Score: {current_score} Solution : {current}")
        if current_score == 0:
            break
    return current

target_string = "Artificial Intelligence"
solution = hill_climb(target_string)
print("\nFinal Solution:", solution)

```
### OUTPUT
```
Score: 574 Solution : z@cRpCOL^FS[}|GfA}}YA`U
Score: 532 Solution : z@cRpCOL^F)[}|GfA}}YA`U
Score: 504 Solution : z@cRpCOh^F)[}|GfA}}YA`U
Score: 490 Solution : z@cRpCOh^T)[}|GfA}}YA`U
Score: 476 Solution : z@cRpC]h^T)[}|GfA}}YA`U
Score: 465 Solution : z@cRpC]h^T)[j|GfA}}YA`U
Score: 447 Solution : z@cRpC]h^r)[j|GfA}}YA`U
Score: 421 Solution : z@cRpC]h^r)[j|ifA}}YA`U
Score: 416 Solution : u@cRpC]h^r)[j|ifA}}YA`U
Score: 406 Solution : u@cRpC]h^r)[j|ifAs}YA`U
Score: 373 Solution : u@cRpC]h^r)[j|ifAs}Yz`U
Score: 346 Solution : (@cRpC]h^r)[j|ifAs}Yz`U
Score: 332 Solution : (NcRpC]h^r)[j|ifAs}Yz`U
Score: 316 Solution : (NsRpC]h^r)[j|ifAs}Yz`U
Score: 305 Solution : (Ns]pC]h^r)[j|ifAs}Yz`U
Score: 305 Solution : (Ns]pC]h^r)[j|afAs}Yz`U
Score: 299 Solution : (Ns]pC]h^r)[j|afAs}kz`U
Score: 293 Solution : (Ns]pC]h^r)[j|afAs}kh`U
Score: 291 Solution : (Ps]pC]h^r)[j|afAs}kh`U
Score: 258 Solution : (Ps]pC]h^r)[j|afvs}kh`U
Score: 257 Solution : (Ps]pC]h^r)8j|afvs}kh`U
Score: 243 Solution : (Ps]pC]h^r)8j|afvsokh`U
Score: 206 Solution : (Ps]ph]h^r)8j|afvsokh`U
Score: 205 Solution : (Ps]ph]h^r)8j|afvsnkh`U
Score: 171 Solution : (rs]ph]h^r)8j|afvsnkh`U
Score: 160 Solution : (rshph]h^r)8j|afvsnkh`U
Score: 158 Solution : (rshph]h^r)8j|apvsnkh`U
Score: 158 Solution : (rshphih^r)8j|apvsnkh`U
Score: 158 Solution : (rshph]h^r)8j|apvsnkh`U
Score: 154 Solution : (rshph]h^r)8j|apvsnkh`q
Score: 154 Solution : (ruhph]h^r)8j|apvsnkh`q
Score: 153 Solution : (ruhph]h^r)8j|apvsnkh`p
Score: 151 Solution : (ruhph]h^r)8j|cpvsnkh`p
Score: 151 Solution : (rujph]h^r)8j|cpvsnkh`p
Score: 151 Solution : (rujph]h^r)8j|cpvsnkh`p
Score: 151 Solution : (rujph]hdr)8j|cpvsnkh`p
Score: 151 Solution : (rujph]hdr)8j|cpvsnkh`p
Score: 147 Solution : (rujph]hdr)8j|cpvsdkh`p
Score: 142 Solution : (rujph]hdr)Uj|cpvsdkh`p
Score: 142 Solution : Zrujph]hdr)Uj|cpvsdkh`p
Score: 141 Solution : Zrujph]hdr)Tj|cpvsdkh`p
Score: 138 Solution : Zrujph]hdr)Tj|cpvsgkh`p
Score: 137 Solution : Zrujph]hdr)Tj|cpvsg`h`p
Score: 118 Solution : Grujph]hdr)Tj|cpvsg`h`p
Score: 112 Solution : Grujph]hdr)Tjvcpvsg`h`p
Score: 112 Solution : Grujph]hdr)Tjvcpvsg`h`p
Score: 103 Solution : Grujph]hdr)Tjvcpvjg`h`p
Score: 94 Solution : Grujph]hdr)Kjvcpvjg`h`p
Score: 94 Solution : Grujph]hdr)Kjvcpvjg`h`p
Score: 92 Solution : Grujph]hdr)Kjvcpvjg`h`\
Score: 92 Solution : Grujph]hdr)Kjvcpvjg`h`\
Score: 92 Solution : Grujph]hdr)Kjvcpvjg`h`\
Score: 88 Solution : Grujphehdr)Kjvcpvjg`h`\
Score: 84 Solution : Crujphehdr)Kjvcpvjg`h`\
Score: 84 Solution : Crujphehdr)Kjvcpvjg`h`\
Score: 83 Solution : Crujpheh_r)Kjvcpvjg`h`\
Score: 83 Solution : Crujpheh_r)Kjvcpvjg`h`\
Score: 83 Solution : ?rujpheh_r)Kjvcpvjg`h`\
Score: 83 Solution : ?rujphah_r)Kjvcpvjg`h`\
Score: 82 Solution : ?rujphah_q)Kjvcpvjg`h`\
Score: 76 Solution : ?rujjhah_q)Kjvcpvjg`h`\
Score: 75 Solution : ?ruijhah_q)Kjvcpvjg`h`\
Score: 74 Solution : Bruijhah_q)Kjvcpvjg`h`\
Score: 68 Solution : Bruijhah_q)Kjvcphjg`h`\
Score: 68 Solution : Bruijhah_q)Kjvcphjg`h`\
Score: 65 Solution : Bruijhah_q)Kjvcphjggh`\
Score: 64 Solution : Bruijhah_q)Kjvcphjggs`\
Score: 62 Solution : Bruijhah_q)Kjvcphjggs`^
Score: 58 Solution : Bruijhah_m)Kjvcphjggs`^
Score: 58 Solution : Bruijhah_m)Kjvcphjggs`^
Score: 52 Solution : Bruijhah_m)Kjvcphjggs`f
Score: 50 Solution : Bruijhah_m)Ijvcphjggs`f
Score: 49 Solution : Bruijhah_m)Ijvcphjggj`f
Score: 47 Solution : Bruihhah_m)Ijvcphjggj`f
Score: 47 Solution : Bruihhah_m)Ijvcphjggj`f
Score: 47 Solution : Bruidhah_m)Ijvcphjggj`f
Score: 44 Solution : Bruidhah_m)Ijvcpkjggj`f
Score: 42 Solution : Bruidhah_m)Ijvcjkjggj`f
Score: 40 Solution : Bruidhaham)Ijvcjkjggj`f
Score: 36 Solution : Bruidhaham)Ijvcjkjggn`f
Score: 35 Solution : Bruidhaham)Ijvfjkjggn`f
Score: 35 Solution : Bruidhaham)Ijvfjkjggn`f
Score: 35 Solution : Bruidhaham)Ijvfjkjggn`f
Score: 35 Solution : Bruidhaham)Ijvfnkjggn`f
Score: 30 Solution : Bruidhaham$Ijvfnkjggn`f
Score: 30 Solution : Bruidhaham$Ijvfnkjggn`f
Score: 30 Solution : Bruidhaham$Ijvfjkjggn`f
Score: 28 Solution : Bruidhaham$Ijvfjkjggndf
Score: 27 Solution : Aruidhaham$Ijvfjkjggndf
Score: 27 Solution : Aruidhaham$Ijvfnkjggndf
Score: 26 Solution : Aruidhaham$Ijvfnkjgdndf
Score: 26 Solution : Aruidhaham$Ijvfnkjgdndf
Score: 25 Solution : Aruidhaham$Ijvfnkjgdnde
Score: 21 Solution : Aruidhaham$Invfnkjgdnde
Score: 21 Solution : Aruidhaham$Inrfnkjgdnde
Score: 21 Solution : Aruidhaham$Inrfnkjgdnde
Score: 21 Solution : Aruidheham$Inrfnkjgdnde
Score: 20 Solution : Aruidheham$Inufnkjgdnde
Score: 20 Solution : Aruidheham$Inufnkjgdnde
Score: 19 Solution : Aruidhbham$Inufnkjgdnde
Score: 18 Solution : Aruidhbham$Inufnkigdnde
Score: 18 Solution : Aruidhbjam$Inufnkigdnde
Score: 18 Solution : Aruidhbjam$Inufnkigdnde
Score: 18 Solution : Aruihhbjam$Inufnkigdnde
Score: 16 Solution : Aruifhbjam$Inufnkigdnde
Score: 16 Solution : Aruifhbham$Inufnkigdnde
Score: 15 Solution : Aruifhbham$Inufnkigdnce
Score: 15 Solution : Aruifhbham$Inufnkigdnce
Score: 15 Solution : Aruifhbham$Inufnkigdnce
Score: 14 Solution : Aruifhbham$Inufmkigdnce
Score: 13 Solution : Aruifhcham$Inufmkigdnce
Score: 13 Solution : Arsifhcham$Inufmkigdnce
Score: 12 Solution : Arsifhcham$Inuemkigdnce
Score: 12 Solution : Arsifhcham$Inuemkigdnce
Score: 9 Solution : Arsifhcham!Inuemkigdnce
Score: 9 Solution : Arsifhcham!Inuemkigdnce
Score: 9 Solution : Arsifhcham!Inuemkigdnce
Score: 9 Solution : Arsifhcham!Inuemkigdnce
Score: 9 Solution : Arsifhcham!Inuemkigdnce
Score: 9 Solution : Arsifhcham!Insemkigdnce
Score: 9 Solution : Arsifhcham!Insemkigdnce
Score: 9 Solution : Arsifhcham!Insemkigdnce
Score: 9 Solution : Arsifhcham!Insemkigdnce
Score: 9 Solution : Arsifhcham!Insemkigdnce
Score: 9 Solution : Arsifhcham!Insemkigdnce
Score: 8 Solution : Arsifhcham!Insemligdnce
Score: 8 Solution : Arsifhcham!Insemligdnce
Score: 8 Solution : Arsifhcham!Insemligdnce
Score: 8 Solution : Arsifhcham!Insemligdnce
Score: 8 Solution : Arsifhchak!Insemligdnce
Score: 8 Solution : Arsifhchak!Insekligdnce
Score: 7 Solution : Arsifhchak!Inselligdnce
Score: 7 Solution : Arsifhchak!Inselligdnce
Score: 7 Solution : Arsifhchak!Inselligdnce
Score: 7 Solution : Arsifhchak!Inselligdnce
Score: 7 Solution : Arsifjchak!Inselligdnce
Score: 7 Solution : Arsifjchak!Inselligdnce
Score: 7 Solution : Arsifjcham!Inselligdnce
Score: 7 Solution : Arsifjcham!Inselligfnce
Score: 7 Solution : Arsifjcham!Inselligfnce
Score: 7 Solution : Arsifjcham!Inselligfnce
Score: 7 Solution : Arsifjcham!Inselligfnce
Score: 7 Solution : Arsifjcham!Inselligfnce
Score: 6 Solution : Arsifjcham Inselligfnce
Score: 6 Solution : Arsifjcham Inselligfnce
Score: 6 Solution : Arsifjcham Inselligfnce
Score: 6 Solution : Arsifjcham Inselligfnce
Score: 5 Solution : Arsifjcham Intelligfnce
Score: 5 Solution : Arsifjcham Intelligfnce
Score: 5 Solution : Arsifjcham Intelligfnce
Score: 4 Solution : Arsifjciam Intelligfnce
Score: 4 Solution : Arsifjciam Intelligfnce
Score: 4 Solution : Arsifjciam Intelligfnce
Score: 4 Solution : Aruifjciam Intelligfnce
Score: 4 Solution : Aruifjciam Intelligfnce
Score: 3 Solution : Aruifjciam Intelligence
Score: 3 Solution : Aruifjciam Intelligence
Score: 3 Solution : Aruifjciam Intelligence
Score: 3 Solution : Aruifjciam Intelligence
Score: 3 Solution : Aruifhciam Intelligence
Score: 3 Solution : Aruifhciam Intelligence
Score: 3 Solution : Aruifhciam Intelligence
Score: 3 Solution : Aruifhciam Intelligence
Score: 3 Solution : Aruifhciam Intelligence
Score: 3 Solution : Aruifhciam Intelligence
Score: 3 Solution : Arsifhciam Intelligence
Score: 3 Solution : Arsifhciam Intelligence
Score: 3 Solution : Arsifhciam Intelligence
Score: 3 Solution : Arsifhciam Intelligence
Score: 3 Solution : Arsifhciam Intelligence
Score: 3 Solution : Arsifjciam Intelligence
Score: 3 Solution : Arsifjciam Intelligence
Score: 3 Solution : Arsifjciam Intelligence
Score: 3 Solution : Arsifjciam Intelligence
Score: 3 Solution : Arsifjciam Intelligence
Score: 2 Solution : Arsifjcial Intelligence
Score: 2 Solution : Arsifjcial Intelligence
Score: 2 Solution : Arsifjcial Intelligence
Score: 2 Solution : Arsifhcial Intelligence
Score: 2 Solution : Arsifhcial Intelligence
Score: 2 Solution : Arsifhcial Intelligence
Score: 2 Solution : Arsifhcial Intelligence
Score: 2 Solution : Arsifhcial Intelligence
Score: 2 Solution : Aruifhcial Intelligence
Score: 1 Solution : Aruificial Intelligence
Score: 1 Solution : Aruificial Intelligence
Score: 1 Solution : Aruificial Intelligence
Score: 1 Solution : Aruificial Intelligence
Score: 1 Solution : Aruificial Intelligence
Score: 1 Solution : Aruificial Intelligence
Score: 1 Solution : Aruificial Intelligence
Score: 1 Solution : Aruificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 1 Solution : Arsificial Intelligence
Score: 0 Solution : Artificial Intelligence

Final Solution: Artificial Intelligence
```

### RESULT
The Simple Hill Climbing Algorithm was successfully implemented and the target string was generated by mutating one character at each iteration.
