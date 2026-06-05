# 🗺️ Urban Routes App Test Suite (FR-4 Verification)


| ID | Test Case Summary | Test Technique | Test Data | Status |
| :--- | :--- | :--- | :--- | :--- |
| **t-1** | Verify spaces are allowed in From address field | Positive Testing | `Creston Street` | [ ] Pass <br> [ ] Fail |
| **t-2** | Verify dashes are allowed in From address field | Positive Testing | `123-B Creston Street` | [ ] Pass <br> [ ] Fail |
| **t-3** | Verify periods are allowed in From address field | Positive Testing | `St. Jude Avenue` | [ ] Pass <br> [ ] Fail |
| **t-4** | Verify commas are allowed in From address field | Positive Testing | `Grand Rapids, MI` | [ ] Pass <br> [ ] Fail |
| **t-5** | Verify Latin characters are allowed in From address field | Positive Testing | `Creston` | [ ] Pass <br> [ ] Fail |
| **t-6** | Verify error message & submission block for non-Latin in From field | Negative Testing | `123 Крестон` | [ ] Pass <br> [ ] Fail |
| **t-7** | Verify error message & submission block for forbidden symbols in From field | Negative Testing | `#123 Creston St` | [ ] Pass <br> [ ] Fail |
| **t-8** | Verify error message & submission block when From field is empty | Negative Testing | `""` (Empty) | [ ] Pass <br> [ ] Fail |
| **t-9** | Verify valid minimum length boundary (1 char) in From field | Boundary Value Analysis | `A` | [ ] Pass <br> [ ] Fail |
| **t-10** | Verify valid length validation at 49 characters in From field | Boundary Value Analysis | `123 Creston Street, Kalamazoo, Michigan, MI, 4900` | [ ] Pass <br> [ ] Fail |
| **t-11** | Verify valid maximum length boundary (50 chars) in From field | Boundary Value Analysis | `123 Creston Street, Kalamazoo, Michigan, MI, 49002` | [ ] Pass <br> [ ] Fail |
| **t-12** | Verify error message & submission block at 51 characters in From field | Boundary Value Analysis | `123 Creston Street, Kalamazoo, Michigan, MI, 49002-` | [ ] Pass <br> [ ] Fail |
| **t-13** | Verify error message & submission block for drastic length overages in From field | Equivalence Partitioning | `123 Creston Street, Kalamazoo, Michigan, MI, 49002----` | [ ] Pass <br> [ ] Fail |
| **t-14** | Verify leading spaces stay visible when From field is in focus | Positive Testing | ` 123 Creston Street` | [ ] Pass <br> [ ] Fail |
| **t-15** | Verify leading spaces are deleted when From field loses focus | Positive Testing | ` 123 Creston Street` | [ ] Pass <br> [ ] Fail |
| **t-16** | Verify trailing spaces stay visible when From field is in focus | Positive Testing | `123 Creston Street ` | [ ] Pass <br> [ ] Fail |
| **t-17** | Verify trailing spaces are deleted when From field loses focus | Positive Testing | `123 Creston Street ` | [ ] Pass <br> [ ] Fail |
| **t-18** | Verify error message & submission block when From field contains only spaces | Negative Testing | `"   "` | [ ] Pass <br> [ ] Fail |
| **t-19** | Verify spaces are allowed in To address field | Positive Testing | `Main Street` | [ ] Pass <br> [ ] Fail |
| **t-20** | Verify dashes are allowed in To address field | Positive Testing | `123-B Creston Street` | [ ] Pass <br> [ ] Fail |
| **t-21** | Verify periods are allowed in To address field | Positive Testing | `St. Jude Avenue` | [ ] Pass <br> [ ] Fail |
| **t-22** | Verify commas are allowed in To address field | Positive Testing | `Grand Rapids, MI` | [ ] Pass <br> [ ] Fail |
| **t-23** | Verify Latin characters are allowed in To address field | Positive Testing | `Creston` | [ ] Pass <br> [ ] Fail |
| **t-24** | Verify error message & submission block for non-Latin in To field | Negative Testing | `123 Крестон` | [ ] Pass <br> [ ] Fail |
| **t-25** | Verify error message & submission block for forbidden symbols in To field | Negative Testing | `#123 Creston St` | [ ] Pass <br> [ ] Fail |
| **t-26** | Verify error message & submission block when To field is empty | Negative Testing | `""` (Empty) | [ ] Pass <br> [ ] Fail |
| **t-27** | Verify valid minimum length boundary (1 char) in To field | Boundary Value Analysis | `A` | [ ] Pass <br> [ ] Fail |
| **t-28** | Verify valid length validation at 49 characters in To field | Boundary Value Analysis | `123 Creston Street, Kalamazoo, Michigan, MI, 4900` | [ ] Pass <br> [ ] Fail |
| **t-29** | Verify valid maximum length boundary (50 chars) in To field | Boundary Value Analysis | `123 Creston Street, Kalamazoo, Michigan, MI, 49002` | [ ] Pass <br> [ ] Fail |
| **t-30** | Verify error message & submission block at 51 characters in To field | Boundary Value Analysis | `123 Creston Street, Kalamazoo, Michigan, MI, 49002-` | [ ] Pass <br> [ ] Fail |
| **t-31** | Verify error message & submission block for drastic length overages in To field | Equivalence Partitioning | `123 Creston Street, Kalamazoo, Michigan, MI, 49002----` | [ ] Pass <br> [ ] Fail |
| **t-32** | Verify leading spaces stay visible when To field is in focus | Positive Testing | ` 123 Creston Street` | [ ] Pass <br> [ ] Fail |
| **t-33** | Verify leading spaces are deleted when To field loses focus | Positive Testing | ` 123 Creston Street` | [ ] Pass <br> [ ] Fail |
| **t-34** | Verify trailing spaces stay visible when To field is in focus | Positive Testing | `123 Creston Street ` | [ ] Pass <br> [ ] Fail |
| **t-35** | Verify trailing spaces are deleted when To field loses focus | Positive Testing | `123 Creston Street ` | [ ] Pass <br> [ ] Fail |
| **t-36** | Verify error message & submission block when To field contains only spaces | Negative Testing | `"   "` | [ ] Pass <br> [ ] Fail |
| **t-37** | Verify selection behavior of Optimal mode option | Positive Testing | *None* | [ ] Pass <br> [ ] Fail |
| **t-38** | Verify selection behavior of Fastest mode option | Positive Testing | *None* | [ ] Pass <br> [ ] Fail |
| **t-39** | Verify selection behavior of Custom mode option | Positive Testing | *None* | [ ] Pass <br> [ ] Fail |
| **t-40** | Verify selection behavior of on foot transport icon | Positive Testing | *None* | [ ] Pass <br> [ ] Fail |
| **t-41** | Verify selection behavior of user's car transport icon | Positive Testing | *None* | [ ] Pass <br> [ ] Fail |
| **t-42** | Verify selection behavior of car-sharing transport icon | Positive Testing | *None* | [ ] Pass <br> [ ] Fail |
| **t-43** | Verify selection behavior of taxi transport icon | Positive Testing | *None* | [ ] Pass <br> [ ] Fail |
| **t-44** | Verify selection behavior of scooter transport icon | Positive Testing | *None* | [ ] Pass <br> [ ] Fail |
| **t-45** | Verify selection behavior of bicycle transport icon | Positive Testing | *None* | [ ] Pass <br> [ ] Fail |
