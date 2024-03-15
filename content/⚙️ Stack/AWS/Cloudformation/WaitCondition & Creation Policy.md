# WaitCondition & Creation Policy

- EC2 will send signal to cfn when the status is ‘**CRETE_COMPLETE**’, but it doesn’t mean all the resource is ready (e.g. bootstrapping in EC2 takes extra time)
- **WaitCondition** & **Creation Policy** are ways that we can get around this default limitation

**Signal**

- configure CFN to **hold** until for timeout/ ‘x’ number of **success** signals
    - if success signals received.. **create_comple**
    - if failure signal received.. creation fails
    - if timeout is reached.. creation fails
- use Creation Policy & WaitCondition to build the signals

[[WaitCondition & Creation Policy/Untitled.png]]

- usually use Creation Policy for EC2/ ACG, which is a default resource ready to use

[[WaitCondition & Creation Policy/Untitled 1.png]]

- waitcondition is a separate logical resources for more advanced data flow features
