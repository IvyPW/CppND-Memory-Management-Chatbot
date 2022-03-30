# My tasks with this project
## 1. fix the segment fault issue
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
