# D795 — Applied Algorithms and Reasoning

**Course 3 of 10** · Apr 23 – 28, 2026 · 1 performance task · 2 textbooks

**Time:** 6 calendar days · ~13 hours on WGU work · ~13 hours of outside courses 

**How it went:** My fastest course. About as much time went into outside courses on Big O, data structures, and Python as into the task itself. That outside work is what made the task quick.

## In one line

I built two versions of an ambulance-dispatch router, one using Dijkstra and one using A*. I benchmarked them and explained why the difference was noise.

## What the course covers

Designing, analyzing, and optimizing algorithms for real problems. It covers Big O and asymptotic notation, data structures, searching and sorting, greedy and dynamic programming, benchmarking and profiling, and testing.

## What I did

- **Built a Python command-line dispatch system.** It reads four CSV files (calls, call priorities, a road network, ambulance locations), sorts calls by urgency, sends the fastest ambulance to each call, and logs every decision.
- **Modeled the road network as a graph.** The network became an adjacency list: a `dict` of node → list of `(neighbor, cost)` tuples. Cost = travel time + traffic delay.
- **Used a stable sort for triage.** Python's Timsort is stable, so calls with the same priority keep their arrival order. That's the right behavior for a 911 queue.
- **Prototype 1: Dijkstra.** It uses a min-heap priority queue (`heapq`) and is guaranteed optimal when edge weights are non-negative.
- **Prototype 2: A\*.** Same interface, same everything else. Only the routing function changed. With no GPS coordinates in the data, I used a constant admissible heuristic.
- **Benchmarked both.** I ran each 10 times, timed only the routing calls (300 route evaluations per run), and compared averages and ranges.
- **Reported the result honestly.** A* averaged ~2% faster, but that's inside measurement noise on a 7-node graph. A constant heuristic gives A* almost nothing to work with. The real win needs coordinates and a Euclidean-distance heuristic.
- **Used Git.** Two prototypes on a working branch in GitLab, one commit per prototype.

## Skills used

`Python` `heapq` `csv.DictReader` `graph algorithms` `Dijkstra` `A*` `admissible heuristics` `Big O` `benchmarking` `Git`

## Complexity, in brief

| | Dijkstra | A* |
|---|---|---|
| Time | O((V + E) log V) | O((V + E) log V) worst case |
| Space | O(V + E) | O(V + E) |
| When it wins | No domain knowledge needed | Good heuristic available (coordinates) |

## What I'd do differently

- **Time with `time.perf_counter()`, not `time.time()`.** `perf_counter` is built for short intervals. At ~1 ms totals, timer resolution matters.
- **Run more trials and drop warm-up runs.** Report median and spread, not just the mean.
- **Prove the heuristic is admissible.** A constant h = 1 is admissible only if every remaining path costs at least 1. I'd check the minimum edge cost in code.
- **Store the path once, not in every heap entry.** A parent-pointer dictionary uses less memory than carrying a full path list in each heap item.

## Key ideas worth knowing

- Big O, Big Omega, Big Theta; dominant terms; amortized analysis
- Stacks (LIFO), queues (FIFO), priority queues and binary heaps
- Hash tables: hash functions, load factor, chaining vs. open addressing
- Trees: BST, AVL, red-black, B-trees, tries
- Greedy algorithms, dynamic programming (memoization, optimal substructure), divide and conquer
- Heuristics, approximation algorithms, technical debt

## Books

### *Algorithm Design and Applications* (zyBook, WGU custom edition)
**zyBooks** · 2024 · zyBooks / Wiley

**What's in it:** algorithm analysis, Big O, amortization, data structures (stacks, queues, lists, trees, heaps, hash tables), recursion, greedy, dynamic programming, and randomized algorithms. Interactive, with a short Python primer.

**Thoughts:** This book is interactive and if you go through the entire thing it could potentially teach you from zero to hero in Python and everything you need to know. There are interactive quizzes and problems in it. I liked this book quite a bit. I only skimmed it but if you're an absolute DSA and Python beginner it's a great resource.

### *Advanced Data Structures and Algorithms*
**A. Abirami, R. L. Priya** · 2023 · BPB Publications

**What's in it:** analysis of algorithms, advanced data structures (AVL, red-black, B-trees, tries, Huffman coding), divide and conquer, greedy algorithms, dynamic programming and NP-completeness, and string matching (KMP, Rabin-Karp).

**Thoughts:** Short book. Review of DSA. I skimmed and ultimately preferred the same material through more interactive methods. I didn't really use it that much.

## Outside courses I took for this one

About 13 hours finished. Several came from the course reading list, and I finished them a few days after the course ended.

| Course | Platform | Length |
|---|---|---|
| [NumPy Essential Training](#numpy-essential-training) | LinkedIn Learning | 1h 26m |
| [Complete Algorithms Complexity and Big O Notation Course](#complete-algorithms-complexity-and-big-o-notation-course) | Udemy | 2h |
| [Foundations of Algorithmic Thinking with Python](#foundations-of-algorithmic-thinking-with-python) | LinkedIn Learning | 1h 16m |
| [Introduction to Artificial Intelligence](#introduction-to-artificial-intelligence) | LinkedIn Learning | 1h 34m |
| [Python Recursion](#python-recursion) | LinkedIn Learning | 2h 10m |
| [Azure AI Fundamentals (AI-900 prep)](#azure-ai-fundamentals-ai-900-prep) | LinkedIn Learning | 2h |
| [Text Analytics and Predictions with Python](#text-analytics-and-predictions-with-python) | LinkedIn Learning | 35m |
| [Agile Software Development: Legacy Code and Technical Debt](#agile-software-development-legacy-code-and-technical-debt) | LinkedIn Learning | 1h 2m |
| [Intelligent Automation for Project Managers](#intelligent-automation-for-project-managers) | LinkedIn Learning | 47m |
| [Generative AI in Learning and Development](#generative-ai-in-learning-and-development) | LinkedIn Learning | 31m |

### NumPy Essential Training
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=NumPy+Essential+Training) · 1h 26m

**Thoughts:** Great course. I actually combined this with a huge string of DataCamp 4-hour blocks of Python with Numpy and other Data Science libraries. So you can probably add another 40 hours of this topic with adjacent material not listed. If you want NumPy training I recommend DataCamp (free subscription with WGU student status)

### Complete Algorithms Complexity and Big O Notation Course
[Udemy](https://www.udemy.com/courses/search/?q=Complete+Algorithms+Complexity+and+Big+O+Notation+Course) · 2h

**Thoughts:** I hit Big O from a few angles until it made sense when I first learned it. This course was good. It is enough if you take notes. I like to hit the same material from multiple angles but this is good. 

### Foundations of Algorithmic Thinking with Python
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=Foundations+of+Algorithmic+Thinking+with+Python) · 1h 16m

**Thoughts:** Quick overview of the different types of Algorithms. It was okay. Grinding LEETcode in addition would help.

### Introduction to Artificial Intelligence
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=Introduction+to+Artificial+Intelligence) · 1h 34m

**Thoughts:** Quick overview of AI. You will probably want to go a lot more in depth with this later and elsewhere.

### Python Recursion
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=Python+Recursion) · 2h 10m

**Thoughts:** Great course on recursion. The teacher also has a website with interactive things and visuals and games. https://compucademy.net/

### Azure AI Fundamentals (AI-900 prep)
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=Azure+AI+Fundamentals) · 2h

**Thoughts:** Unrelated to this course. More about AI within the Microsoft Azure ecosystem. The book work for this course ultimately led you through a lot of AI material as an introduction but nothing deep.

### Text Analytics and Predictions with Python
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=Text+Analytics+and+Predictions+with+Python) · 35m

**Thoughts:** 35 minute definition of text analytics and predictions. Breeze through it but not huge weight in value.

### Agile Software Development: Legacy Code and Technical Debt
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=Agile+Software+Development+Legacy+Code+and+Technical+Debt) · 1h 2m

**Thoughts:** Not worth your time but quick 2x view is fine for introduction to technical debt and agile.

### Intelligent Automation for Project Managers
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=Intelligent+Automation+for+Project+Managers) · 47m

**Thoughts:** Too shallow for anything useful for a MSCS student.

### Generative AI in Learning and Development
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=Generative+AI+in+Learning+and+Development) · 31m

**Thoughts:** 2x speed this like all of these other short courses for a quick walk through of terminology.

## Public rebuild (planned)

Dijkstra vs. A* on a real road graph (OpenStreetMap via `osmnx`), where A* gets a real geographic heuristic. Same benchmark harness, `perf_counter`, and plots of nodes expanded vs. graph size. It will go in `rebuilds/` when it's done.

These rebuilds are low priority. The idea here is to practice this before the course. But the course itself is the practice if you're already in the term. If not, learn algorithms and even copy and paste established ones into your code and try them out. 
