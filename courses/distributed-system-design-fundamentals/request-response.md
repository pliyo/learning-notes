# Request Response

Sagas will have some order processing, and a call out to ITOps (again: what do we mean by ITops here?)

Udhi prefers to define a class to process the saga, ex: OrderingProcessSaga
```
public class OrderinProcessSaga : Saga<OrderProcessingSaga.MyData>
{
    public class MyData : ContainsSaga
    {
        
    }
}


```