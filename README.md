# iceoryx_on_fire

|`ReferenceCounter`     | i        |   | Basic building block for classes which are needing some kind of reference counting like a `std::shared_ptr` |
|`set`                  | i        | X | Templated helper functions to create a fake `std::set` from a vector. |
|`poor_mans_heap`       |          | Acquires memory on the stack for placement new instantiations. All classes must inherit from a base class which has to be known at compile time but the class itself does not have to be known - only the size. |
|`ActiveObject`         | i | X | Active object base skeleton implementation inspired by [Prefer Using Active Objects Instead Of Naked Threads](https://www.drdobbs.com/parallel/prefer-using-active-objects-instead-of-n/225700095)  |
|`TriggerQueue`            | i | X | Queue with a `push` - `pop` interface where `pop` is blocking as long as the queue is empty. Can be used as a building block for active objects. |



| Data Structure           | Shared Memory usable  | Thread-Safe | Lock-Free | Concurrent Producers : Consumers | Bounded Capacity | Data Type Restriction | Use Case                                     |
|`TriggerQueue`            | No                    | Yes         | No        | n:m                              | Yes              | Copyable              | Process events in a blocking way             |
|`TACO`                    | Yes                   | Yes         | Yes       | n:m                              | Yes              | Copyable or Movable   | fast lock-free exchange data between threads |  
