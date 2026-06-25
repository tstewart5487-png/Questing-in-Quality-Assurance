### 📂 04 Joining Tables

- [ ] **Relationships Between Tables** (Theory)
  - [ ] **Key Mapping**: Identifies one-to-one, one-to-many, and many-to-many physical links between records.
  - [ ] **Data Integrity**: Ensures records remain consistent across separate files through constraints.

- [ ] **Entity-Relationship Diagrams** (Theory)
  - [ ] **Visual Schema**: Blueprints tables, column attributes, and cardinality links using standard notation.
  - [ ] **Database Design**: Maps physical system structures before translating them into actual SQL code.

- [ ] **Joining Tables: INNER JOIN** (2 tasks)
  - [ ] **Exact Matches**: Returns only the specific rows where the joined keys match perfectly in both sources.
  - [ ] **Intersection Syntax**: Uses the explicit `INNER JOIN` phrase paired with an `ON` matching condition.

- [ ] **Using INNER JOIN with WHERE** (3 tasks)
  - [ ] **Row Filtering**: Applies specific conditions using `WHERE` to narrow down merged output datasets.
  - [ ] **Execution Order**: Tests how criteria filter results after the initial table combination occurs.

- [ ] **Joining Tables: LEFT OUTER JOIN** (1 task)
  - [ ] **Left Preservation**: Extracts all rows from the primary left table regardless of right-side matches.
  - [ ] **Null Handling**: Fills right-side columns with missing `NULL` values when no matching keys exist.

- [ ] **Joining Tables: RIGHT OUTER JOIN** (1 task)
  - [ ] **Right Preservation**: Keeps every single record from the secondary right source table intact.
  - [ ] **Mirror Behavior**: Reverses left logic to ensure total data coverage for the secondary source.
