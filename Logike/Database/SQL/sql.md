https://www.sqlstyle.guide/
https://www.simonholywell.com/post/2016/12/sql-style-guide-misconceptions/?utm_source=sqlstyle.guide-sqlstyle.guide&utm_medium=link&utm_campaign=footer-link
https://en.m.wikipedia.org/wiki/Object%E2%80%93relational_impedance_mismatch
https://www.sqlshack.com/sql-multiple-joins-for-beginners-with-examples/
# [What's the difference between identifying and non-identifying relationships?](https://stackoverflow.com/questions/762937/whats-the-difference-between-identifying-and-non-identifying-relationships)

- An **identifying relationship** is when the existence of a row in a child table depends on a row in a parent table. This may be confusing because it's common practice these days to create a pseudokey for a child table, but _not_ make the foreign key to the parent part of the child's primary key. Formally, the "right" way to do this is to make the foreign key part of the child's primary key. But the logical relationship is that the child cannot exist without the parent.
    
    Example: A `Person` has one or more phone numbers. If they had just one phone number, we could simply store it in a column of `Person`. Since we want to support multiple phone numbers, we make a second table `PhoneNumbers`, whose primary key includes the `person_id` referencing the `Person` table.
    
    We may think of the phone number(s) as belonging to a person, even though they are modeled as attributes of a separate table. This is a strong clue that this is an identifying relationship (even if we don't literally include `person_id` in the primary key of `PhoneNumbers`).
    
- A **non-identifying relationship** is when the primary key attributes of the parent _must not_ become primary key attributes of the child. A good example of this is a lookup table, such as a foreign key on `Person.state` referencing the primary key of `States.state`. `Person` is a child table with respect to `States`. But a row in `Person` is not identified by its `state` attribute. I.e. `state` is not part of the primary key of `Person`.
    
    A non-identifying relationship can be **optional** or **mandatory**, which means the foreign key column allows NULL or disallows NULL, respectively.