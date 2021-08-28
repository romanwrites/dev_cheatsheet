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

## Delete .class files
```
find . -name "*.class" -delete
```

## Autowired RequiredArgsConstructor
when needed to add qualifier to RequiredArgsConstructor do this:
```java
@RequiredArgsConstructor(onConstructor = @__(@Autowired))
```

After spring 4.3 can use just
```
@RequiredArgsConstructor
```

## Check if json field exists
use [jsonPath](https://www.baeldung.com/guide-to-jayway-jsonpath) library
```java
boolean hasOrangeInProducts(ResponseEntity<String> responseEntity) {
  try {
    DocumentContext jsonContext = JsonPath.parse(responseEntity.getBody());
    return isJsonContextContainsField(jsonContext, "$.products[?(@.orangeCount)].orangeCount");
  } catch (Exception e) {
    e.printStackTrace();
    return false
  }
}

boolean isJsonContextContainsField(DocumentContext jsonContext, String path) {
  return !((net.minidev.json.JSONArray) jsonContext.read(path)).isEmpty();
}
```
