# Swagger in SpringBoot

Add this in `application.yml`

````yaml
springdoc:
  api-docs:
    path: /api-docs
  swagger-ui:
    path: /swagger-ui.html
    configUrl: /v3/api-docs/swagger-config
````

Add this in `pom.xml`

````xml
	<dependency>
			<groupId>org.springdoc</groupId>
			<artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
			<version>2.6.0</version>
		</dependency>
````

OpenApi or Swagger config -> `OpenApiConfig.java`

````java

@Configuration
public class OpenApiConfig {

    @Bean
    public OpenAPI customOpenAPI() {
        return new OpenAPI()
                .info(new Info()
                        .title("Open API")
                        .version("1.0")
                        .description("API documentation for Example application"));
    }
}
````

#### Write it before controller method

- @Operation
- @ApiResponse
- @ApiResponses
- @Parameter

````java

@Operation(summary = "Update a journal", description = "Update an existing journal entry by its ID")
@ApiResponses(value = {@ApiResponse(responseCode = "200", description = "Journal successfully updated"), @ApiResponse(responseCode = "404", description = "Journal not found")})
@PatchMapping
    public ResponseEntity<Boolean> updateJournalById(@RequestBody JournalEntity journalEntity) {
        boolean isUpdated = journalService.updateJournalById(journalEntity);
        return isUpdated ? new ResponseEntity<>(true, HttpStatus.OK) : new ResponseEntity<>(false, HttpStatus.NOT_FOUND);
    }

````
