# C++ Concurrency

## Things I don't know

i. function object 

### delegating constructors





## General notes

* Concurrency VS Parallelism
  
  * concurrency when primary concern is **separation of concern**
  * parallelism when primary concern is to make use of all hardware and improve performance
  
* Hello world threading in C++

  ```c++
  #include<iostream>
  #include<thread>
  
  void hello() {
    std::cout << "Hello world" << std::endl;
  }
  
  int main() {
    std::thread t(hello);
    t.join();
  }
  ```

  * Run this by (may be have to see more options )

    `g++ -std=c++11 main.cpp -pthread`

  * More info at [link](https://stackoverflow.com/questions/34933042/undefined-reference-to-pthread-create-error-when-making-c11-application-with)

* Managing threads

  * some function `void some_function()` is created and passed to `std::thread my_thread(some_function)` and the thread start running and stops when the function returns. 

  * While passing function object to a thread 

    * *Wrong:* `std::thread my_thread(task());` 

      this declares a function that named `my_thread`, takes a parameter and returns a threa

    * *Right:* 

      i. `std::thread my_thread((task()));`

      ii. `std::thread my_thread{task()};`

    * Thread has a destructor `std::terminate()` 

    * If run `my_thread.detach()` then the thread will be detached from main function and continue to run even after the main function / associate function exits.

    * It is bad idea to create thread that has access to local variables of a function.

    * calling `my_thread.join()` will wait for the thread to finish. To make more accessible thread control **conditional variables & futures** are used.

    * 

    























