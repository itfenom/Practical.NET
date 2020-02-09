
- I/O Operations
  + Disk
  + Memory
  + Web/API
  + Database
- async/await
  + The await keyword:
    + Introduces a continuation, allowing us to get back to the original context (thread)
    + Gives us a potential result
    + Validates the success or failure of the operation
    + Continuation is back on calling thread
  + Should not use async void, it is only appropriate for event handlers (use async Task instead)
  + Exceptions occurring in an async void method cannot be caught
  + Using async and await in Asp.Net means the web server can handle other requests
  + Best Practices:
    + Never use async void unless it's an event handler or delegate
    + Never block an asynchronous operation by calling Result or Wait() *([Don't Block on Async Code](https://blog.stephencleary.com/2012/07/dont-block-on-async-code.html))*
    + Always use async and await together
    + Always return a Task from an asynchronous method
    + Always await an asynchronous method to validate the operation
    + Use async and await all the way up the chain
- Task
  + Task is a reference to an asynchronous operation
  + Work passed to Task.Run() is scheduled to execute on a different thread
  + Tasks swallow exceptions
  + Continuations are executed on a different thread
  + Wrapping synchronous code in Task.Run() can be dangerous. Make sure there is no blocking code.
- Task Continuation
  + Obtaining the Result of a Task
  + Handling Success or Failure
  + Validate Tasks even when not using async and await by chaining on a continuation
  + ContinueWith()
    + ContinueWith() vs await
  + ConfigureAwait()
    + ConfigureAwait(false) should be used when we don't care about the original context
    + Shoule use ConfigureAwait(false) when writing libraries
    + Not applicable for .Net Core
    + [ConfigureAwait FAQ | .NET Blog](https://devblogs.microsoft.com/dotnet/configureawait-faq/)
- Task Cancellation
- Task Completion
  + Getting Result or Exception from a Task
  + Task.WhenAll()
  + Task.WhenAny()
- Task.Delay() vs Thread.Sleep()