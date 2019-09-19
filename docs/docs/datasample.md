# Sampling the Data

Attempts to sample data into smaller file


## Normal Sampling method

      sample_data = df.sample(n=2,replace="False")    #pandas dataframe sampling?

* n is the sample size
* Without replacement
* *Read entire file, takes too long, more efficient way?*




## Reservoir Sampling

### Algorithm R

      (*
        S has items to sample, R will contain the result
       *)
      ReservoirSample(S[1..n], R[1..k])
        // fill the reservoir array
        for i = 1 to k
            R[i] := S[i]

        // replace elements with gradually decreasing probability
        for i = k+1 to n
          j := random(1, i)   // important: inclusive range put random access
          if j <= k
              R[j] := S[i]

* http://www.cs.umd.edu/~samir/498/vitter.pdf
* Run through list once (O(n) time)
* Creates a reservoir sample size *k*, keeps the first *k* lines of the file, then iterates through the lines until file is all read. At the *i-th* line generate a random number *j* between 1 and *i*, if *j* less than or equal to *k*, the *j-th* line of the reservoir array is replaced with the *i-th* line.
* **random access by kilobytes at a time** implement on C or Java?


### Random Sort with Priority Queue

      (*
        S is a stream of items to sample, R will contain the result
        S.Current returns current item in stream
        S.Next advances stream to next position
        min-priority-queue supports:
          Count -> number of items in priority queue
          Minimum -> returns minimum key value of all items
          Extract-Min() -> Remove the item with min key
          Insert(key, Item) -> Adds item with specified key
       *)
      ReservoirSample(S[1..?], R[1..k])
        H = new min-priority-queue
        while S has data
          r = Random(0,1)
          if H.Count < k
            H.Insert(r, S.Current)
          else
            if H.Minimum < r
              H.Extract-Min()
              H.Insert(r, S.Current)
          S.Next

* Worst case is O(n log n) while best case is O(n)
* Can be extended to weighted sampling?


## Random Sort with Bash

      sort --random-sort | head -n 10000 uq-wireless-locations-w41-2018.jsonl > sample_wl_w41_2018.jsonl
