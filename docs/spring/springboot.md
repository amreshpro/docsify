# Spring Boot

## SpringBoot Foundation

#### Dpendency Injection(Design Pattern) or IOC(principle)

`Constructor Injection` Recommended

```java
@RestController
class TestController {
	TestService testService;
  /* constructor */
	TestController(TestService testService){
		this.testService = testService;
	}
}

```

`Method Injection` Recommended

```java
@RestController
class TestController {
	TestService testService;
  /* method */
	setServiceInjection(TestService testService){
		this.testService = testService;
	}
}

```

`Field Injection` Recommended

```java
@RestController
class TestController {
	@Autowired
	TestService testService;
}

```

### Spring REST

- @Component
- @RestController
- @Entity
- @Service
- @Controller

- @RequestBody
- @PathVariable
- @RequestMapping("/api/user")
- @GetMapping
- @PostMapping
- @DeleteMapping
- @PutMapping
- @PatchMapping

> > Send Response with proper http status code use `new ResponseEntity()`

```java
new ResponseEntity<>(false, HttpStatus.NOT_FOUND);
new ResponseEntity<>(journalEntities, HttpStatus.OK);
```
