# E2CF: The Entry-Extensible Cuckoo Filter
The entry-extensible cuckoo filter (E2CF) support entry-level extension for dynamic set representation and accelerate the membership query. E2CF utilizes adjacent buckets with sequential physical addresses in a cuckoo filter to extend bucket entries, which avoids many discrete memory accesses in a query. To further make E2CF space and time efficient, we adopt asynchronous extension and fine-grained splitting methods. Experiment results show that compared to existing designs, E2CF reduces the query and insertion time by up to 82% and 29%, respectively.

## How to use?
### Environment
We implement E2CF in a Red Hat Enterprise Linux Server release 6.2 with an Intel 2.60GHz CPU and 64GB RAM, the size of a cache line in the server is 64 bytes, and OpenSSL library environment. 

Install OpenSSL (Please refer to https://www.openssl.org to learn more).

```txt
sudo apt-get install openssl
sudo apt-get install libssl-dev
```
Build and run the example

```txt
make
./test
```


### Configurations
Configurations including false pisitive, item number and dataset path can be costomized in "configuration/config.txt". 

```txt
false positive = 0.02
item number = 100
input file path = input/input100.txt
```

### Results
Results are shown in "output/results.txt", including false positive, fingerprint size, building block number, operation time consumed and etc. In the following is the comparison of DCF and DBF when dealing with 1,000,000 items (including insert/query/delete/compact operation).

Metrics:

item_num: total number inserted/queried/deleted

exp_FPR: the expected false positive rate

actual_FPR: the false positive rate that we measured

actual_BBN: the building block number that we observed

F_size: fingerprint size

space_cost: space overhead of data structure

I_time: insert time

Q_time: query time

D_time: delete time


```
After transform operation time to speed, the results show that compared to existing designs, E2CF reduces the query and insertion time by up to 82% and 29%, respectively.


If you want to know more detailed information, please refer to this paper: The Entry-Extensible Cuckoo Filter


