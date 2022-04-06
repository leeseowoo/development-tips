JUnit 5부터는 @RunWith 대신 @ExtendWith를 사용하여 테스트를 실행하는 방법을 커스터 마이징할 수 있다.
@ExtendWith은 메타 애노테이션(애노테이션 클래스에 적용할 수 있는 애노테이션)으로 사용 가능하고 여러 번 중복 사용이 가능하다는 점이 @RunWith과의 주요 차이점이다.
메타 애노테이션으로 사용 가능하다는 점을 스프링 부트에서 적극 활용하여 @SpringBootTest 사용 시 @ExtendWith(SpringExtension.class)를 생략할 수 있게 됐다.

```java
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Inherited
@BootstrapWith(SpringBootTestContextBootstrapper.class)
@ExtendWith(SpringExtension.class)
public @interface SpringBootTest {

}
```
@SpringBootTest가 @ExtendWith(SpringExtension.class)를 메타 애노테이션으로 가지고 있기 때문이다.

## References
- https://junit.org/junit5/docs/current/user-guide/
- https://www.whiteship.me/springboot-no-more-runwith/
