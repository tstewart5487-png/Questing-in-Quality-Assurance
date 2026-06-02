# Software Testing Study Notes

## Test Case Types

### Positive Test Cases
* Tests whether an app is doing something it should according to a particular requirement.
* Uses valid test data.
* Always carry out positive test cases first.
* Checks that a requirement has been met at the most basic level (most likely cases first).
* Important to make sure the software works correctly.

### Negative Test Cases
* Tests whether an app is doing something it shouldn't.
* Verifies how the app responds when misused or when invalid test data is used.
* Application should implement successful error handling.
* Goal is to try to break the system while making sure it doesn't crash.

---

## Black-Box Testing Techniques
* Implies scripted testing where test cases are written in advance.
* Widespread system of testing that replicates how a user interacts with the software.
* Testers have no access to the underlying code.

---

## Equivalence Partitioning & Boundary Values

### Equivalence Partitioning
* Input values are grouped into ranges or sets called "partitions."
* All values in a single group are expected to be treated exactly the same by the system.
* Used to reduce the total number of test cases while covering a wide range of inputs.
* Optimizes testing by covering the most representative input cases (does not guarantee all errors are caught).
* **Execution Rule:** Pick exactly 1 representative value from each class.
* **Range:** A continuous interval of numeric values.
* **Set:** A collection of specific, discrete values (or sometimes just one value) without a range.
* *Note: Range classes + Sets = Full coverage.*

### Boundary Value Analysis
* Focuses on the edges of the ranges defined in Equivalence Partitioning.
* Assigned only to equivalence classes that have a range of values.
* Errors are most likely to happen right at these boundaries.
* **Workflow:** Define the class $\rightarrow$ Define the range $\rightarrow$ Define the mathematical boundaries $\rightarrow$ Define the boundary values.

### The Empty Field Rule
* It is good practice to always test an empty field.
* While it might not be a boundary or a standard class, experience shows it often causes crashes because developers forget to handle it.

---

## Decision Tables
* Allows testers to optimize tests by modeling all possible combinations of conditions that impact a decision.
* Helps identify significant condition combinations and potential gaps in the test requirements.
* Can be minimized to remove unnecessary or redundant combinations.
* **Minimum Coverage Standard:** Test exactly one test case per rule.

---

## Pairwise Testing
* Involves testing pairs of parameters rather than every single possible combination.
* Highly useful when there are a large number of parameters to manage.
* **Methodology:** Create pairs of columns, using the same columns to generate the pairs.
* Generates an *orthogonal array* mathematical structure to optimize combinations.
* **Tool Link:** [Pairwise Teremok Games Tool](https://teremokgames.com)
