
# dps-laboratory2

To run the test follow the next steps:

- install libgtest-dev and cmake  by runing
	-  `sudo apt-get install libgtest-dev`
	- `sudo apt-get install cmake`
	- `cd /usr/src/gtest`
	- `sudo cmake CMakeLists.txt`
	- `sudo make`
    - `sudo cp lib/libgtest.a /usr/lib`
	- `sudo cp lib/libgtest_main.a  /usr/lib`

- run `g++ tests.cpp -lgtest -lpthread -o executable` to compile the tests

- Finally, to run the test`./executable`

This will run the test in `test.cpp` file


**Explanation of last test (Move UINT_MAX,  12 positions)**
For the last test case where we call the function wrapFunctionShift(UINT_MAX, 12):

We have `UINT_MAX = 1111 1111 1111 1111 1111 1111 1111 1111` and when we move 12 bits we obtain:

    (UINT_MAX << 12)  = 1111 1111 1111 1111 1111 0000 0000 0000 

the overflow cause that we lost some bits by moving to left due the limit of 32 bit of the uint32_t varible. The function also computes `UINT_MAX >> (32 - 12)` and as last case, we lost some bits by moving to right, obtaining:

    (UINT_MAX >> (32 - 12) ) =  0000 0000 0000 0000 0000 1111 1111 1111

Finally, apply the OR over both results giving

    (UINT_MAX << 12) |  (UINT_MAX >> (32 - 12) ) = 1111 1111 1111 1111 1111 1111 1111 1111

    (UINT_MAX << 12) |  (UINT_MAX >> (32 - 12) ) = 4.294.967.295


**References:**

- https://gist.github.com/Cartexius/4c437c084d6e388288201aadf9c8cdd5

- https://www.youtube.com/watch?v=HoQhw6_1NAA&ab_channel=TheCherno

- https://www.youtube.com/watch?v=KXwRt7og0gI&ab_channel=TheCherno