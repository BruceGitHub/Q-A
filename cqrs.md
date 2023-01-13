# Video 
- 2014 - Event Sourcing - https://www.youtube.com/watch?v=8JKjvY4etTY 
- Greg Young - 
Main topics key point in the comment


# Blog

- 2022 - https://dev.to/adgaray/cqrs-with-symfony-messenger-2h3g - [php]


- 2021 - https://www.eventstore.com/cqrs-pattern
    - https://www.eventstore.com/cqrs-pattern#CQRS-misconceptions
    "Commands and queries need to be run on separate databases, and everything must be stored in separate databases

- 2021 - https://event-driven.io/en/cqrs_facts_and_myths_explained/
    - Oskar Dudycz - 

# Pro

- Independent scaling. It allows the read and write models to scale independently
- Optimized data schemas. The read model can use a schema that is optimized for queries, and the write model uses a schema that is optimized for updates.
- Security. It's easier to ensure that only the right domain entities are performing writes.
- Separation of concerns. The complex business logic goes into the write model. The read model can be simple.


# Note

## Command in Application
```php
namespace App\EmailSender\Application\Create;
final class CreateEmailCommand implements Command {}
```

## Possible structure of directory 
![](https://res.cloudinary.com/practicaldev/image/fetch/s--5g7OIlNn--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1wm4h856c27tylb0fqra.png)


# Question
## Command in Domain or Application ? 