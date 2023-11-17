# What problem I meet

```
val alreadyExistEntity = repository.save(originalEntity).block()
        println(alreadyExistEntity?.createdAt)
        StepVerifier.create(
            handoverLocationEntityRepository.findByNodeIdentifier(originalEntity.nodeIdentifier),
        ).assertNext {
            Assertions.assertThat(it).isEqualTo(alreadyExistEntity)
        }.verifyComplete()
```

`originalEntity` has two properties, they are:
```
@CreatedDate
var createdAt: Instant? = null,

@LastModifiedDate
var updatedAt: Instant? = null,
```

When I ran this test code in local(Mac OS), it passed.

When I ran this in our CI pipeline(Linux), it failed, and error is:

```
excepted:
createdAt=2023-11-17T03:42:56.768235432Z, updatedAt=2023-11-17T03:42:56.768235432Z

but was:
createdAt=2023-11-17T03:42:56.768235Z, updatedAt=2023-11-17T03:42:56.768235Z
```

We could quickly know that it is a time precision problem. But what happened? Why it has different performance in local and CI env?

# What happened
1. Our testing use H2 db, it provides 6 digits precision timestamp by default.

2. JDK 17 Instant use nanosecond precision(9 digits), so when the originalEntity saved, it will generate a 9 digits precision timestamp, but it actually depends on the clock frequency of your specific system and hardware.

3. MacOS's time API just provide precision at the microsecond level(), but Linux provide precision at nanosecond level.

In summary, when I ran in local, I got a 6 digits precision time because my system is MacOS, and My H2 DB use 6 digits precision, so the test passed coincidently. On the other hand, my CI env use Linux system, it provide 9 digits precision. As a result, the test failed because H2 DB saved 6 digits precision time but it asserts equal with 9 digits precision time fields.