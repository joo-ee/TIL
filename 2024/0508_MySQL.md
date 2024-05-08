## MySQL auto increment

MySQL의 auto increment는 테이블의 컬럼에 자동으로 순차적인 값을 할당하는 기능이다. 이 기능은 특히 테이블의 기본 키(primary key) 역할을 하는 열에 많이 사용된다.

일반적으로 auto increment 열은 정수 데이터 타입(INT, BIGINT 등)을 사용하며, 테이블에 새로운 레코드를 추가할 때마다 자동으로 이 값이 증가된다. 이를 통해 새로운 레코드가 추가될 때마다 자동으로 고유한 식별자를 할당할 수 있다.

auto increment를 설정하려면 테이블 생성 시 해당 열에 AUTO_INCREMENT 옵션을 추가하면 된다. id라는 열을 auto increment로 설정하는 예시이다.

```sql
    CREATE TABLE example_table (
        id INT AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(50)
    );
```

위의 예시에서 id 열은 AUTO_INCREMENT 옵션을 가지고 있으며, 이는 새로운 레코드가 추가될 때마다 자동으로 증가되는 값을 갖게 된다.

auto increment를 사용하면 새로운 레코드를 삽입할 때 해당 열에 값을 지정하지 않아도 된다. MySQL은 자동으로 다음에 삽입할 값을 결정하고 할당한다.

```sql
INSERT INTO example_table (name) VALUES ('John');
```

위의 쿼리를 실행하면 id 열에 자동으로 1씩 증가하는 값이 할당되는 것이다.

auto increment 는 고유한 식별자를 자동으로 생성할 때 유용하겠지만, auto increment 열에는 중복된 값이 존재할 수 없으며, 삭제된 레코드의 값은 재사용되지 않기 때문에 주의해야한다.

### 시퀀스를 초기화하면 해당 시퀀스부터 auto increment가 될까?

🙅‍♂️. 채번 초기화라는 용어는 데이터베이스 시퀀스를 특정 값으로 다시 시작하거나 초기화하는 것을 의미한다. 즉, 시퀀스의 현재 값이 특정 값으로 설정되어 다음 생성되는 값이 그 값부터 다시 시작하게 된다.
하지만, 이와 별개로 이미 auto increment 컬럼에 시퀀스보다 큰 값이 들어가있다면 해당 값을 바라본다. auto increment 지정된 컬럼을 다시 1부터 적재되도록 하고싶을 땐 ...

```sql
ALTER TABLE example_table AUTO_INCREMENT = 1;
```

이렇게 하면 된다는데 .. 직접 한 번 해봐야할 것 같다 📝
