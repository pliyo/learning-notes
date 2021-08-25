# Long running processes

A long running process is a process whose execution lifetime exceeds the time to process a single external event or message.

Long running means that multiple external events / triggers are handled by the same process instance -> is Stateful

**Examples**: moving money from one bank to another, where it could mean that where the money arrives to one account the account is already closed to the money starts to make the money back.
The challenge is all the fees you have to pay for moving the money around.
So although there is a compensation transaction, you might not return to the state where you were at the beginning.

You could say it's like Object Oriented Programming was meant to be about, you take some data, encapsulate that with behaviour, and that behavious is invoked as a result of triggers. 

That's why sagas are being built like objects with an state around.

* Which service owns the HTTP invokation part?
    ITOPs (what do we mean in this context with ITOps???)
- Each of the messages serves as a trigger for the integration process.

The responses that we get back are viewed just like mesages coming in. Every response is just like any other message.
We could model the state of the process, as the number of pending responses that we are waiting for.

A lot of running processes will invert the flow. What state do I need to hold to to be able to process all those messages correctly?

# Sagas
- Triggers are messages (via bus by a queue)
- Similar to message handlers, can handle a number of different message tyes
- Different from message handlers, have state, message handlers don't
- A saga is a class that handles multiple messages and contains multiple states.


