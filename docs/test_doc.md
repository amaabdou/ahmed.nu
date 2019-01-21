#Bad logging by examples

## General errors
Any logged message is communicated with other engineers, you should consider that it is not you who will see this message,  
Usually sending a message like this in slack or email will be bad idea,   
It is like those complains you do not like to hear "The PC is not working",   
so imagine service having a problem and all the other engineer can see is this bad message and in very bad time.

``` php tab="PHP"
<?php
$this->logger->error('Operation failed');
```

``` python tab="Python"
#!/bin/python
logger.error('Operation failed')
```

## No context
Bad messages are equally bad as messages with no context, Yes it is little better but it does not help much,  
Usually when a general problem happens it will affect 100% of all requests,   
But imagine when you see this message only with 5% of requests,   
how can start to debug such problem in first place? how to reproduce the problem? it will not possible

``` php tab="PHP"
<?php
$this->logger->error('Given number not found');
```

``` python tab="Python"
#!/bin/python
logger.error('Given number not found')
```


## Slightly better messages

- The message is specifying a problem, so it will be easier to understand.
- The mssage contains the context, the given number mentioned in the error message itself, so it's easy to debug and re produce the problem.

``` php tab="PHP"
<?php
$this->logger->error(sprintf('Given number not found [%s]', $number));
```

``` python tab="Python"
#!/bin/python
logger.error('Given number not found')
```
