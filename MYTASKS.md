# My tasks with this project
## 0. fix the segment fault issue
"ChatBot Destructor" was called twice before the segment fault. 
In graphnode destructor, delete chatBot was found while the constructor actually did not new one.
```    
    GraphNode::GraphNode(int id)
{
    _id = id;
}

GraphNode::~GraphNode()
{
    //// STUDENT CODE
    //// Ivy: delete is unexpected

    //delete _chatBot; 
    _chatBot = nullptr;

    ////
    //// EOF STUDENT CODE
}
```
## 1. Task 1 : Exclusive Ownership 1
Use smart pointer unique_ptr to access ChatLogic

## 2. Task2: Rule of Five
https://cpppatterns.com/patterns/rule-of-five.html

If a class implements any of the following functions, it should implement all of them:
    
    copy constructor
    copy assignment operator
    destructor
    move constructor
    move assignment operator

## 3. Task3: exclusive of GraphNode in ChatLogic, and not change ownership
usage of unique_ptr:
https://en.cppreference.com/w/cpp/memory/unique_ptr

Please remember that with smart pointers, resource acquisition occurs simultaneously. When instantiated with make_unique, the smart pointer is initialized, and the internal raw pointer is created using new and initialized in a single step. This is the recommended way to initialize smart pointers.

The other way is as follows.
```
std::unique_ptr<ChatLogic> _chatLogic(new ChatLogic());
```
The above is not exception-safe as it may cause memory leaks. Imagine when using new that an exception happens in the constructor of the resource. In such a case, the object would not be handled properly, and its destructor would never be called even if the managing object goes out of scope. Therefore, make_unique and make_shared should always be preferred.

## 4. using of std::move
https://www.youtube.com/watch?v=OWNeCTd7yQE