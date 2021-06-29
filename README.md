# Qubit-ion-mapping

## Compiling
```
g++ -o optimizer optimizer.cpp
```

## Command

Linux/Mac OS X
```
./optimizer input.txt T
```
where `input.txt` stores the input data, and `T` is a real number such that the program stops after `T` seconds.

## Input Format

The first line is an integer `n`, which corresponds to the number of ions.

The following `n` lines is the cost matrix. In each line there should be `n` real numbers.

In the next line, there is an integer `m`, the number of qubits.

In the following line, there are `m` integers with values `0` or `1`. The `i`-th number is `0` only if it is a data qubit and `1` only if it is an ancilla.


In the next line, there is an integer `p`,  the number of edges in the connectivity graph.

Finally, the following `p` lines provide the information of the edges. Each line consists of three numbers `u`, `v` and `k`, which represents that there are `k` two-qubit gates between the qubit `u` and `v`.

Note that the ions are labeled from `0` to `n-1`, while the qubits are labeled from `0` to `m-1`.

## Sample Input

`input.txt`:

```
13

0.0000000000000	0.0865298239060	0.0978134578280	0.0830354840215	0.0814779760561	0.0874596003704	0.1082075474848	0.0814140195096	0.0811562831130	0.0839677305892	0.0788299040583	0.0929799163358	0.0729723890422
0.0865298239060	0.0000000000000	0.0846463468898	0.0880196247393	0.0836443246824	0.0940657792900	0.1129583066338	0.0839021237462	0.1106280799506	0.0794089631333	0.1164736274295	0.0763636326096	0.0929799163358
0.0978134578280	0.0846463468898	0.0000000000000	0.0895171409019	0.1021776685834	0.0977839726503	0.1230426538579	0.1282611181414	0.0881625712420	0.1036945456063	0.0847001107418	0.1164736274295	0.0788299040583
0.0830354840215	0.0880196247393	0.0895171409019	0.0000000000000	0.0949483409265	0.0968403908296	0.1223417665486	0.0954719278792	0.1185730735534	0.0826368411558	0.1036945456063	0.0794089631333	0.0839677305892
0.0814779760561	0.0836443246824	0.1021776685834	0.0949483409265	0.0000000000000	0.0996598385523	0.1119004532412	0.1251402833627	0.0916404692985	0.1185730735534	0.0881625712420	0.1106280799506	0.0811562831130
0.0874596003704	0.0940657792900	0.0977839726503	0.0968403908296	0.0996598385523	0.0000000000000	0.1282436757633	0.0907396991131	0.1251402833627	0.0954719278792	0.1282611181414	0.0839021237462	0.0814140195096
0.1082075474848	0.1129583066338	0.1230426538579	0.1223417665486	0.1119004532412	0.1282436757633	0.0000000000000	0.1282436757633	0.1119004532412	0.1223417665486	0.1230426538579	0.1129583066338	0.1082075474848
0.0814140195096	0.0839021237462	0.1282611181414	0.0954719278792	0.1251402833627	0.0907396991131	0.1282436757633	0.0000000000000	0.0996598385523	0.0968403908296	0.0977839726503	0.0940657792900	0.0874596003704
0.0811562831130	0.1106280799506	0.0881625712420	0.1185730735534	0.0916404692985	0.1251402833627	0.1119004532412	0.0996598385523	0.0000000000000	0.0949483409265	0.1021776685834	0.0836443246824	0.0814779760561
0.0839677305892	0.0794089631333	0.1036945456063	0.0826368411558	0.1185730735534	0.0954719278792	0.1223417665486	0.0968403908296	0.0949483409265	0.0000000000000	0.0895171409019	0.0880196247393	0.0830354840215
0.0788299040583	0.1164736274295	0.0847001107418	0.1036945456063	0.0881625712420	0.1282611181414	0.1230426538579	0.0977839726503	0.1021776685834	0.0895171409019	0.0000000000000	0.0846463468898	0.0978134578280
0.0929799163358	0.0763636326096	0.1164736274295	0.0794089631333	0.1106280799506	0.0839021237462	0.1129583066338	0.0940657792900	0.0836443246824	0.0880196247393	0.0846463468898	0.0000000000000	0.0865298239060
0.0729723890422	0.0929799163358	0.0788299040583	0.0839677305892	0.0811562831130	0.0814140195096	0.1082075474848	0.0874596003704	0.0814779760561	0.0830354840215	0.0978134578280	0.0865298239060	0.0000000000000

8
0 0 0 0 1 1 1 1

13
0 1 1
0 2 1
0 3 1
0 4 1
0 5 1
0 6 1
0 7 1
1 2 1
1 3 1 
1 4 1
1 5 1
1 6 1
1 7 1
```

## Output Format

The first line of the output is the optimal total cost (I assume that the total cost is the sum of the cost of each gate).

The second line consists of `m` numbers, the `i`-th number is the ion index of qubit `i`.

## Sample Output

```
1.086696
0 1 4 3 7 9 11 12 
```

