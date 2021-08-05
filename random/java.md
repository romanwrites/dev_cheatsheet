# Some useful code snippets

## When needing to chain call and handle NPE
```java
Optional.ofNullable(someObject.generateSomething())
        .map(something -> something.doSomethingElse)
        .orElseThrow(IllegalArgument::new);
```

## Compile java sources from shell
```bash
find * -name '*.java' > src.txt
javac @src.txt
```

## Autowired RequiredArgsConstructor
when needed to add qualifier to RequiredArgsConstructor do this:
```java
@RequiredArgsConstructor(onConstructor = @__(@Autowired))
```
