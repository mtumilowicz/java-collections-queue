# java-collections-queue

# queue notes
* https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/Queue.html
* `interface Queue<E> extends Collection<E>`
* methods
    * inserting
        * returns `true` if the element was added to this queue, else `false`
        * `boolean add(E e)`
            * `IllegalStateException` if the element cannot be added at this time due to capacity restrictions
        * `boolean offer(E e)`
    * removing
        * returns the head of this queue
        * `E remove()`
            * `NoSuchElementException` if this queue is empty
        * `E poll()`
            * returns `null` if this queue is empty
    * examining
        * returns the head of this queue
        * `E element()`
            * `NoSuchElementException` if this queue is empty
        * `E peek()`
            * returns `null` if this queue is empty
* for every action we have two methods, because they deal
with extreme cases differently
* what can be extreme cases? for example examining element
when queue is empty or adding element when queue is full
* summary

    |   |throws exception   |returns special value   |
    |---|---|---|
    |insert   |`add(e)`   |`offer(e)`   |
    |remove   |`remove()`   |`poll()`   |
    |examine   |`element()`   |`peek()`   |
* the latter form of the insert operation (`offer`) is designed 
specifically for use with capacity-restricted `Queue` 
implementations
* in most implementations, insert operations cannot fail
* `offer` method is designed for use when failure is a normal, 
rather than exceptional occurrence, for example, in 
fixed-capacity (or "bounded") queues
* queue implementations generally do not allow insertion of 
`null` elements (`null` in queue usually makes no sense)
* implementations generally do not define element-based 
versions of methods `equals` and `hashCode` (for the same 
elements we may have different ordering properties, so 
element-based equality is not always well defined)
* the line of customers in a shop is an example of a queue
* types
    * **unbounded queue** - unlimited length (`LinkedList`)
    * **bounded queue** - limited length (`BlockingQueue`): 
    https://github.com/mtumilowicz/java11-concurrency-blockingqueue-producer-consumer-problem
* **head** - exit point of a queue
* **tail** - entry point
* head and tail may be the same
* LIFO (stack) - head and tail are the same