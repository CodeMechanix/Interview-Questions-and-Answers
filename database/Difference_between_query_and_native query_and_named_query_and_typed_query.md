### Question
Difference between a query, native query, named query and typed query?

What are the differences between a query, a native query, a named query and a typed query? Does the 'alone-standing' query even exist, or is it just an abbreviation? In my mind, a native Query is a query written in simple sql, whereas a named query relates to entities (hibernate-mapping). Can someone explain this briefly?

-------------------

### Answer

Query
> Query refers to JPQL/HQL query with syntax similar to SQL generally used to execute DML(Data Manipulation Language deals with the manipulation of data present in the database like insert, delete, update) statements(CRUD operations).

In JPA, you can create a query using entityManager.createQuery(). 

In Hibernate, you use session.createQuery()

NativeQuery
> A native query refers to actual sql queries (referring to actual database objects). These queries are the sql statements which can be directly executed in a database using a database client.

JPA : entityManager.createNativeQuery() 

Hibernate (Non-JPA implementation): session.createSQLQuery()

NamedQuery

> Similar to how the constant is defined. NamedQuery is the way you define your query by giving it a name. You could define this in mapping file in hibernate or also using annotations at entity level.
```java
@Table(name = "users")
@Entity
@NamedQuery(name = "UserEntity.findByUserId", query = "SELECT u FROM UserEntity u WHERE u.id=:userId")
public class UserEntity {

    @Id
    private Long id;
    private String name;
    //Standard constructor, getters and setters.

}
```
```java
public UserEntity getUserByIdWithNamedQuery(Long id) {
    Query namedQuery = getEntityManager().createNamedQuery("UserEntity.findByUserId");
    namedQuery.setParameter("userId", id);
    return (UserEntity) namedQuery.getSingleResult();
}
```
TypedQuery

> TypedQuery gives you an option to mention the type of entity when you create a query and therefore any operation thereafter does not need an explicit cast to the intended type. Whereas the normal Query API does not return the exact type of Object you expect and you need to cast.

```java
public UserEntity getUserByIdWithTypedQuery(Long id) {
    TypedQuery<UserEntity> typedQuery
      = getEntityManager().createQuery("SELECT u FROM UserEntity u WHERE u.id=:id", UserEntity.class);
    typedQuery.setParameter("id", id);
    return typedQuery.getSingleResult();
}
```