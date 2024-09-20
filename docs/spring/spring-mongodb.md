# MongoDB in SpringBoot

Add this in `pom.xml`

```xml
	<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-mongodb</artifactId>
		</dependency>
```

#### Add this in `application.yaml` config

```yaml
spring:
  application:
    name: app-name
  data:
    mongodb:
      database: dbName
      host: localhost
      port: 27017
      auto-index-creation: true
```

### Entity with lombok

```java
@Document(collection = "journal_entries")
@Data
public class JournalEntity {
    @Id
    private ObjectId journalId;
    @NonNull
    private String content;
    @NonNull
    private String title;
    private LocalDateTime date;
}

```

### Service which use Mongo Repository

```java

@Service
public class JournalService {


    private JournalRepository journalRepository;

    //    DI
    JournalService(JournalRepository journalRepository) {
        this.journalRepository = journalRepository;
    }

    public Boolean saveJournal(JournalEntity journalEntity) {
        journalEntity.setDate(LocalDateTime.now());
        journalRepository.save(journalEntity);
        return true;

    }

    public List<JournalEntity> getAllJournal() {
        return journalRepository.findAll();
    }

    public Optional<JournalEntity> getJournalById(ObjectId id) {
        return journalRepository.findById(id);
    }

    public Boolean updateJournalById(JournalEntity journalEntity) {
        Boolean isJournalExist = journalRepository.existsById(journalEntity.getJournalId());

        if (isJournalExist) {
            journalEntity.setDate(LocalDateTime.now());
            journalRepository.save(journalEntity);
            return true;
        } else {
            return false;
        }
    }

    public Boolean deleteJournalById(ObjectId id) {
        Boolean isJournalExist = journalRepository.existsById(id);
        if (isJournalExist) {
            journalRepository.deleteById(id);
            return true;
        } else {
            return false;
        }

    }

}

```

### Repository Configuration in Spring MongoDB

```java
public interface JournalRepository extends MongoRepository<JournalEntity, ObjectId> {
// nothing just blank
}

```
