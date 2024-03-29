# Java

## Generate src
### [Generate sources from openapi](https://github.com/kukinpower/generate-spring-src-maven)


## Some useful code snippets

### Handle NPE when need a chain call and 
```java
Optional.ofNullable(someObject.generateSomething())
        .map(something -> something.doSomethingElse)
        .orElseThrow(IllegalArgument::new);
```

### Compile java sources from shell
```bash
find * -name '*.java' > src.txt
javac @src.txt
```

### Delete .class files
```
find . -name "*.class" -delete
```

### Autowired RequiredArgsConstructor
when needed to add qualifier to RequiredArgsConstructor do this:
```java
@RequiredArgsConstructor(onConstructor = @__(@Autowired))
```

After spring 4.3 can use just
```
@RequiredArgsConstructor
```

### Check if json field exists
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

### Why use Optional over null?
Optional tells code user that a method can return empty value  
It has iseful methods to handle errors  
Better to read then null handling with conditions  
Idea warns you if you are trying to get value without check. So it reduces NPE  

### Test multithreading as if in one thread
```java
doAnswer(invocation -> {
  ((Runnable)invocation.getArgument(0)).run();
  return null;
}).when(threadPoolTaskExecutor).execute(any(Runnable.class));
```

### Throw exception with protected constructor
Can create an anonymous exception by adding {}
```java
when(objectMapper.writeValueAsString(any(Object.class))).thenThrow(new JsonProcessingException("message"){})
```

### Mask specific field in json file
```java
String myRegex = "(\"name\"\\s*:\\s*\")(.+)(\"\\s*)(?=[,}])";
String replacedValue = json.replaceAll(myRegex,"$1********$3");
```

## Ways to read file from `resources`
```java
Files.readString(Path.of("src/java/resources/path-to-file"));
```

```java
String FILENAME = "file.csv";

ClassPathResource classPathResource = new ClassPathResource(FILENAME);
InputStream inputStream = classPathResource.getInputStream();
InputStreamReader inputStreamReader = new InputStreamReader(inputStream);
BufferedReader bufferedReader = new BufferedReader(inputStreamReader);

while (bufferedReader.ready()) {
  String line = bufferedReader.readLine();
}
```

```java
class ResourceFileReader {

  public static void main(String[] args) throws URISyntaxException, IOException {
    URL resource = ResourceFileReader.class.getResource("some.txt");
    URI uri = Objects.requireNonNull(resource).toURI();
    Path path = Paths.get(uri);
    List<String> lines = Files.lines(path).collect(Collectors.toList());
    System.out.println(lines);
  }
}
```

## Useful Libraries
### JSON
#### Compare two `JSONObject` regardless ordering
https://www.baeldung.com/jsonassert

#### JsonPath
https://www.baeldung.com/guide-to-jayway-jsonpath

### Throttling
#### Bucket4j
https://www.baeldung.com/spring-bucket4j


### Cache
#### Caffeine
https://www.baeldung.com/java-caching-caffeine

### Telegram bot
#### TelegramBots
https://github.com/rubenlagus/TelegramBots
