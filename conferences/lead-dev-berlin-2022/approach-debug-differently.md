# Why we must approach debugging differently, by Elinor Swery

75% of developers time is spent on solving bugs (Coralogix study)<br>
That's only: 1 day + 1/4 on new features

- As a tendency, people like to work on new things. Fixing old things is not as fun
- Confirm that the input to the functions is what you think it should be.
- Step over on your function. What output do you get from it?
  - The tools we give our teams are simply not right for the job ahead.
  - We can't run the debugger in production at scale
- Processes:
  - Adjust sprint commitment / backlog if bugs come in
  - Establish a prioritisation method for new bugs
  - Have the groundwork already done for the developers
    - Let's not give them a bug ticket without no information
- Tools:
  - Cloud native. Integrated with daily workflow. Data is gold