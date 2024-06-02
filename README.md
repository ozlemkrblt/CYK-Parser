
# CYK Parser

It is the assignment 4 for Grammar Formalisms course at University of Tuebingen. 
Task is to implement the CYK algorithm for parsing context-free grammars, according to the following pseudocode taken from wikipedia https://en.wikipedia.org/wiki/CYK_algorithm


```
 let the input be a string I consisting of n characters: a1 ... an.
 let the grammar contain r nonterminals R1 ... Rr, with start symbol R1.
 let P[n,n,r] be an array of booleans. Initialize elements of P to false.
 let back[n,n,r] be an array of lists of backpointing triples.
 Initialize all elements of back to the empty list.
 for each s = 1 to n
    for each unit production Rv → as
        set P[1,s,v] = true
 for each l = 2 to n    -- Length of span
    for each s = 1 to n-l+1 -- Start of span
        for each p = 1 to l-1 -- Partition of span
            for each production Ra → Rb Rc
                if P[p,s,b] and P[l-p,s+p,c] then
                    set P[l,s,a] = true,
                    append <p,b,c> to back[l,s,a]
 if P[n,1,1] is true then
     I is member of language
    return back
 else
    return "not a member of language"
```

## Acknowledgements

- You will need to read a grammar file containing a context-free grammar in CNF. Name of the file is *grammar.txt* . It's format is specificed such as: 
```
 S->NP VP
 N->cat
 V -> runs
 ...
```

- The sentences for parsing are contained in another file named *sentences.txt* one sentence per line. Words are already lowercased to match the terminals in the grammar.
```
 cat runs
 cat barks
 ...
```

- The output file is named *Ozlem_Karabulut.txt* and contains 1s and 0s in each line to indicate for each corresponding sentence if it is in the language described by the input grammar.



## Bonus: Visualization

Task is to write some code to generate a dot decription to represent the parse trees for valid sentences. The output should be written to the results irectory in a file called *Ozlem_Karabulut_viz.txt* using the following format:
```
 this is a sentence
 parses: 2
 graph{
 <description for parse #1>
 }
 graph{
 <description for parse #2>
 }
 this is another sentence
 parses: 1
 ...
 ```
## Run Locally

Code is  runnable from a terminal, taking 3 arguments: A grammar file,a file ofs entences to parse and an output directory in which to write the parse results. For my project it can be run from the directory of project such as : 

```bash
   main.py grammar.txt sentences.txt project_dir/PythonCYKParser/
```
