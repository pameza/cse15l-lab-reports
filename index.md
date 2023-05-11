# Lab 3
In this lab, I explored different options that can be used with `grep` that I think could be very useful in the future. Grep is a very useful tool that scans files in a given directory. It matches the contents of the file to a given string and returns the file names as well as the lines in which the matching string appears. 
For reference, the working directory that was used during these examples was `Users/Paola/Documents/Github/docsearch/`, here is what it looks like:


📂`docsearch`

   📂`technical`
   
      📁 `biomed`
      
       📁`plos`



## Examples of `grep -r`

Input 1:
```
$ grep -r "four monkeys" ./technical/plos/*

```

Output 1:
```
./technical/plos/pmed.0020278.txt:        vaccine was successful in four monkeys, and, thus, is a suitable agent for human study [2].
```
In this example, we use command `grep -r` to search through all the files inside the _plos_ folder and returned the name and line where the `string` "four monkeys" appeared. 


Input 2:
```
$ grep -r "four monkeys" ./technical/biomed/*
```

Output 2:
```

```


In this example, the command `grep -r` searched through the files inside the _biomed_ folder looking for the same string from the previous example but it returned nothing as no files matched the string.


## Examples of `grep -i`

Input 1:
```
$ grep -i "FouR monKeys" ./technical/plos/*

```

Output 1:
```
./technical/plos/pmed.0020278.txt:        vaccine was successful in four monkeys, and, thus, is a suitable agent for human study [2].
```

Normally, the command `grep` performs a case-sensitive search for the given `string`. By using `grep -i`, I can type "FouR monKeys" and the text will still match. We can see that it returned the relative path and line number that matched the `string`.

Input 2:
```
$ grep -i "caesar" ./technical/biomed/*
```

Output 2:

```
./technical/biomed/1471-2288-1-9.txt:          probability of Caesarian section, other forms of
```
Here, we can observe that even though the `string` "caesar" was written in lower-case, there was still a match with the text file's `string` containing the word "Ceasarian".


## Examples of `grep -w`

Input 1:
```
$ grep -w "caesar" ./technical/biomed/*
```

Output 1:
```

```

When we use `grep -w`, the command looks for the given string as is, without letters prior to it or after it. We know that there is a file that contains the word "Caesarian" in this folder, but `grep -w` does not let this match, returning nothing.



Input 2:
```
$ grep -w "Caesarian section" ./technical/biomed/*
```

Output 2:
```
./technical/biomed/1471-2288-1-9.txt:          probability of Caesarian section, other forms of
```

Here, we can note that I wrote a `string` composed of two words, and the output was the relative path of a file containing those words exactly, along the lines the exact `string` appears on.


## Examples of `grep -l`

Input 1:
```
$ grep -l "Caesar" ./technical/biomed/*
```


```
./technical/biomed/1471-2288-1-9.txt
```

Using `grep -l` yields the same result as `grep` but it excludes the lines and line numbers where the given `string` appears.

Input 2:
```
$ grep -l "hypoxia" ./technical/biomed/*
```

Output 2:
```
./technical/biomed/1471-2199-3-10.txt
./technical/biomed/1471-2210-1-8.txt
./technical/biomed/1471-2369-3-1.txt
./technical/biomed/1471-2407-2-8.txt
./technical/biomed/1472-6750-1-11.txt
./technical/biomed/1472-6793-2-8.txt
./technical/biomed/1476-4598-2-25.txt
./technical/biomed/cc1538.txt
./technical/biomed/cc1547.txt
./technical/biomed/cc3.txt
./technical/biomed/cvm-2-6-278.txt
./technical/biomed/rr74.txt
```

The command `grep -l` is most useful when the search will yield many results in order to make the information returned much easier to read. 
Here is what ``` $ grep "hypoxia" ./technical/biomed/* ``` returned, for comparison:
```./technical/biomed/1471-2199-3-10.txt:        Furthermore, USF2 inhibits binding of hypoxia-inducible
./technical/biomed/1471-2210-1-8.txt:        [ 10 11 ] , hypoxia [ 12 ] and a variety of cytokines and
./technical/biomed/1471-2369-3-1.txt:        explanation is tissue hypoxia, which has been suggested to
./technical/biomed/1471-2369-3-1.txt:        cellular stress. Tissue hypoxia therefore remains a
./technical/biomed/1471-2407-2-8.txt:        because wild-type p53 did not repress hypoxia-induced
./technical/biomed/1472-6750-1-11.txt:        vivo, particularly in conditions of hypoxia, such as
./technical/biomed/1472-6793-2-8.txt:          because hypoxia can also induce VEGF mRNA upregulation,
./technical/biomed/1476-4598-2-25.txt:        VEGF is upregulated in response to hypoxia, inducing the
./technical/biomed/cc1538.txt:          pain control, hypertension, hypoxia, and tachycardia.
./technical/biomed/cc1547.txt:        in patients with hepatic hypoxia/reperfusion, obstructive
./technical/biomed/cc3.txt:          the brain's reticular activating system [ 20]. If hypoxia
./technical/biomed/cvm-2-6-278.txt:          hypoxia inducible factor-1 alpha (HIF-1α), is only
./technical/biomed/cvm-2-6-278.txt:          to hypoxia in aged animals [ 28]. A reduced response to
./technical/biomed/cvm-2-6-278.txt:          hypoxia might translate into a weaker angiogenic
./technical/biomed/cvm-2-6-278.txt:        factor; HIF-1α = hypoxia inducible factor-1 alpha; SPECT =
./technical/biomed/rr74.txt:        Severe sustained hypoxia causes pulmonary hypertension
./technical/biomed/rr74.txt:        following severe hypoxia has been reported in rats [ 4, 13,
./technical/biomed/rr74.txt:        the murine lung following hypoxia, with previous reports [
./technical/biomed/rr74.txt:        upregulated following hypoxia and that this may account for
./technical/biomed/rr74.txt:        hypoxia from birth and measured NOS mRNA and protein
./technical/biomed/rr74.txt:          ambient conditions, hypobaric hypoxia (simulating an
./technical/biomed/rr74.txt:          animals that were exposed to hypobaric hypoxia as
./technical/biomed/rr74.txt:          increased following hypoxia, with a trend toward
./technical/biomed/rr74.txt:          1.5-fold following hypoxia as compared with normoxic
./technical/biomed/rr74.txt:          eNOS levels were increased following hypoxia, and the
./technical/biomed/rr74.txt:          not increase following exposure to hypoxia. This was
./technical/biomed/rr74.txt:          pulmonary circulation following hypoxia resulted in
./technical/biomed/rr74.txt:          in animals exposed to hypoxia as compared with sea level
./technical/biomed/rr74.txt:        severe hypoxia-induced pulmonary hypertension. The
./technical/biomed/rr74.txt:        animals exposed to hypoxia during postnatal
./technical/biomed/rr74.txt:        The pulmonary hypertension in mice exposed to hypoxia
./technical/biomed/rr74.txt:        studies of 4 weeks of hypoxia in mature animals [ 9]. The
./technical/biomed/rr74.txt:        due to hypoxia. This is further supported by Tyler 
./technical/biomed/rr74.txt:        which hypoxia increases eNOS expression is poorly
./technical/biomed/rr74.txt:        understood because a hypoxia responsive element has not yet
./technical/biomed/rr74.txt:        transcription factor activator protein-1 during hypoxia may
./technical/biomed/rr74.txt:        hypoxia, the central role of eNOS in protecting against
./technical/biomed/rr74.txt:        hypoxia. In the present study, however, the increase in
./technical/biomed/rr74.txt:        iNOS protein levels in adult mice following hypoxia was
./technical/biomed/rr74.txt:        of hypoxia and inflammation has previously been reported to
./technical/biomed/rr74.txt:        hypoxia and inflammation [ 23]. Others have also reported
./technical/biomed/rr74.txt:        The iNOS promoter contains a hypoxia responsive element,
./technical/biomed/rr74.txt:        and the increase in iNOS transcription in hypoxia may be
./technical/biomed/rr74.txt:        due to the transcription factor hypoxia-inducible factor-1α
./technical/biomed/rr74.txt:        that alterations in redox state during hypoxia may also
./technical/biomed/rr74.txt:        28, 29]. It is not known whether hypoxia interferes with
./technical/biomed/rr74.txt:        hypoxia. We have recently reported that mice deficient in
./technical/biomed/rr74.txt:        hypoxia [ 4], but we did not find an increase in lung nNOS
./technical/biomed/rr74.txt:        in mice following hypoxia. Increased nNOS has been
./technical/biomed/rr74.txt:        other rat vascular beds following hypoxia, other reports
./technical/biomed/rr74.txt:        suggest that the increase in NOS following hypoxia may be
./technical/biomed/rr74.txt:        hypoxia, which correlated with impaired
./technical/biomed/rr74.txt:        in vivo , acute hypoxia caused
./technical/biomed/rr74.txt:        hypoxia in rats, Sato 
./technical/biomed/rr74.txt:        2 . This suggests that hypoxia inhibited
./technical/biomed/rr74.txt:        lung following hypoxia in mice is presently unknown.
./technical/biomed/rr74.txt:        upregulation in the murine lung with severe hypoxia-induced
./technical/biomed/rr74.txt:        hypoxia may lead to more severe pulmonary hypertension than
./technical/biomed/rr74.txt:        that observed in mature mice exposed to hypoxia, and this
```


_For more information follow the instructions in the grep manual by typing `man grep` into the terminal._
